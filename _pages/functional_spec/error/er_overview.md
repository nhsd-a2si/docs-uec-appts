---
title: Error Handling - Overview
keywords: fhir development
tags: [fhir,development]
sidebar: error_sidebar
permalink: er_overview.html
summary: "Implementation guidance for developers - focusing on error handling"
---

## Introduction

There are several points at which an error may occur to prevent the appointment booking operations completing successfully.

The following guidance is for Care Connect Appointment booking.  GP Connect is very similar but has specific guidance <a href="https://nhsconnect.github.io/gpconnect/development_fhir_error_handling_guidance.html" target="_blank">here</a>.

## Overview

Error codes are returned by the APIs used to connect to each service.  Error codes are meant for developer use only - they should not be presented to end-users.  Instead, Consumer applications should interpret the codes and provide user-friendly resolution steps on failure.  Consumer and Provider systems should record the detailed error codes in local logs in order to support service incident investigation.

As the process is initiated by a Consumer there could be several stages that create issues - this table provides a high-level overview of each stage and then follows with specific sections to detail the error handling process and Consumer and Provider responsibilities.

| Interaction Flow          | Error Handling Overview                                                                               |
|---------------------------|-------------------------------------------------------------------------------------------------------|
| Consumer→DOS                                  | DOS APIs return a number of significant errors specific to the actual API failing. These are all self-contained in that process.These are documented below and will not affect the ongoing activity unless the data returned in the query is erroneous and then means the next stages of the process fail.                                                                                                 |
| Consumer→SDS                                  | SDS processes will fail if connectivity to SDS does not work, authentication of the Consumer system does not work or badly formed requests are sent in.A successful request should return the correct information on the endpoints to be used for the next stage of the process with SSP, however, if the data supplied from DOS is invalid there may be a successful return with no endpoint information. |
| Consumer→SSP                                  | SSP processes will fail if connectivity to SSP does not work, authentication of the Consumer system does not work or badly formed requests are sent in.A successful request should be passed through to the Provider endpoint and processed by that system, but these operations could fail.                                                                                                               |
| Consumer→SSP→Provider                       | If SSP successfully proxies a request through to a Provider endpoint, it will return an error code from that endpoint.                                                                                                                                                                                                                                                                                     |
