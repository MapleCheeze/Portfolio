---
title: "Impossible Travel Detection Workflow"
excerpt: "End-to-end detection, enrichment, and response workflow for impossible-travel sign-ins -- tuned to cut false-positive churn and shrink time-to-action."
header:
  teaser: /assets/images/portfolio/impossible-travel-teaser.jpg
toc: true
toc_sticky: false
toc_label: "On this page"
sidebar:
  - title: "Domain"
    text: "Identity Threat Detection & Response"
  - title: "Tools Used"
    text: "Microsoft Sentinel, Entra ID, Defender XDR, Logic Apps, KQL"
  - title: "Skills Demonstrated"
    text: "Detection engineering, SOAR automation, identity security, false-positive tuning"
  - title: "Code & Templates"
    text: "[tech-cookbook/sentinel/impossible-travel](https://github.com/MapleCheeze/Tech-Cookbook/tree/main/sentinel/impossible-travel)"
---

## Overview

<!-- The problem: out-of-the-box impossible-travel alerts are noisy. VPN/proxy traffic, cloud-hosted clients, and legitimate travel all create signal that looks like compromise.
What changed: built a workflow that handles the noisy 90% automatically and routes only the genuinely suspicious cases to analysts. -->

## Detection Logic

<!-- The KQL/analytic rule logic that triggers the workflow.
Signals correlated, suppression conditions, thresholds. -->

## Workflow Diagram

<!-- ![Impossible travel workflow](/assets/images/portfolio/impossible-travel/impossible-travel-v3.svg) -->

## Enrichment & Triage

<!-- What context the workflow attaches before an analyst (or the user) sees it:
- User risk score from Entra ID Protection
- Recent sign-in pattern (last 7d/30d locations)
- Device compliance state
- MFA history on the session
- Known VPN/proxy ASN check -->

## Response Actions

<!-- Automated path: prompt-to-confirm to user, conditional access policy invocation,
session revocation if uncontested, escalation to analyst on suspicious response.
Manual path: how/when an analyst gets pulled in. -->

## Outcomes

<!-- False-positive reduction, MTTR change, analyst hours saved per week. -->

## Lessons Learned

<!-- VPN/proxy carve-outs, executive travel exemptions, the limits of "user prompt-to-confirm." -->
