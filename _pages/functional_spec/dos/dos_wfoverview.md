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
2. Service discovery
3. Endpoint discovery
4. Slot discovery
5. Attempt booking
6. Confirm booking



## Important DoS workflow considerations

* What if a service is profiled for both triage outcomes that are appropriate for an appointment and other outcomes that are not appropriate?

* How do you know what type of booking interaction is required by the provider system? Is it stored on the DoS?

* If a provider system is compliant  GP Connect and Care Connect could you get two endpoints on SDS for the same DoS service?
