---
title: "Device Tagging in Defender for Endpoint"
excerpt: "Designed and automated a department-aware device tagging strategy in Microsoft Defender for Endpoint to drive faster response, scoped policies, and meaningful reporting."
header:
  teaser: /assets/images/portfolio/device-tagging-teaser.jpg
toc: true
toc_sticky: true
toc_label: "On this page"
sidebar:
  - title: "Domain"
    text: "Endpoint Security & Asset Management"
  - title: "Tools Used"
    text: "Microsoft Defender for Endpoint, Advanced Hunting (KQL), Entra ID, Logic Apps, Defender API"
  - title: "Skills Demonstrated"
    text: "Endpoint strategy, tag taxonomy design, identity-driven automation, RBAC alignment"
  - title: "Code & Templates"
    text: "[tech-cookbook/defender-for-endpoint/device-tagging](https://github.com/MapleCheeze/Tech-Cookbook/tree/main/defender-for-endpoint/device-tagging)"
---

## Overview

In Microsoft Defender for Endpoint, every device is just a name on a list until you tell the platform what it is. Without context, an analyst responding to an incident has to stop and figure out which department a device belongs to, who uses it, and how sensitive its data is -- usually by chasing information across spreadsheets and directory tools. That lookup costs time at exactly the moment time matters most.

Device tagging is built into Defender, included at no extra cost, and almost universally underused. I designed an automated tagging system that pulls department data from Entra ID and applies it to devices on a schedule, so context is always present in Defender itself -- no separate lookup required.

## Goals

- Eliminate manual tagging and the maintenance burden that comes with it
- Drive every device tag from a single source of truth (Entra ID)
- Keep tags accurate as users move between departments and as devices come and go
- Make tags useful operationally: device groups, scoped detections, and clean reporting

## Tag Taxonomy

A consistent prefix-based convention so tags stay readable and case-sensitive collisions don't create duplicates:

- **DEPT-{Name}** — department, sourced directly from Entra ID (e.g., `DEPT-Finance`, `DEPT-IT`)
- **SITE-{Name}** — physical or logical location (e.g., `SITE-Remote`, `SITE-HQ`)

Naming follows Entra ID's existing department field exactly, so the system stays self-consistent if HR or IT change conventions upstream.

## Architecture

<!-- ![Device tagging automation flow](/assets/images/portfolio/device-tagging/device-tagging-flow.svg) -->

The workflow joins identity data to device data inside Microsoft 365 Defender Advanced Hunting, then a Logic App pushes the resulting tags back into Defender via the API on a weekly schedule.

**1. Map users to departments** -- query Entra ID's identity table for the latest department assignment per user:

```kql
IdentityInfo
| where isnotempty(Department)
| summarize arg_max(Timestamp, *) by AccountUpn
| project AccountUpn, Department
```

**2. Join devices to that map** -- enumerate logged-on users per device and pull their department:

```kql
let DeptMap =
    IdentityInfo
    | where isnotempty(Department)
    | summarize arg_max(Timestamp, *) by AccountUpn
    | project AccountUpn, Department;
DeviceInfo
| where isnotempty(LoggedOnUsers)
| mv-expand ParsedUser = parse_json(LoggedOnUsers)
| extend UserUpn = tostring(ParsedUser.UserPrincipalName)
| join kind=inner DeptMap on $left.UserUpn == $right.AccountUpn
| summarize arg_max(Timestamp, *) by DeviceId
| project DeviceId, DeviceName, UserUpn, Department
```

**3. Reconcile and apply** -- a Logic App compares the resulting tag list against current device tags in Defender and writes only the deltas:

- Add tags where they're missing
- Remove tags when a user has moved departments
- Flag devices with no matching user for review (rather than silently mistagging them)

The full sanitized Logic App template lives in the [tech-cookbook repo](https://github.com/MapleCheeze/Tech-Cookbook/tree/main/defender-for-endpoint/device-tagging).

## How Tags Drive Operations

### Device Groups & RBAC
Tags map directly to Defender device groups, which scope analyst access. Finance devices are visible to Finance-aligned analysts; sensitive groups are restricted by default.

### Scoped Detections
Custom analytic rules in Sentinel filter on device tags, so high-sensitivity device groups can run stricter rules without spamming false positives across the rest of the fleet.

### Reporting & Compliance
Vulnerability reports, incident dashboards, and audit evidence pivot on department tags. Instead of "40 devices have a critical vuln," reporting becomes "8 in Finance, 3 in HR" -- routable, accountable.

## Outcomes

- **Incident context immediate** -- analysts no longer interrupt response to chase device ownership
- **Vulnerability remediation routed by department** -- tickets go to the right team leads from the start
- **Tags stayed accurate** -- the weekly reconcile prevented the stale-tag drift that kills manual systems
- **Scoping logic consolidated** -- detections, RBAC, and reporting all anchor on the same taxonomy

## Lessons Learned

The most important design decision was building tag *removal* into the workflow from day one. Without it, tags accumulate and become actively misleading after a few rounds of department changes. A tagging system that quietly lies is worse than no tagging at all -- the cleanup logic is what makes the rest trustworthy.
