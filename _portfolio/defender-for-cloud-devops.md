---
title: "Defender for Cloud & DevOps Governance"
excerpt: "Currently leading the rollout of Microsoft Defender for Cloud across our Azure environment, paired with governance integrated directly into our Azure DevOps pipelines."
header:
  teaser: /assets/images/portfolio/defender-cloud-teaser.jpg
toc: true
toc_sticky: false
toc_label: "On this page"
sidebar:
  - title: "Domain"
    text: "Cloud Security & Governance"
  - title: "Tools Used"
    text: "Microsoft Defender for Cloud, Azure Policy, Azure DevOps, Microsoft Sentinel, Entra ID"
  - title: "Skills Demonstrated"
    text: "Cloud security architecture, DevSecOps, Azure governance, policy as code, program leadership"
  - title: "Status"
    text: "In progress, ongoing rollout"
---

## Overview

This is an in-flight initiative I'm leading to bring Microsoft Defender for Cloud and a coherent governance model into our Azure environment, with security integrated directly into the Azure DevOps pipelines that ship the work.

The driver is straightforward: cloud workloads have grown faster than the program around them. Defender for Cloud gives us posture management and workload protection across the estate, and embedding governance into the pipeline means the controls travel with the code instead of being bolted on afterward. The goal is to land a model where security is the default path, not a separate one.

## Goals

- Stand up Defender for Cloud across all Azure subscriptions with consistent CSPM and CWPP coverage
- Establish a governance baseline through Azure Policy, management groups, and naming/tagging standards
- Integrate security gates into Azure DevOps pipelines so misconfigurations and risky changes are caught at PR time
- Build the operating model so this is sustainable, ownership, exceptions, and remediation paths are all defined
- Treat policy and governance as code, versioned in DevOps the same as everything else

## Approach

### Defender for Cloud Rollout

The rollout started with a business case grounded in concrete pain points raised by the infrastructure and DevOps teams: misconfigured resources surfacing too late, no consistent view of cloud posture, and vulnerabilities reaching production before security could catch them. Framing the work in those terms (rather than as a generic security upgrade) is what secured senior leadership buy-in and got it funded.

Defender for Cloud is being deployed incrementally across Azure subscriptions, prioritizing the workloads with the highest exposure first. CSPM coverage establishes the baseline posture across the estate, and CWPP plans are enabled selectively where the runtime protection value justifies the cost. Alerts route into ServiceNow for ticketing workflows and into Azure DevOps for developer-side remediation, so the right team sees the right finding without anyone having to triage in the Defender portal.

### Governance Foundation

Before any controls could be enforced consistently, the governance layer underneath had to exist. Defender for Cloud is being deployed onto an Azure estate without a coherent baseline for naming, tagging, management group structure, or policy scope: a greenfield state in everything but inventory.

The foundation is being built using Azure Policy as Code. Definitions and initiatives live as JSON in source control and deploy through pipelines rather than the portal. The tagging governance standard is the anchor, with mandatory and optional tag sets, constrained value lists where it matters (environment, business unit, data classification), and enforcement tuned per resource type. New non-compliant resources are blocked with the `deny` effect, existing non-compliant resources are remediated via the `modify` effect, and tag inheritance pulls values down from parent scopes where they should be uniform. Exemptions follow a defined approval workflow rather than living as silent overrides.

### DevOps Integration

The DevOps integration is what makes the program defensible long-term: catching configuration and code-level risk before it ships, not after. Defender for DevOps connects to the Azure DevOps organization so the same Defender for Cloud surface that shows runtime posture also shows pre-deployment signal.

In the pipeline itself, IaC templates (Bicep, ARM, Terraform) are scanned for misconfigurations before merge, secrets scanning catches credentials and tokens that should not reach the repo, and CI/CD telemetry surfaces risky changes at PR time so developers can fix them in context rather than waiting on a security ticket weeks later. Policy definitions themselves live in the same DevOps repos as the workloads they govern and deploy through pipelines with review gates, which keeps policy changes auditable and reversible the same as any other code change.

### Operating Model

None of this works long-term without a clear ownership model. Security owns the program end-to-end (definitions, initiatives, exception decisions) while the day-to-day remediation lives with the teams closest to the work: infrastructure for platform-level findings, DevOps for code- and pipeline-level findings, and individual workload owners for application-tier issues. Routing into ServiceNow and Azure DevOps respectively is the mechanism that makes that distribution work without manual hand-offs.

Exceptions follow a defined approval path with time-bound review rather than living as silent overrides, and the policy-as-code workflow means every standard change is reviewable and reversible the same way any other code change is. The operating cadence (posture review, initiative review, policy refresh) is being formalized as the rollout matures, with the goal of keeping the program from drifting back toward the chaotic baseline it replaced.

## Architecture Diagram

![DevOps security pipeline architecture]({{ '/assets/images/portfolio/defender-cloud/devops-pipeline.svg' | relative_url }})

## Where It Stands

This is genuinely ongoing work, and the writeup will mature alongside it. Current focus is consistent posture management coverage and getting the first wave of policy-as-code patterns landed in DevOps. Future updates here will document what got built, what we changed mid-flight, and the outcomes.

## Templates & Code

Sanitized policy definitions, pipeline templates, and deployment patterns will be published in the [Tech-Cookbook repo](https://github.com/MapleCheeze/Tech-Cookbook) as they're cleared for sharing.
