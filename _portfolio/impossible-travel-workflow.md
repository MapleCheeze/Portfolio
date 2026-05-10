---
title: "Impossible Travel Detection Workflow"
excerpt: "End-to-end detection, enrichment, and response workflow for impossible-travel sign-ins, tuned to cut false-positive churn and shrink time-to-action."
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
    text: "[tech-cookbook/security-operations/impossible-travel](https://github.com/MapleCheeze/Tech-Cookbook/tree/main/security-operations/impossible-travel)"
---

## Overview

Out-of-the-box impossible-travel alerts in Microsoft Sentinel are notoriously noisy. Corporate VPN exits, cloud-hosted clients, mobile carriers that hop regions mid-session, and legitimate business travel all produce sign-in patterns that look like compromise. Triaging these manually was burning analyst hours on false positives, and the genuine cases were getting buried in the noise.

This workflow handles the routine 90% automatically: it enriches each alert with the context analysts actually need, contacts the user, evaluates the response, and applies a Conditional Access action when warranted. Only the cases that genuinely require human judgment escalate to the SOC.

## Detection Logic

The trigger is Sentinel's UEBA-driven impossible-travel analytic rule, with adjustments tuned to the environment:

- **Region carve-outs at the rule level.** Known corporate VPN egress points, cloud-hosted clients, and mobile carrier ASNs are suppressed in the analytic rule itself, not in the workflow. This matters: filtering inside the Logic App still fires the alert, still consumes hunting cycles, and still risks noisy escalation paths. Pushing the suppression up to the rule means the alert never lights up in the first place for traffic the team already understands.
- **Velocity threshold tuning.** The default threshold is too aggressive for a distributed workforce. Tuned to match the actual travel patterns observed across staff, with a gradual rollout to validate before going live.
- **Identity Protection correlation.** Each alert is joined to Entra ID Identity Protection user-risk and sign-in-risk signals at trigger time. The workflow has a credibility score to act on, not just a geographic delta.

## Workflow Diagram

![Impossible travel workflow]({{ '/assets/images/portfolio/impossible-travel/impossible-travel-v3.svg' | relative_url }})

## Enrichment & Triage

Before the workflow contacts anyone, it pulls the context the analyst would otherwise have to gather manually:

- User risk score and recent risky-sign-in history from Entra ID Identity Protection
- Recent sign-in patterns across the last 7 and 30 days for travel context
- Device compliance state for both source IPs
- MFA history on the impossible-travel session itself
- ASN reputation and geolocation for the source IPs

This package lands in the Sentinel incident comments and in the message sent to the user, so by the time anyone reads anything, the surrounding context is already there.

## Response Actions

The workflow takes one of three paths based on the user's response and the surrounding signal:

- **User confirms the sign-in + signals are clean** → close the incident as benign, log the outcome to Sentinel.
- **User denies, doesn't respond, or signals are suspicious** → invoke a named Conditional Access policy. Depending on severity, the policy revokes active sessions, requires MFA on next sign-in, or blocks. Action lands inside minutes.
- **Signals strongly suggest compromise regardless of the user's response** → escalate to the SOC channel with the enrichment summary attached. The analyst arrives with full context, not a blank ticket.

The auto-handle vs. escalate boundary was tuned over several weeks of running the workflow in observation mode, watching what was getting through and what was over-rotating, before letting it act independently.

## Outcomes

- **Faster response.** Mean time from alert to first user contact dropped from analyst-paced hours to workflow-paced minutes. For genuine compromises, the Conditional Access action lands before the attacker has session time to act on.
- **Reduced analyst workload.** The routine cases (legitimate travel, known VPN, mobile carrier hops) close automatically. The analyst review queue shrank substantially, freeing capacity for genuinely ambiguous cases and other detection work.
- **Better experience for travelers.** Frequent travelers used to be repeatedly questioned by the SOC. Now the workflow contacts them directly, they confirm in seconds, and there's a logged trail. No SOC ticket, no analyst time.
- **Cleaner incident records.** Every action the workflow takes is written back to the Sentinel incident, giving a clean audit trail for compliance and a feedback loop for tuning the detection over time.

## Lessons Learned

- **Suppress at the rule, not the workflow.** Filtering inside the Logic App means firing alerts you ignore. That looks fine until someone audits why an obvious VPN signal "wasn't acted on" for a quarter.
- **Executive travel is its own pattern.** Some users travel constantly. Tier the policy (looser for known travelers) or accept that those users will benefit less from this control. Don't pretend the workflow can normalize their pattern away.
- **User-prompt fatigue is real.** Prompt too often and people click through without reading. The rule has to be tight enough that the prompt itself signals "this matters, look closely."
- **Session revocation has user impact.** Revoking sessions logs the user out of every active session. Match the action to the signal severity. Don't over-rotate on weak evidence.
- **The auto-handle line will be wrong on day one.** Plan for tuning runs. The SOC should own the criteria over time.
