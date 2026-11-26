---
title: "Argus - npm Supply Chain Malware Detection Registry Proxy"
summary: "White Hat School team project. A registry proxy that intercepts npm install requests, inspects packages for malicious behavior and decides allow or block"
type: team
team_size: "8 members"
role: "PM · Scanner"
period: "2026.08 ~ TODO: end date"
tags: ["npm", "Supply Chain Security", "Static/Dynamic Analysis", "PM"]
cat: malware
order: 1
---

## Overview
A **registry proxy** that inspects npm packages before an organization installs them, built to counter open-source supply chain attacks. It targets enterprise security staff, focuses on prevention and detection, and is scoped to the npm ecosystem.

- Flow: `npm install` → Gateway / Verdaccio → package inspection → ALLOW / REVIEW / DENY → review on the Dashboard
- Final stack: Verdaccio, Fastify Gateway, GuardDog (first-pass static analysis), Fakeium (lightweight JS dynamic sandbox), Redis/BullMQ, NestJS/PostgreSQL, React/Vite dashboard

## My Role
Served as both **PM** and **Scanner** developer.
- **PM**: Led schedule, role assignment, collaboration process and mentor feedback for the 8-member team
- **Scanner**: Worked on detection logic and package analysis, and took part in the Tier 1 / Tier 2 inspection implementation

## Architecture
TODO: One architecture diagram (Gateway → Verdaccio → Scanner → Dashboard) and where the Scanner fits

## Scanner Details
> Detailed write-up to be added by me

### Design
- Tier 1: Static analysis based on GuardDog
- Tier 2: Dynamic verification of static findings, designed as a "static hypothesis verifier" that labels each finding CONFIRMED / NOT_OBSERVED / REFUTED
- Dynamic analysis starts with Fakeium (logs JS API calls inside a V8 isolate); a container-based real-execution runner is planned as a later extension

### What I Implemented
TODO: Items you implemented or analyzed yourself (e.g. detection logic, rules, pipeline integration)

### Problems and Solutions
TODO: False positive / false negative cases and how they were resolved

## PM Work
- **Kickoff and operations**: Ran two regular meetings a week plus weekly mentoring after kickoff
- **Role design**: Split tracks (Gateway, Registry, Scanner, Data, etc.) according to members' experience, and adjusted the organization using team feedback
- **Scope control**: Within a roughly 2.5-month window, limited deliverables to Verdaccio proxy + GuardDog engine + custom dashboard, excluding a custom registry, multi-ecosystem support and GNN detection
- **Schedule**: Targeted an MVP in August, then added dynamic analysis and AI detection step by step in September
- **Collaboration rules**: Established a main / develop / feature branch strategy, an Issue → PR → code review → merge flow, and commit conventions
- **Mentor feedback**: Reordered the design process after feedback to define threat modeling and workflows before architecture
- **Prototype**: During research, built a Verdaccio + proxy + GuardDog prototype that intercepts install requests and allows them or blocks with 403

TODO: Links to meeting notes, schedules and other evidence

## Results
TODO: Deliverables, numbers, GitHub link

## Takeaways
TODO: One or two lines (from both PM and Scanner perspectives)
