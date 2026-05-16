---
title: "Endpoint Security for an International NGO"
excerpt: "Security Advisor engagement through the CyberPeace Institute: worked with the leadership of an international NGO to design endpoint security controls for their remote workforce and produce accessible documentation staff actually read."
header:
  teaser: /assets/images/portfolio/ngo-endpoint-teaser.jpg
toc: true
toc_sticky: false
toc_label: "On this page"
sidebar:
  - title: "Domain"
    text: "Endpoint Security, BYOD, Security Communications"
  - title: "Tools & Frameworks"
    text: "BYOD architecture, MFA / password managers, mobile device controls, VPN guidance"
  - title: "Engagement Type"
    text: "Security Advisor through the CyberPeace Institute, advisory + documentation"
  - title: "Skills Demonstrated"
    text: "Stakeholder engagement, control design for resource-constrained orgs, plain-language security writing"
---

## Context

The client was an international NGO whose staff increasingly worked remotely on a mix of personal and organizational devices. The org had no in-house IT security capacity, a small budget, and a workforce distributed across regions, network conditions, and threat environments. The leadership knew the risks were real but didn't have a coherent way to address them: there was no shared baseline for what "secure enough" looked like, and the controls they had weren't paired with anything staff could actually read and act on.

I joined as a Security Advisor through the CyberPeace Institute to work with their leadership on two fronts at once: designing endpoint controls that fit the org's actual capacity, and producing documentation staff would use rather than ignore.

## Approach

The engagement was deliberately scoped to be sustainable for an organization without a security team. That meant controls built into platforms they were already paying for, and user-driven actions over anything that needed central management. The documentation had to read for non-technical staff without watering down the substance.

Two parallel workstreams:

1. **Control design** , a practical BYOD model covering personal-device use, screen lock and authentication standards, malware protection, MFA on critical accounts, mobile and physical security, and VPN use on untrusted networks.
2. **Documentation** , a single staff-facing guide that turned the control set into clear, actionable steps without jargon. Written for the reader, not the auditor.

## BYOD Architecture

The architecture below shows the BYOD control flow: how personal devices accessing organizational systems were segmented, what was required of the device before access, and where the org's responsibility began and ended.

![BYOD security architecture]({{ '/assets/images/portfolio/ngo-endpoint/byod-architecture.svg' | relative_url }}){: .full}

## Deliverables

- **Endpoint Security Guide** , a 10-page staff-facing document covering device access control, OS and application updates, malware protection, account security and MFA, mobile device security, physical security, and VPN use. Written in plain language with a quick-reference checklist and glossary. Available [here]({{ '/assets/files/endpoint-security-guide.pdf' | relative_url }}).
- **BYOD architecture** , the control model above, used internally by leadership to align on what staff and the org are each responsible for.
- **Implementation guidance** , recommendations on how to operationalize the controls without dedicated IT capacity (built-in tools, free tier options, what to phase first).

## Outcomes

- Leadership had a shared, written baseline for endpoint security expectations across the global staff.
- Staff received a guide that reads like advice, not policy , designed to be opened, not just acknowledged.
- Free and built-in tools (Windows Defender, XProtect, Bitwarden, authenticator apps) carried most of the weight, keeping ongoing cost near zero.
- The BYOD model gave the org a clear answer to "what's our policy on personal devices?" beyond "don't."

## Considerations

- **Budget reality matters more than ideal architecture.** An NGO with no IT specialist needs controls they can stand up themselves and maintain without expert help. Recommendations that require a paid MDM or a dedicated admin would have been ignored, regardless of how technically sound.
- **The doc is the deliverable, not the policy.** A formal policy that nobody reads doesn't change behavior. The staff guide was deliberately framed as helpful advice with reasoning attached ("why this matters") rather than a list of mandates.
- **Lowest-friction path wins.** MFA via authenticator apps over SMS, browser-based VPN clients, password managers with personal-use free tiers, biometric over PIN: every recommendation was chosen partly for what staff would actually adopt.
- **Advisory engagement boundaries.** The work delivered a baseline. Sustained operation, audit, and incident response remain the org's responsibility, with the CyberPeace Institute available for follow-on engagements as needed.
