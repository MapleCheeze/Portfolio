---
title: "Impossible Travel Detection Workflow"
excerpt: "Built an end-to-end workflow to detect, triage, and respond to impossible travel alerts across identity and endpoint signals."
header:
  teaser: /assets/images/portfolio/impossible-travel-teaser.jpg
toc: true
toc_sticky: true
toc_label: "On this page"
sidebar:
  - title: "Domain"
    text: "Identity Threat Detection & Response"
  - title: "Tools Used"
    text: "Microsoft Sentinel, Entra ID, Defender XDR, Logic Apps, KQL"
  - title: "Skills Demonstrated"
    text: "Detection engineering, SOAR automation, identity security, false-positive tuning"
  - title: "Code & Templates"
    text: "[tech-cookbook/sentinel/impossible-travel](https://github.com/keshawn-white/tech-cookbook/tree/main/sentinel/impossible-travel)"
---

## Overview

<!-- The problem: impossible-travel alerts are noisy by default. Out-of-the-box, analysts churn on VPN/proxy false positives.
What the goal of this workflow was: reduce noise, automate enrichment, response in minutes not hours. -->

## Detection Logic

<!-- KQL or Sentinel analytic rule: signals correlated (sign-in logs, MCAS, Defender for Identity),
thresholds, suppression conditions. -->

## Workflow Diagram

<!-- ![Impossible travel workflow](/assets/images/portfolio/impossible-travel/impossible-travel-v2.svg) -->
<!-- Trigger → enrichment → user verification → conditional access action → escalation paths -->

## Enrichment & Triage

<!-- What context gets pulled before analyst sees the alert: user risk score, recent sign-ins,
device compliance, location reputation, MFA history. -->

## Response Actions

<!-- Automated: user prompt-to-confirm, conditional access policy invocation, session revocation.
Manual escalation criteria. SOC notifications. -->

## Outcomes

<!-- False-positive reduction %, MTTR change, analyst hours saved per week. -->

## Lessons Learned

<!-- VPN/proxy carve-outs, regional travel patterns, executive-tier exemptions, etc. -->
