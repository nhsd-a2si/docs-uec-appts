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

### Consumer → DOS

The DOS will return specific errors when searching for services. These are detailed <a href="https://developer.nhs.uk/apis/dos-api/soap_api_errors_1_5.html" target="_blank">here</a>.

**These errors are all about:**
* Technical issues with connecting to DOS, which should be investigated by local IT Support; or
* No valid services being returned, which should be handled locally with agreed processes for widening search parameters.
*Note that successful completion of a DOS Search may occur, but provide incomplete or erroneous data for the booking process to continue due to poor data quality.*

**Common issues with data held in the DOS that will be discovered later:**
* Service information returned that supports booking, but a FHIR scheduling endpoint is not entered against the service or is not formatted correctly.  This will result in failure later when using SDS to retrieve the endpoint information. This is an issue with DOS configuration and should be investigated with the DOS Leads.
* Service information returned but no FHIR endpoint is configured even though booking is permitted.

**Consumer responsibilities:**

1. Log errors returned by DOS for incident investigation
2. Inform end-user with a suitable message appropriate to the business flow e.g. critical error with advice to call local IT helpdesk, or business process options to warn users to choose another service
3. Ensure information for appropriate local incident management is captured

### Consumer → SDS

SDS interactions are LDAP and provide specific error codes for these interactions.

There are several errors that may be returned by SDS:

| HTTP Code | Issue Type    | Description of Error                                                                                                           |
|-----------|---------------|--------------------------------------------------------------------------------------------------------------------------------|
| 403        | forbidden      | The sender or receiver’s ASID is not authorised for this interaction.                                                          |
| 405        | not-supported  | Bad request for an unsupported HTTP verb such as TRACE.                                                                        |
| 415        | not-supported  | A consumer application asked for an unsupported media type.                                                                    |
| 502        | transient      | A downstream server is offline.  This will mean the forwarding of the request to the Provider system failed as it was offline. |
| 504        | transient      | A downstream server timed out.  This will mean SSP forwarded the request to the Provider system but it received a timeout.     |

