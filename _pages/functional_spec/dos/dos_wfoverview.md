---
title: DoS Workflow Overview
sidebar: dos_sidebar
keywords: specification
permalink: dos_wfoverview.html
toc: false
folder: dos
---

## Workflow Overview

The overall workflow for the booking process is as follows:

1. Patient triage/assessment
2. **Service discovery
3. **Endpoint discovery
4. Slot discovery
5. Attempt booking
6. Confirm booking

The bold items in the list above indicate where in the process the DoS is involved. As discussed elsewhere, the actualy endpoint address will be stored in a separate directory (SDS). The DoS will provide a pointer (ASID) to the correct directory entry. 

Each SDS directory entry will correspond to the specific schedule resource on the target provider system. Therefore it can be assumed that a system could have multiple entries on the directory (SDS). 

As a provider system, it is therefore expected that there will be a mechanism in the system to link diaries/schedules to an ASID. This will then be the "grouping factor" on the slots that are returned by a "get slots" request from a consuming system.

## Important DoS workflow considerations

* What if a service is profiled for both triage outcomes that are appropriate for an appointment and other outcomes that are not appropriate?

* How do you know what type of booking interaction is required by the provider system? Is it stored on the DoS?

* If a provider system is compliant  GP Connect and Care Connect could you get two endpoints on SDS for the same DoS service?
