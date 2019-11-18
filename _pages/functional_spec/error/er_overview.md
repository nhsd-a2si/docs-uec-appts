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

If the SSP determines the endpoint is valid using the supplied ASID, then it will forward the request to the FHIR endpoint of the Provider system.  The SSP will act as a true proxy here and passthrough requests and responses between Consumer and Provider systems.

However, there are instances where the request will fail before the Provider system receives the requests.

SSP will return specific HTML error codes under these circumstances as per the following approach:

https://developer.nhs.uk/apis/spine-core/api_spine-operationoutcome.html

https://developer.nhs.uk/apis/spine-core/ssp_implementation_guide.html

Here are examples of errors returned by SSP as error codes:

| HTTP Code | Issue Type    | Description of Error                                                                                                           |
|-----------|---------------|--------------------------------------------------------------------------------------------------------------------------------|
| 403        | forbidden      | The sender or receiver’s ASID is not authorised for this interaction.                                                          |
| 405        | not-supported  | Bad request for an unsupported HTTP verb such as TRACE.                                                                        |
| 415        | not-supported  | A consumer application asked for an unsupported media type.                                                                    |
| 502        | transient      | A downstream server is offline.  This will mean the forwarding of the request to the Provider system failed as it was offline. |
| 504        | transient      | A downstream server timed out.  This will mean SSP forwarded the request to the Provider system but it received a timeout.     |

### Consumer responsibilities:

1. Log errors returned by SSP for incident investigation by IT support staff
2. Inform end-user with a suitable message appropriate to the business flow e.g. critical error with advice to call local IT helpdesk, or business process options to warn users to choose another service
3. Ensure information for appropriate local incident management is captured

**Consumer → SSP → Provider**

Provider will respond to errors processing requests from a Consumer system as per the guidance below.  The SSP will forward the responses unchanged.

For Care Connect appointment workflows, the process is very similar to GP Connect.  However, the Care Connect APIs have standardised on the approach to error handling to use the standard HL7 FHIR OperationOutcome resource.

The error code guidance is provided for each capability in the <a href="https://developer.nhs.uk/apis/nhsscheduling-1.0.4-alpha/developing.html" target="_blank">NHS FHIR Scheduling API development section</a>

### Provider System responsibilities

1. Log errors locally for incident investigation by IT support staff.  If the Request is malformed, this should be logged specifically as a Consumer system issue.  Details of the Consumer system should be logged to support investigation e.g. Org ID.
2. On error send an appropriate HTML error code and an OperationOutcome resource. Use the sections of the OperationOutcome resource to send detailed information back to the Consumer system on what went wrong and why. This is especially important if there was an error in the Request, as this will help the Consumer support function diagnose what is wrong with their system or configuration.
3. As a minimum the OperationOutcome resource must contain:
  * ID - a Provider id for the outcome e.g. a local ID to identify local error codes or a text description
  * An issue severity code
  * An issue code
  
The next table details the appropriate error code return values to be sent by Provider systems for important common issues that may occur for each interaction.  In addition, the table details specific information that should be appended into the OperationOutcome response by Provider systems.  Providers MUST implement these as a minimum.
