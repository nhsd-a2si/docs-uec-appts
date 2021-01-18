---
title: Authentication with Care Connect
sidebar: overview_sidebar
keywords: specification
permalink: fs_authentication.html
toc: false
folder: functional_spec
---


[//]: # (Broken Links by line number below:)
[//]: # (60 - security_authorisation.html)
[//]: # (152 - development_general_api_guidance.html#service-root-url - linked to GPC section)
[//]: # (154 - integration_spine_directory_service.html - DELETED)
[//]: # (208 - development_api_security_guidance.html#authorisation-of-access-to-endpoints - linked to GPC section)
[//]: # (284 - integration_cross_organisation_audit_and_provenance.html#sub-subject-claim - fixed link so now points at own documentation)
[//]: # (<DR> These look to be relative links to GP Connect documentation?? - I have made them absolute but will need to check with KG)

Note: for GP Connect Authentication please see <a href="https://developer.nhs.uk/apis/gpconnect-1-2-7/development_api_security_guidance.html" target="_blank">here</a>

## Introduction

The main principle in the approach to authentication is to authorise the consumer **system** rather than the user. Therefore there is no dependency on passing through a users strongly authenticated identity and role (such as via a smartcard) to authorise the transaction. This approach will always be the case for viewing and booking slots. There may be a future requirement for more granular authorisation when doing modification and retrieval operations such as third party cancelling and rebooking.

In order to allow the Provider to trust requests from Consumer systems, we need to implement support for Authorisation. In the fullness of time, this is expected to be performed by NHS Identity (AKA NHS Identity).  This process will provide both system and user Authorisation with signed tokens.

Prior to the delivery of NHS Identity for this purpose, the SSP will validate requests and could potentially block unauthorised requests.  Therefore, Provider systems can trust the system request from SSP.

To support audit and provenance, the information about both the Consumer system and the authenticated user MUST be passed into the API calls in the form of an OAuth Access (bearer) token - specifically an encoded JSON web token.

In the future NHS Identity solution will provide an authorisation endpoint that can grant these tokens to authorised users/systems, but until that service is available the calling system must generate the token itself. The specification of this token, what should be in it, and how it can be generated can be found in the below.

## Configuring a new consumer service

When a new consumer or provider system is assured for booking using the Care Connect standard the following steps are taken:

1. Each Consumer and Provider service created as an App Registration in the directory.
  - This is done at a fine grained detailed level, so if many Provider or Consumer services are being run on one instance of a system, of which many instances have been deployed, the App registration is done at the 'Service' level.
2. Several groups will be created, but they’re created once before anyone can go live:
  * urn:nhs:names:services:careconnect:fhir:rest:read:slot
    * Membership of this group indicates that the following organisations represented by this app registration have all been assured to be allowed to view slots:
        * the Service
        * the Organisation delivering the service
        * the system being used
        * and the supplier of that system
    * urn:nhs:names:services:careconnect:fhir:rest:create:appointment
     * Membership of this group indicates that the following organisations represented by this app registration have all been assured to be allowed to book appointments:
        * the Service
        * the Organisation delivering the service
        * the system being used
        * and the supplier of that system

  Separating these groups provides for an application viewing available slots but not have authority to book appointments, for example this might be a dashboard or monitoring application.

  In due course further groups will be defined such as: urn:nhs:names:services:careconnect:fhir:rest:delete:appointment
  These new groups will be documented here.

## Use of bearer tokens

An output of authorising access to an API is the provision of a JSON Web Token (see GP Connect documentation for some more guidance on this subject: [authorising access](https://developer.nhs.uk/apis/gpconnect-1-2-7/development_api_security_guidance.html#authorisation-of-access-to-endpoints){:target="_blank"} for UEC booking (Care Connect) the same guidance applies). This MUST be passed in the API calls to ensure the systems being called are able to verify that the user has been authorised to see the resources requested. This JWT is also used for audit purposes, so the API implementation (and the SSP in the case of a call brokered through that service) can record the user context in it's audit trail.

In order to achieve this, the Consumer MUST include Access token in the HTTP authorisation header as an oAuth Bearer Token (as outlined in [RFC 6749](https://tools.ietf.org/html/rfc6749){:target="_blank"}) in the form of a JSON Web Token (JWT) as defined in [RFC 7519](https://tools.ietf.org/html/rfc7519){:target="_blank"}.

An example such an HTTP header is given below:

```
     Authorization: Bearer jwt_token_string
```

API Provider systems SHALL respond to oAuth Bearer Token errors in line with [RFC 6750 - section 3.1](https://tools.ietf.org/html/rfc6750#section-3.1){:target="_blank"}.

It is highly recommended that standard libraries are used for creating the JWT as constructing and encoding the token manually may lead to issues with parsing the token. A good source of information about JWT and libraries to use can be found on the [JWT.io site](https://jwt.io/){:target="_blank"}


## JWT without an Authorisation Server ##

The new national authentication service is not yet in place, so it is not currently possible to request an Access token from that service. In the interim, Consumer systems are expected to either use a local service to generate tokens, or generate a new JWT for each API request themselves. A consumer generated JSON Web Token (JWT) SHALL consisting of three parts seperated by dots `.`, which are:

- Header
- Payload
- Signature

### Header ###

Where Consumer systems are generating the JWT locally, they SHALL generate an Unsecured JSON Web Token (JWT) using the 'none' algorithm parameter in the header to indicate that no digital signature or MAC has been performed (please refer to section 6 of [RFC 7519](https://tools.ietf.org/html/rfc7519){:target="_blank"} for details).

```json
{
  "alg": "none",
  "typ": "JWT"
}
```

### Payload ###

Consumers systems SHALL generate a JWT Payload conforming to the requirements set out in the [JWT Payload](#jwt-payload) section of this page.

### Signature ###

Consumer systems SHALL generate an empty signature.

### Complete JWT ###

The final output is three Base64url encoded strings separated by dots (note - there is some canonicalisation done to the JSON before it is Base64url encoded, which the JWT code libraries will do for you).

```shell
eyJhbGciOiJub25lIiwidHlwIjoiSldUIn0.eyJpc3MiOiJodHRwczovL2Nhcy5uaHMudWsiLCJzdWIiOiJodHRwczovL2ZoaXIubmhzLnVrL0lkL3Nkcy1yb2xlLXByb2ZpbGUtaWR8Mzg3NDI5Nzg1MzA5Mjc1IiwiYXVkIjoiaHR0cHM6Ly9jbGluaWNhbHMuc3BpbmVzZXJ2aWNlcy5uaHMudWsiLCJleHAiOjE0Njk0MzY5ODcsImlhdCI6MTQ2OTQzNjY4NywicmVhc29uX2Zvcl9yZXF1ZXN0IjoiZGlyZWN0Y2FyZSIsInNjb3BlIjoicGF0aWVudC8qLnJlYWQiLCJyZXF1ZXN0aW5nX3N5c3RlbSI6Imh0dHBzOi8vZmhpci5uaHMudWsvSWQvYWNjcmVkaXRlZC1zeXN0ZW18MjAwMDAwMDAwMjA1IiwicmVxdWVzdGluZ191c2VyIjoiaHR0cHM6Ly9maGlyLm5ocy51ay9JZC9zZHMtcm9sZS1wcm9maWxlLWlkfDQzODcyOTM4NzQ5MjgifQ.
```

NOTE: The final section (the signature) is empty, so the JWT will end with a trailing `.` (this must not be omitted, otherwise it would be an invalid token).


## JWT Payload ##

Consumers **SHALL** populate the payload section of the JWT with the following claims:

- [`iss`](#iss-issuer-claim) (issuer)
- [`sub`](#sub-subject-claim) (subject)
- [`aud`](#aud-audience-claim) (audience)
- [`exp`](#exp-expiry-claim) (expiry)
- [`iat`](#iat-issued-at-claim) (issued at)
- [`reason_for_request`](#reason_for_request-claim)
- [`requested_scope`](#requested_scope-claim)
- [`requesting_device`](#requesting_device-claim)
- [`requesting_organization`](#requesting_organization-claim)

Consumers **COULD** optionally populate the payload section of the JWT with the following claims. Provider systems **MUST** cope with it being both present or absent:

- [`requesting_practitioner`](#requesting_practitioner-claim)

<br>
Please see details below on how to populate each claim.

#### `iss` (issuer) claim

Consumer systems token issuer URI.

As the consuming system is presently responsible for generating the access token, this **SHALL** contain the URL of the Spine endpoint of the consumer system.

In future OAuth2 implementation, the `iss` claim will contain the URL of the OAuth2 authorisation server token endpoint.

**Example**: `"iss": "https://consumersupplier.thirdparty.nhs.uk/"`

---

#### `sub` (subject) claim

ID for the user on whose behalf this request is being made. Matches [`requesting_practitioner.id`](#requesting_practitioner-claim).

**Example**: `"sub": "10019"`

---

#### `aud` (audience) claim

The service root URL of the provider system.

This is the value returned from the SDS endpoint lookup service in the `nhsMhsEndPoint` field.

**Example**: `"aud": "https://providersupplier.thirdparty.nhs.uk/STU3/1"`
<br>
(Please see GP Connect documentation for more guidance on this subject: [service root URL](https://developer.nhs.uk/apis/gpconnect-1-2-7/development_general_api_guidance.html#service-root-url){:target="_blank"} for UEC booking (Care Connect) the same guidance applies).

---

#### `exp` (expiry) claim

Identifies the expiration time in UTC on and after which the JWT **SHALL NOT** be accepted for processing.

The expiration time **SHALL** be set to 5 minutes after the token creation time (populated in the [`iat` claim](#iat-issued-at-claim)).

The value must be an integer representing seconds past 01 Jan 1970 00:00:00 UTC, i.e. [UNIX time](https://en.wikipedia.org/wiki/Unix_time){:target="_blank"}.

Providers **SHALL** reject requests with expired tokens.

**Example**: `"exp": 1469436987`

{% include important.html content="To ensure accuracy of timestamps, and minimise the likelihood of tokens being rejected due to clock skew providers and consumers **SHALL** synchronise their server clocks with NHS Network Time Protocol (NTP) servers." %}

---

#### `iat` (issued at) claim

The time the request and token were generated in UTC.

The value **SHALL** be an integer representing seconds past 01 Jan 1970 00:00:00 UTC, i.e. [UNIX time](https://en.wikipedia.org/wiki/Unix_time){:target="_blank"}.

**Example**: `"iat": 1469436687`

---

#### `reason_for_request` claim

The purpose for which access is being requested.

As UEC apointment booking only supports usage for direct care, this value **SHALL** be set to `directcare`.

**Example**: `"reason_for_request": "directcare"`

---

#### `requested_scope` claim

The scope of the request.

Please the table below for which values to populate.

| Claim value | Operation | Description |
|-------|-------|-------------|
| `patient/appointment.write` | Book / Cancel |Booking in an appointment |
| `organization/slot.read` | Slot Search |Searching for available slots |

Providers should also read the associated [Security guidance](https://developer.nhs.uk/apis/gpconnect-1-2-7/development_api_security_guidance.html){:target="_blank"} GP Connect documentation in relation to this claim, for UEC booking (Care Connect) the same guidance applies.

---

#### `requesting_device` claim

The system or device making the request, populated as a minimal [Device](https://www.hl7.org/fhir/STU3/device.html){:target="_blank"} resource.

The consumer **SHALL** populate the following [Device](https://www.hl7.org/fhir/STU3/device.html){:target="_blank"} fields:

- an `identifier` element, with:
  - `system` containing a consumer-defined system URL representing the type of identifier in the value field, e.g. `https://consumersupplier.com/Id/device-identifier`
  - `value` containing the device or system identifier
- `model` with the consumer product or system name
- `version` with the version number of the consumer product or system

The [Device](https://www.hl7.org/fhir/STU3/device.html){:target="_blank"} resource populated in this claim is a minimally populated resource to convey key details for audit, conforming to the base STU3 FHIR resources definition, and is not required to conform to a GP Connect FHIR resource profile.

**Example**:

<pre class="remove-highlight"><code class="no-highlight">"requesting_device": {
  "resourceType": "Device",
  "identifier": [
    {
      "system": "https://consumersupplier.com/Id/device-identifier",
      "value": "CONS-APP-4"
    }
  ],
  "model": "Consumer product name",
  "version": "5.3.0"
}
</code></pre>

---

#### `requesting_organization` claim

The consumer organisation making the request, populated as a minimal [Organization](https://www.hl7.org/fhir/STU3/organization.html){:target="_blank"} resource.

The consumer **SHALL** populate the following [Organization](https://www.hl7.org/fhir/STU3/organization.html){:target="_blank"} fields:

- `name` with the name of the organisation
- an `identifier` element, with:
  - `system` containing `https://fhir.nhs.uk/Id/ods-organization-code`, and
  - `value` containing the ODS code of the organisation

{% include important.html content="In consumer system topologies where consumer applications are provisioned via a portal or middleware hosted by another organisation, it is vital for audit purposes that the organisation populated in the JWT reflects the organisation from where the request originates, rather than the hosting organisation.<br/>
This is normally determined as the organisation of the logged on user making the request." %}

The [Organization](https://www.hl7.org/fhir/STU3/organization.html){:target="_blank"} resource populated in this claim is a minimally populated resource to convey key details for audit, conforming to the base STU3 FHIR resources definition, and is not required to conform to a GP Connect FHIR resource profile.

**Example**:

<pre class="remove-highlight"><code class="no-highlight">"requesting_organization": {
  "resourceType": "Organization",
  "identifier": [
    {
      "system": "https://fhir.nhs.uk/Id/ods-organization-code",
      "value": "A1001"
    }
  ],
  "name": "111 North East Service"
}
</code></pre>

---

#### `requesting_practitioner` claim

The user making the request, populated as a minimal [Practitioner](https://www.hl7.org/fhir/STU3/practitioner.html){:target="_blank"} resource.

To contain the logged on user's identifier(s) (for example, login details / username). Where the user has both a local system user role as well as a nationally-recognised user role, then both **SHALL** be provided.

{% include important.html content="This field **SHALL NOT** be populated with fixed values or a generic \"system\" user. The values **SHALL** represent the logged on user making the request." %}

The consumer **SHALL** populate the following [Practitioner](https://www.hl7.org/fhir/STU3/practitioner.html){:target="_blank"} fields:

- `id` with a unique [logical](https://www.hl7.org/fhir/STU3/resource.html#id){:target="_blank"} identifier (e.g. user ID or GUID) for the logged on user. This **SHALL** match the value of the [sub](#sub-subject-claim) claim.
- `name` with:
  - `family` containing the user's family name
  - `given` containing the user's given name
  - `prefix` containing the user's title, where available
- an `identifier` element with:
  - `system` containing `https://fhir.nhs.uk/Id/sds-user-id`
  - `value` containing the SDS user ID from the user's NHS smartcard, or the value `UNK` if the user is not logged on with an NHS smartcard
- an `identifier` element with:
  - `system` containing `https://fhir.nhs.uk/Id/sds-role-profile-id`
  - `value` containing the SDS user role profile ID from the user's NHS smartcard, or the value `UNK` if the user is not logged on with an NHS smartcard
- an `identifier` element containing a unique local user or user-role identifier for the logged on user (e.g. user ID, user role ID, logon name) from the consumer system:
  - `system` containing a consumer-defined system URL representing the type of identifier in the value field, e.g. `https://consumersupplier.com/Id/user-guid`
  - `value` containing the unique local identifier for the logged on user

{% include important.html content="Providers should be aware of variance in the population of the `identifier` field amongst existing consumer systems when reading this claim, specifically the latter two elements (SDS role profile ID, and local user identifier) are not always present." %}

The [Practitioner](https://www.hl7.org/fhir/STU3/practitioner.html){:target="_blank"} integration_cross_organisation_audit_and_provenance.html#sub-subject-claim resource populated in this claim is a minimally populated resource to convey key details for audit, conforming to the base STU3 FHIR resources definition, and is not required to conform to a GP Connect FHIR resource profile.

**Example**:

<pre class="remove-highlight"><code class="no-highlight">"requesting_practitioner": {
  "resourceType": "Practitioner",
  "id": "10019",
  "identifier": [
    {
      "system": "https://fhir.nhs.uk/Id/sds-user-id",
      "value": "111222333444"
    },
    {
      "system": "https://fhir.nhs.uk/Id/sds-role-profile-id",
      "value": "444555666777"
    },
    {
      "system": "https://consumersupplier.com/Id/user-guid",
      "value": "98ed4f78-814d-4266-8d5b-cde742f3093c"
    }
  ],
  "name": [
    {
      "family": "Jones",
      "given": [
        "Claire"
      ],
      "prefix": [
        "Dr"
      ]
    }
  ]
}</code></pre>

### JWT payload full example ###

```json
{
  "iss": "https://consumersupplier.thirdparty.nhs.uk/",
  "sub": "10019",
  "aud": "https://providersupplier.thirdparty.nhs.uk/STU3/1",
  "exp": 1469436987,
  "iat": 1469436687,
  "reason_for_request": "directcare",
  "requested_scope": "patient/appointment.write",
  "requesting_device": {
    "resourceType": "Device",
    "identifier": [
      {
        "system": "https://consumersupplier.com/Id/device-identifier",
        "value": "CONS-APP-4"
      }
    ],
    "model": "Consumer product name",
    "version": "5.3.0"
  },
  "requesting_organization": {
    "resourceType": "Organization",
    "identifier": [
      {
        "system": "https://fhir.nhs.uk/Id/ods-organization-code",
        "value": "A1001"
      }
    ],
    "name": "Test Hospital"
  },
  "requesting_practitioner": {
    "resourceType": "Practitioner",
    "id": "10019",
    "identifier": [
      {
        "system": "https://fhir.nhs.uk/Id/sds-user-id",
        "value": "111222333444"
      },
      {
        "system": "https://fhir.nhs.uk/Id/sds-role-profile-id",
        "value": "444555666777"
      },
      {
        "system": "https://consumersupplier.com/Id/user-guid",
        "value": "98ed4f78-814d-4266-8d5b-cde742f3093c"
      }
    ],
    "name": [
      {
        "family": "Jones",
        "given": [
          "Claire"
        ],
        "prefix": [
          "Dr"
        ]
      }
    ]
  }
}
```

## Provenance ##

Provider systems **SHALL** ensure that all additions, amendments or logical deletions to administrative and clinical data made via an API is clearly identified with information regarding the provenance of the data (such as timestamp, details of consumer system, details of user (including role)), so it is clear which information has been generated through an API rather than through the provider system itself.

Provider systems **SHALL** record the following provenance details of all API personal and sensitive personal data recorded within the system:

- author details (identified through unique ID), including name and role
- data entered by (if different from author)
- date and time (to the second) entered
- originating organisation
- API interaction

Provider system **MAY** use the organisation id passed in this or the FHIR profiles to manage authorisatios locally.  For example, refuse requests from organisations that should not be permitted to book into you.  This is not mandatory as a DOS search already controls business rules determining what UEC services can be booked into.

We say we are passing in user role for future use and audit, we do not require use of this for authorising requests.

## Migration to NHS Identity

It is expected that in the future the authorisation process will migrate away from HSCD to NHS Identity. Although the process will be bradly the same there are likely to be some differences. These differences and the process for migrating over to NHS Identity will be documented here in due course.
