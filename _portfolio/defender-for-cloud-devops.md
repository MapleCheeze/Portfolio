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
<!-- Tier strategy (Foundational vs Defender Plans), subscription onboarding, regulatory standards mapped (ISO, NIST), recommendations triage workflow. -->

### Governance Foundation
<!-- Management group hierarchy, Azure Policy initiatives, RBAC model, tagging standards, naming conventions. -->

### DevOps Integration
<!-- Pipeline tasks for secret scanning, IaC scanning (Bicep/ARM/Terraform), Defender for DevOps integration, branch policies enforcing reviews on policy changes. -->

### Operating Model
<!-- Who owns what, how exceptions get raised and approved, how remediations are routed, how this fits with existing security ops. -->

## Architecture Diagram

![DevOps security pipeline architecture]({{ '/assets/images/portfolio/defender-cloud/devops-pipeline.svg' | relative_url }})

## Where It Stands

This is genuinely ongoing work, and the writeup will mature alongside it. Current focus is consistent posture management coverage and getting the first wave of policy-as-code patterns landed in DevOps. Future updates here will document what got built, what we changed mid-flight, and the outcomes.

## Templates & Code

Sanitized policy definitions, pipeline templates, and deployment patterns will be published in the [Tech-Cookbook repo](https://github.com/MapleCheeze/Tech-Cookbook) as they're cleared for sharing.
