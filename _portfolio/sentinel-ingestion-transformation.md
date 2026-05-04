---
title: "Sentinel SIEM Ingestion Transformation"
excerpt: "Designed ingestion-time transformations in Microsoft Sentinel to normalize, enrich, and filter logs before they hit the workspace."
header:
  teaser: /assets/images/portfolio/sentinel-teaser.jpg
toc: true
toc_sticky: true
toc_label: "On this page"
sidebar:
  - title: "Domain"
    text: "SIEM Architecture & Detection Engineering"
  - title: "Tools Used"
    text: "Microsoft Sentinel, Data Collection Rules (DCR), KQL, Log Analytics"
  - title: "Skills Demonstrated"
    text: "Log pipeline design, ingestion-time transformation, cost optimization, data normalization"
  - title: "Code & Templates"
    text: "[tech-cookbook/sentinel/ingestion-transformations](https://github.com/keshawn-white/tech-cookbook/tree/main/sentinel/ingestion-transformations)"
---

## Overview

<!-- The problem: noisy logs, schema drift, ingestion costs blowing up, or analyst fatigue.
Why ingestion-time transformations are the right lever vs post-ingest workspace queries. -->

## Architecture

<!-- ![TI detection ingestion architecture](/assets/images/portfolio/sentinel/ti-detection-integrations.svg) -->
<!-- Walk through: source connectors → DCR → workspace.
Note where filtering happens, where enrichment happens, and what stays in raw form. -->

## Transformations Built

### Filtering
<!-- Examples of low-value events dropped at ingest, with KQL transform snippets. -->

### Normalization
<!-- Schema mapping (e.g., common identity fields across MSFT, Cisco, Okta). -->

### Enrichment
<!-- Adding GeoIP, asset criticality tags, user role attributes at ingest time. -->

## Implementation

<!-- DCR-based deployment, version control, how transformations are tested in lower environments,
rollback strategy when a transformation regresses. -->

## Outcomes

<!-- Cost savings (% reduction in ingestion volume), detection improvements, analyst workflow impact.
If you have before/after numbers, this is where they live. -->

## Lessons Learned

<!-- What you'd do differently. Pitfalls (e.g., transformations that broke detections,
schema changes that cascaded). -->
