---
title: Error Handling - Implementation Guidance
keywords: fhir development
tags: [fhir,development]
sidebar: error_sidebar
permalink: er_errorhandling.html
summary: "Implementation guidance for developers - focusing on error handling"
---

This page is intended for use by software developers looking to build a conformant NHS FHIR Scheduling API interface for UEC flows.
The purpose of response values is to support diagnostic investigation of issues between consumers and providers.

## Spine Secure Proxy responses

Spine Secure Proxy will respond to a FHIR request that fails to be sent and processed by the Provider system with a specific set of errors:

https://developer.nhs.uk/apis/spine-core/resources_error_handling.html#spine-security-proxy-ssp-errors

These include checking the ASID details and if the downstream Provider system is unresponsive.

Consumer systems need to be able to deal with these error types appropriately and display meaningful information to end users.

## FHIR resource validation with Providers

### Incomplete data - expected behaviour

Where resource instance data available in clinical systems is either insufficient or corrupt and thus a resource cannot be constructed by a provider system which meets the associated FHIR profile, the following guidance describes expected behaviour:

**Scenario: GET resource by logical ID**

An HTTP 500 error should be returned with an OperationOutcome resource providing diagnostic details. This may include details of the resource in the location element.

**Scenario: FHIR response bundles**

When a response bundle contains multiple resources, one or more of which cannot be populated as available data does not enable the resource in question to be populated to validate the associated profile, the provider will behave as follows: The request as a whole will error with a 500 HTTP Status returned, together with the appropriate OperationOutcome resource providing diagnostic detail of the error.

### Resource transactions

When performing an update or creating [resource transactions](https://www.hl7.org/fhir/STU3/http.html#transactional-integrity), providers:

-	SHALL **validate the content against valid profiles** and business rules before creating/updating the resource
-	MAY apply business rules that alter the content
-	MAY merge updated content with existing content

Providers SHALL validate the existence of any referenced resources when creating or updating a resource. For example, a `Slot` reference (for example, `Slot/D497DB00-99AA-11E5-A837-0800200C9A66`) used when creating a new `Appointment` would be checked for existence on the server and an error returned (and the create interaction aborted) if the slot does not exist.

Providers SHALL provide a read interaction for every resource it accepts update interactions on.

Consumers SHALL follow the pattern described in the [Transactional Integrity](https://www.hl7.org/fhir/STU3/http.html#transactional-integrity) section of the base FHIR specification, built on top of version-aware updates, for updating resources.

## FHIR&reg; resource interactions

### Requests

Providers SHALL be able to consume and process the following requests for NHS FHIR Scheduling FoT:

| Interaction | Path | Request verb | Request content-type | Body | Prefer | Conditional |
| ----------- | ---- | ------------ | -------------------- | ---- | ------ | ----------- |
| `read`   | `/[type]/[id]` | `GET` | N/A | N/A | N/A | `ETag` |
| `update` | `/[type]/[id]` | `PUT` | R | Resource | O | `If-Match`|
| `delete` | `/[type]/[id]` | `DELETE` | N/A | N/A | N/A | N/A |
| `create` | `/[type]` | `POST` | R | Resource | O | N/A |
| `search` | `/[type]?` | `GET` | N/A | N/A | N/A | N/A |
| `(operation)` | `/[type]/$[name]` `/[type]/[id]/$[name]` | `POST` <br/> `GET` | R <br/> `application/x-www-form-urlencoded` | Parameters <br/> form data | N/A | N/A |

> N/A = not present, R = required, O = optional

### Responses

Providers SHALL be expected to produce the following responses for NHS FHIR Shceduling FoT:

| Interaction | Response content-type | Body | Location | Content-location | Versioning | Status codes |
| ----------- | --------------------- | ---- | -------- | ---------------- | ---------- | ------------ |
| `read`   | R | R: Resource | N/A | R | `ETag` | `200`, `404`, `410` |
| `update` | R | R: Resource | N/A | R | `ETag` | `200`, `201`, `400`, `404` `405`, `409`, `412`, `422` |
| `delete` | R | R: Operation Outcome | N/A | N/A | N/A | `200`, `204`, `404`, `405`, `409`, `412` |
| `create` | R | R: Resource | R | R | `ETag` | `201`, `400`, `404` `405`, `422` |
| `search` | R | R: Bundle | N/A | N/A | N/A | `200`, `403` |
| `(operation)` | R | R: Parameters/Resource | N/A | N/A | N/A | `200`, `400`, `403`, `404`, `422`  |

> N/A = not present, R = required, O = optional

#### Response codes

Servers SHALL produce the following main [HTTP status codes](http://www.iana.org/assignments/http-status-codes/http-status-codes.xhtml):

| HTTP status code | Description |
| ---------------- | ----------- |
| `200` | OK |
| `201` | Created |
| `400` | Bad request |
| `401` | Unauthorized |
| `403` | Forbidden |
| `404` | Not found |
| `405` | Method not allowed |
| `409` | Conflict |
| `410` | Gone |
| `412` | Precondition failed |
| `415` | Unsupported media type |
| `422` | Unprocessable entity |
| `500` | Internal server error |
| `501` | Not implemented |

#### Errors

If the event of an error response HTTP `4xx` or `5xx` an [OperationOutcome](https://www.hl7.org/fhir/STU3/operationoutcome.html) MUST be returned.

As a minimum the OperationOutcome resource must contain:
  * A provider id for the outcome e.g. a local id to identify local error codes or a text description
  * An issue severity code
  * An issue code

  ***Example***
```
{
  "resourceType": "OperationOutcome",
  "id": "ERR-23451",
  "meta": {
    "profile": [
      "https://www.hl7.org/fhir/STU3/operationoutcome.html"
    ]
  },
  "issue": [
    {
      "severity": "error",
      "code": "value",
      "details": {
        "coding": [
          {
            "system": "https://fhir.nhs.uk/STU3/ValueSet/Spine-ErrorOrWarningCode-1",
            "code": "INVALID_NHS_NUMBER"
          }
        ]
      },
      "diagnostics": "Any further internal debug details i.e. stack trace details etc."
    }
  ]
}
```




##### [Rejecting updates](https://www.hl7.org/fhir/STU3/http.html#2.1.0.10.1)


Providers are permitted to reject update interactions because of integrity concerns or other business rules, and return HTTP status codes accordingly (usually a `422`).

As part of this API, erros of this type MUST be accompanied by an [OperationOutcome](https://www.hl7.org/fhir/STU3/operationoutcome.html) resource that provides additional detail concerning the issue.
