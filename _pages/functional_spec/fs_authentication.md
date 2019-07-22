---
title: Authentication with Care Connect
sidebar: overview_sidebar
keywords: specification
permalink: fs_authentication.html
toc: false
folder: functional_spec
---

Note: for GP Connect Authentication please see <a href="https://nhsconnect.github.io/gpconnect/development_api_security_guidance.html" target="_blank">here</a>

## Introduction

The main principle in the approach to authentication is to authorise the consumer **system** rather than the user. Therefore there is no dependency on passing through a users strongly authenticated identity and role (such as via a smartcard) to authorise the transaction. This approach will always be the case for viewing and booking slots. There may be a future requirement for more granular authorisation when doing modification and retrieval operations such as third party cancelling and rebooking.

In order to allow the Provider to trust requests from Consumer systems, we need to implement support for Authorisation. In the fullness of time, this is expected to be performed by NHS Identity (AKA NHS Identity).

For initial rollout the Health and Social Care Directory (HSCD) will be used. This is a mature service and supporting NHS Mail identities.

This uses the standard OAuth 2 client_credentials flow (see: <a href="https://oauth.net/2/grant-types/client-credentials/" target="_blank">OAuth Client Credentials Flow</a>) and has the following key features:

* New Consumer and Provider systems can be implemented and removed with NO effect on other services. 
* It allows central control over authorisation at a capability level 
* All configuration is controlled centrally in HSCD/NHS Identity and those details are passed to the Provider to allow them to make the required authorisation decisions. 
* In addition to the provider system checking the tokens, the SSP can also validate requests and could potentially block unauthorised requests

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
3. Create a 'secret' in HSCD for each Consumer system. 
  * The secret is the equivalent to a password, and as such it is ESSENTIAL that it is strongly protected by the Consumer system
  * there is likely to be a security policy and attached process on the protection of these secrets published in due course

## Authentication workflow

When a Consumer system wants to request Slots or to book an Appointment at a Provider system, a request is made to HSCD for an access token. It includes the secret and the details of the Provider system it's accessing, e.g:

```json
client_id: "id Goes here",
client_secret: "secret goes here",
scope:  [base url of the provider system] + "/.default",
grant_type: "client_credentials"
```

For example these values might be used:
```json
client_id=92d85f9d-0666-49bc-a31c-12b45b04a7de
client_secret=y7rCysA8anvYshLckwwFNs8qnC6JPyCerE7CUAAnGgo=
```

HSCD will then issue a signed access token containing the groups that the Consumer is a member of. This token is valid for one hour. The response will look similar to this:

```json
{
"token_type": "Bearer",
"expires_in": 3600,
"ext_expires_in": 3600,
"access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6Im5iQ3dXMTF3M1hrQi14VWFYd0tSU0xqTUhHUSIsImtpZCI6Im5iQ3dXMTF3M1hrQi14VWFYd0tSU0xqTUhHUSJ9.eyJhdWQiOiJodHRwOi8vYXBwb2ludG1lbnRzLmRpcmVjdG9yeW9mc2VydmljZXMubmhzLnVrOjQ0My9wb2MiLCJpc3MiOiJodHRwczovL3N0cy53aW5kb3dzLm5ldC9lNTIxMTFjNy00MDQ4LTRmMzQtYWVhOS02MzI2YWZhNDRhOGQvIiwiaWF0IjoxNTQ3MDMyNDU1LCJuYmYiOjE1NDcwMzI0NTUsImV4cCI6MTU0NzAzNjM1NSwiYWlvIjoiNDJSZ1lNZ0tEbFZYMnBIMnE5cFhlamJ6MzVtWkFBPT0iLCJhcHBpZCI6IjkyZDg1ZjlkLTA2NjYtNDliYy1hMzFjLTEyYjQ1YjA0YTdkZSIsImFwcGlkYWNyIjoiMSIsImdyb3VwcyI6WyJhYjQxMmZlOS0zZjY4LTQzNjgtOTgxMC05ZGMyNGQxNjU5YjEiLCJkYWNiODJjNS1hZWE4LTQ1MDktODg3Zi0yODEzMjQwNjJkZmQiLCI1NWRhMWM5YS0yY2ViLTQxYTctOWI3Yy0xYzcwMTVlZDFmZGUiXSwiaWRwIjoiaHR0cHM6Ly9zdHMud2luZG93cy5uZXQvZTUyMTExYzctNDA0OC00ZjM0LWFlYTktNjMyNmFmYTQ0YThkLyIsIm9pZCI6IjU4YjI1Zjk5LWQ0MDQtNDQ4My1hNjBhLTQwNmYxY2MzYzg4NyIsInN1YiI6IjU4YjI1Zjk5LWQ0MDQtNDQ4My1hNjBhLTQwNmYxY2MzYzg4NyIsInRpZCI6ImU1MjExMWM3LTQwNDgtNGYzNC1hZWE5LTYzMjZhZmE0NGE4ZCIsInV0aSI6IlI1S2FEa21Rc0VlTk96d1c3WElUQUEiLCJ2ZXIiOiIxLjAifQ.eVSncRYT138bByvEHa00uQpfuZrLvW0b9NPF9tDsxIckjaxEiOWJz1pYpaEJoZPnSxmJjKZ_v7h-0ea21ApB-9dYRE6OZ9Y12CGbDr4IKIbO2Oh0QulU06BzvDrA9hMbLXV2vG06mIcLBE8BAJbJp8ktF4PZ1vmRXd0jxy1YonEFqO9e5QsUoekw7eL_LPBBUlNrUsFedP7eKPdW1uGRrd6i_UmQTDx0tq0cV8NOV-vvQLgKY7GROPjZ1qOx6-3s_oEDL_T65ERFJH4CMcMBOH1HsDf2Ee47pM3-lGlBh7SSLpCVbxpOxAc1O6cULbbbSRuAEyUXuQZroagtqoiiwQ"
}
```

The access_token field in that response contains the actual JWT to be used when making requests to the Provider system specified in the request as 'scope'.

This access_token can then be decoded (for example the following sites: <a href="https://jwt.ms" target="_blank">jwt.ms</a>  or <a href="https://jwt.io" target="_blank">jwt.io</a>).

When decoded the token will look something like the following:
```json
{ // Header section
"typ": "JWT",
"alg": "RS256",
"x5t": "nbCwW11w3XkB-xUaXwKRSLjMHGQ",
"kid": "nbCwW11w3XkB-xUaXwKRSLjMHGQ" // This indicates the id of the public key that can be used to validate the signature
}.{
  "aud": "https://provider url will be here", // This will be set from the requested scope.
  "iss": "https://sts.windows.net/e52111c7-4048-4f34-aea9-6326afa44a8d/", // The issuer, i.e: HSCD - this will change before we go live
  "iat": 1540205024, // Issued at
  "nbf": 1540205024, // Not for use before
  "exp": 1540208924, // Expiry
  "aio": "42RgYOj/WnPNrHf6KrsGL/Nmb+tnAA==",
  "appid": "da94f55e-c638-4fe6-a547-993648947ac3", // The client id (as submitted in the request)
  "appidacr": "1",
  "groups": [
    "99402151-a646-470d-a82a-765024126cc4", // The Identifiers  of the Groups - these values will change before we go live
    "E8e69933-5429-45e9-bbb1-bfd4db3c2b15"
  ],
  "idp": "https://sts.windows.net/e52111c7-4048-4f34-aea9-6326afa44a8d/", // The issuer, i.e: HSCD - this will change before we go live
  "oid": "d70d78d1-afb8-4993-ab68-64722bfa5a95",
  "sub": "d70d78d1-afb8-4993-ab68-64722bfa5a95",
  "tid": "e52111c7-4048-4f34-aea9-6326afa44a8d",
  "uti": "BC6JP5cx9022Tz_CyK5vAA",
  "ver": "1.0"
}.{ // Signature section
[Signature]
}
```

Because this token is signed, the Provider system can trust that the Consumer really is a member of the specified groups. It can also retrieve the public key from the directory and validate that the token hasn't been tampered with. There are standard ways of doing this.

When requests are made to a Provider system, they must include an Authorization http header which takes the form:

```
Authorization	Bearer +  space +  [access_token value from above ]
```

For example using the token shown above:

```
Authorization	Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6Im5iQ3dXMTF3M1hrQi14VWFYd0tSU0xqTUhHUSIsImtpZCI6Im5iQ3dXMTF3M1hrQi14VWFYd0tSU0xqTUhHUSJ9.eyJhdWQiOiJodHRwOi8vYXBwb2ludG1lbnRzLmRpcmVjdG9yeW9mc2VydmljZXMubmhzLnVrOjQ0My9wb2MiLCJpc3MiOiJodHRwczovL3N0cy53aW5kb3dzLm5ldC9lNTIxMTFjNy00MDQ4LTRmMzQtYWVhOS02MzI2YWZhNDRhOGQvIiwiaWF0IjoxNTQ3MDMyNDU1LCJuYmYiOjE1NDcwMzI0NTUsImV4cCI6MTU0NzAzNjM1NSwiYWlvIjoiNDJSZ1lNZ0tEbFZYMnBIMnE5cFhlamJ6MzVtWkFBPT0iLCJhcHBpZCI6IjkyZDg1ZjlkLTA2NjYtNDliYy1hMzFjLTEyYjQ1YjA0YTdkZSIsImFwcGlkYWNyIjoiMSIsImdyb3VwcyI6WyJhYjQxMmZlOS0zZjY4LTQzNjgtOTgxMC05ZGMyNGQxNjU5YjEiLCJkYWNiODJjNS1hZWE4LTQ1MDktODg3Zi0yODEzMjQwNjJkZmQiLCI1NWRhMWM5YS0yY2ViLTQxYTctOWI3Yy0xYzcwMTVlZDFmZGUiXSwiaWRwIjoiaHR0cHM6Ly9zdHMud2luZG93cy5uZXQvZTUyMTExYzctNDA0OC00ZjM0LWFlYTktNjMyNmFmYTQ0YThkLyIsIm9pZCI6IjU4YjI1Zjk5LWQ0MDQtNDQ4My1hNjBhLTQwNmYxY2MzYzg4NyIsInN1YiI6IjU4YjI1Zjk5LWQ0MDQtNDQ4My1hNjBhLTQwNmYxY2MzYzg4NyIsInRpZCI6ImU1MjExMWM3LTQwNDgtNGYzNC1hZWE5LTYzMjZhZmE0NGE4ZCIsInV0aSI6IlI1S2FEa21Rc0VlTk96d1c3WElUQUEiLCJ2ZXIiOiIxLjAifQ.eVSncRYT138bByvEHa00uQpfuZrLvW0b9NPF9tDsxIckjaxEiOWJz1pYpaEJoZPnSxmJjKZ_v7h-0ea21ApB-9dYRE6OZ9Y12CGbDr4IKIbO2Oh0QulU06BzvDrA9hMbLXV2vG06mIcLBE8BAJbJp8ktF4PZ1vmRXd0jxy1YonEFqO9e5QsUoekw7eL_LPBBUlNrUsFedP7eKPdW1uGRrd6i_UmQTDx0tq0cV8NOV-vvQLgKY7GROPjZ1qOx6-3s_oEDL_T65ERFJH4CMcMBOH1HsDf2Ee47pM3-lGlBh7SSLpCVbxpOxAc1O6cULbbbSRuAEyUXuQZroagtqoiiwQ
```

## Migration to NHS Identity

It is expected that in the future the authorisation process will migrate away from HSCD to NHS Identity. Although the process will be bradly the same there are likely to be some differences. These differences and the process for migrating over to NHS Identity will be documented here in due course.
