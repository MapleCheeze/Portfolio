---
title: "Device Tagging in Defender for Endpoint"
excerpt: "Designed and automated a device tagging strategy in Microsoft Defender for Endpoint to drive targeted policies, detections, and reporting."
header:
  teaser: /assets/images/portfolio/device-tagging-teaser.jpg
toc: true
toc_sticky: true
toc_label: "On this page"
sidebar:
  - title: "Domain"
    text: "Endpoint Security & Asset Management"
  - title: "Tools Used"
    text: "Microsoft Defender for Endpoint, Graph API, PowerShell, Logic Apps"
  - title: "Skills Demonstrated"
    text: "Endpoint strategy, tag taxonomy design, automation, RBAC alignment"
  - title: "Code & Templates"
    text: "[tech-cookbook/defender-for-endpoint/device-tagging](https://github.com/keshawn-white/tech-cookbook/tree/main/defender-for-endpoint/device-tagging)"
---

## Overview

<!-- The problem: without tags, every policy/detection/report applies to "all devices" or has to be hand-curated.
This made device groups, RBAC scoping, and targeted detections operationally painful. -->

## Tag Taxonomy

<!-- The categories and naming conventions you designed. Examples:
- Environment: prod, dev, lab
- Sensitivity: high, medium, standard
- Function: workstation, server, kiosk, OT
- Owner / business unit
Show the structure -- ideally a table. -->

## Automation Architecture

<!-- ![Device tagging automation](/assets/images/portfolio/device-tagging/device-tagging-flow.svg) -->
<!-- Source of truth (CMDB, AAD groups, naming convention), the Logic App / function that syncs,
Graph API endpoints, run cadence. -->

## How Tags Drive Operations

### Device Groups & RBAC
<!-- How tags map to MDE device groups and analyst access. -->

### Targeted Detections
<!-- Custom detections scoped by tag. Example: stricter rules for high-sensitivity devices. -->

### Reporting & Compliance
<!-- Power BI / Sentinel queries that pivot on tags for compliance evidence. -->

## Outcomes

<!-- Reduction in mis-scoped policies, RBAC clarity, detection precision improvements, audit value. -->

## Lessons Learned

<!-- Tag drift, ownership of taxonomy, what to keep vs prune over time. -->
