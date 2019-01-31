---
title: Authentication
sidebar: overview_sidebar
keywords: specification
permalink: fs_authentication.html
toc: false
folder: functional_spec
---

{% include note-notpublished.html %}

## Introduction

The main principle in the approach to authentication is to authorise the consumer **system** rather than the user. Therefore there is no dependency on passing through a users strongly authenticated identity and role (such as via a smartcard) to authorise the transaction. This approach will always be the case for viewing and booking slots. There may be a future requirement for more granular authorisation when doing modification and retrieval operations such as third party cancelling and rebooking.

----

In order to allow the Provider to trust requests from Consumer systems, we need to implement support for Authorisation. In the fullness of time, this is expected to be performed by NHS Identity (AKA Strat Auth), however in order to remove a dependency on that programme's delivery timescales, for Beta rollout we will use the Health and Social Care Directory (HSCD) which is already live and supporting NHS Mail identities. In the very early days we are using a temporary Azure AD (which is the what HSCD is based on) account.
-


----






This uses the standard OAuth 2 client_credentials flow (see: https://oauth.net/2/grant-types/client-credentials/ ) , and allows new Consumer and Provider systems to be implemented and removed, with NO effect on other services. It allows central control over authorisation at a capability level (which we can control based on the outcome of Solution Assurance processes). All configuration is controlled centrally in HSCD, and those details are passed to the Provider to allow them to make the required authorisation decisions. In addition to the provider system checking the tokens, the SSP can also validate requests and could potentially block unauthorised requests.

The approach we are taking is as follows:

Create each Consumer and Provider system as an App Registration in Azure AD. This is done at a fine grained detailed level, so if many Provider or Consumer services are being run on one instance of a system, of which many instances have been deployed, the App registration is done at the 'Service' level.

Create two new groups in the HSCD directory (for ease of management, the names of these groups are the same as the SDS Interaction names).

urn:nhs:names:services:careconnect:fhir:rest:read:slot
Membership of this group indicates that the Service, and the Organisation delivering it, and the system being used, and the supplier of that system represented by this App Registration have all been assured (to whatever level is deemed necessary) to be allowed to view slots.
urn:nhs:names:services:careconnect:fhir:rest:create:appointment
Membership of this group indicates that the Service, and the Organisation delivering it, and the system being used, and the supplier of that system represented by this App Registration have all been assured (to whatever level is deemed necessary) to be allowed to book appointments.
Separating these two groups means we have the ability to allow an application to view available slots, but not have the ability to book appointments, for example this might be a dashboard or monitoring application.

We will later have new Groups defined for example: urn:nhs:names:services:careconnect:fhir:rest:delete:appointment



Edit the Manifest of each Provider application to have the value: "groupMembershipClaims": "All"  this means that the provider will receive (in any access_tokens intended for it, issued by HSCD) a list of the groups that a consumer system is a member of.

Assign the Consumer applications to the groups as created above (NB: it's unlikely but possible that a system would ever only be allowed to view Slots) as they progress through solution assurance / onboarding processes.



Create a 'secret' in HSCD for each Consumer system. The secret is the equivalent to a password, and as such it is ESSENTIAL that it is strongly protected by the Consumer system, we MIGHT want to define a set of practices that we expect of them.  We can create a number of secrets (any current one can be used), and should put in place a rotation policy, for example we might rotate secrets each month, having 5 secrets in place at any one time. We might therefore (based on today being January) have secrets named 201811, 201812, 201901, 201902, 201903 to reflect current month plus 2 and minus 2. Rotation of secrets protects us (eventually) against a secret becoming known by someone other than the Consuming system.

OUTSTANDING QUESTION: We need to come up with a rotation policy, a process to automate the generation and rotation of keys and a secure way to distribute those new keys to each Consuming system.

When a Consumer system wants to request Slots or to book an Appointment at a Provider system, it then makes a request to HSCD (or for now to the temporary Azure AD account), for an access token. It includes the secret and the details of the Provider system it's accessing, e.g:


client_id: "id Goes here",
client_secret: "secret goes here",
scope:  [base url of the provider system] + "/.default",
grant_type: "client_credentials"

For example (a form on the Demonstrator allows this to be submitted) these values can be used:

client_id=92d85f9d-0666-49bc-a31c-12b45b04a7de
client_secret=y7rCysA8anvYshLckwwFNs8qnC6JPyCerE7CUAAnGgo=

HSCD will then issue a signed access_ token, containing the groups that the Consumer is a member of, this token is valid (default) for one hour. The response will look similar to this:

{
"token_type": "Bearer",
"expires_in": 3600,
"ext_expires_in": 3600,
"access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6Im5iQ3dXMTF3M1hrQi14VWFYd0tSU0xqTUhHUSIsImtpZCI6Im5iQ3dXMTF3M1hrQi14VWFYd0tSU0xqTUhHUSJ9.eyJhdWQiOiJodHRwOi8vYXBwb2ludG1lbnRzLmRpcmVjdG9yeW9mc2VydmljZXMubmhzLnVrOjQ0My9wb2MiLCJpc3MiOiJodHRwczovL3N0cy53aW5kb3dzLm5ldC9lNTIxMTFjNy00MDQ4LTRmMzQtYWVhOS02MzI2YWZhNDRhOGQvIiwiaWF0IjoxNTQ3MDMyNDU1LCJuYmYiOjE1NDcwMzI0NTUsImV4cCI6MTU0NzAzNjM1NSwiYWlvIjoiNDJSZ1lNZ0tEbFZYMnBIMnE5cFhlamJ6MzVtWkFBPT0iLCJhcHBpZCI6IjkyZDg1ZjlkLTA2NjYtNDliYy1hMzFjLTEyYjQ1YjA0YTdkZSIsImFwcGlkYWNyIjoiMSIsImdyb3VwcyI6WyJhYjQxMmZlOS0zZjY4LTQzNjgtOTgxMC05ZGMyNGQxNjU5YjEiLCJkYWNiODJjNS1hZWE4LTQ1MDktODg3Zi0yODEzMjQwNjJkZmQiLCI1NWRhMWM5YS0yY2ViLTQxYTctOWI3Yy0xYzcwMTVlZDFmZGUiXSwiaWRwIjoiaHR0cHM6Ly9zdHMud2luZG93cy5uZXQvZTUyMTExYzctNDA0OC00ZjM0LWFlYTktNjMyNmFmYTQ0YThkLyIsIm9pZCI6IjU4YjI1Zjk5LWQ0MDQtNDQ4My1hNjBhLTQwNmYxY2MzYzg4NyIsInN1YiI6IjU4YjI1Zjk5LWQ0MDQtNDQ4My1hNjBhLTQwNmYxY2MzYzg4NyIsInRpZCI6ImU1MjExMWM3LTQwNDgtNGYzNC1hZWE5LTYzMjZhZmE0NGE4ZCIsInV0aSI6IlI1S2FEa21Rc0VlTk96d1c3WElUQUEiLCJ2ZXIiOiIxLjAifQ.eVSncRYT138bByvEHa00uQpfuZrLvW0b9NPF9tDsxIckjaxEiOWJz1pYpaEJoZPnSxmJjKZ_v7h-0ea21ApB-9dYRE6OZ9Y12CGbDr4IKIbO2Oh0QulU06BzvDrA9hMbLXV2vG06mIcLBE8BAJbJp8ktF4PZ1vmRXd0jxy1YonEFqO9e5QsUoekw7eL_LPBBUlNrUsFedP7eKPdW1uGRrd6i_UmQTDx0tq0cV8NOV-vvQLgKY7GROPjZ1qOx6-3s_oEDL_T65ERFJH4CMcMBOH1HsDf2Ee47pM3-lGlBh7SSLpCVbxpOxAc1O6cULbbbSRuAEyUXuQZroagtqoiiwQ"
}

The access_token field in that response contains the actual JWT to be used when making requests to the Provider system specified in the request as 'scope'.

This access_token can be decoded using a site such as https://jwt.ms  or https://jwt.io eg to something like:

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

See: https://docs.microsoft.com/en-us/azure/active-directory/develop/access-tokens for more details on the fields in the above.

Because this token is signed, the Provider system can trust that the Consumer really is a member of the specified groups. It can also retrieve the public key from Azure AD and validate that the token hasn't been tampered with. There are standard ways of doing this.



When requests are made to a Provider system, they must include an Authorization http header which takes the form:

Authorization	Bearer +  space +  [access_token value from above ]
For example using the token shown above:

Authorization	Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6Im5iQ3dXMTF3M1hrQi14VWFYd0tSU0xqTUhHUSIsImtpZCI6Im5iQ3dXMTF3M1hrQi14VWFYd0tSU0xqTUhHUSJ9.eyJhdWQiOiJodHRwOi8vYXBwb2ludG1lbnRzLmRpcmVjdG9yeW9mc2VydmljZXMubmhzLnVrOjQ0My9wb2MiLCJpc3MiOiJodHRwczovL3N0cy53aW5kb3dzLm5ldC9lNTIxMTFjNy00MDQ4LTRmMzQtYWVhOS02MzI2YWZhNDRhOGQvIiwiaWF0IjoxNTQ3MDMyNDU1LCJuYmYiOjE1NDcwMzI0NTUsImV4cCI6MTU0NzAzNjM1NSwiYWlvIjoiNDJSZ1lNZ0tEbFZYMnBIMnE5cFhlamJ6MzVtWkFBPT0iLCJhcHBpZCI6IjkyZDg1ZjlkLTA2NjYtNDliYy1hMzFjLTEyYjQ1YjA0YTdkZSIsImFwcGlkYWNyIjoiMSIsImdyb3VwcyI6WyJhYjQxMmZlOS0zZjY4LTQzNjgtOTgxMC05ZGMyNGQxNjU5YjEiLCJkYWNiODJjNS1hZWE4LTQ1MDktODg3Zi0yODEzMjQwNjJkZmQiLCI1NWRhMWM5YS0yY2ViLTQxYTctOWI3Yy0xYzcwMTVlZDFmZGUiXSwiaWRwIjoiaHR0cHM6Ly9zdHMud2luZG93cy5uZXQvZTUyMTExYzctNDA0OC00ZjM0LWFlYTktNjMyNmFmYTQ0YThkLyIsIm9pZCI6IjU4YjI1Zjk5LWQ0MDQtNDQ4My1hNjBhLTQwNmYxY2MzYzg4NyIsInN1YiI6IjU4YjI1Zjk5LWQ0MDQtNDQ4My1hNjBhLTQwNmYxY2MzYzg4NyIsInRpZCI6ImU1MjExMWM3LTQwNDgtNGYzNC1hZWE5LTYzMjZhZmE0NGE4ZCIsInV0aSI6IlI1S2FEa21Rc0VlTk96d1c3WElUQUEiLCJ2ZXIiOiIxLjAifQ.eVSncRYT138bByvEHa00uQpfuZrLvW0b9NPF9tDsxIckjaxEiOWJz1pYpaEJoZPnSxmJjKZ_v7h-0ea21ApB-9dYRE6OZ9Y12CGbDr4IKIbO2Oh0QulU06BzvDrA9hMbLXV2vG06mIcLBE8BAJbJp8ktF4PZ1vmRXd0jxy1YonEFqO9e5QsUoekw7eL_LPBBUlNrUsFedP7eKPdW1uGRrd6i_UmQTDx0tq0cV8NOV-vvQLgKY7GROPjZ1qOx6-3s_oEDL_T65ERFJH4CMcMBOH1HsDf2Ee47pM3-lGlBh7SSLpCVbxpOxAc1O6cULbbbSRuAEyUXuQZroagtqoiiwQ
It is possible for the Provider or SSP to lookup App Registrations and Groups in Azure AD (for example to translate the appid above to a Service name, and the groups to Group names), however this adds some complexity, and is not currently thought to be necessary. The provider would still need to know the name urn:nhs:names:services:careconnect:fhir:rest:create:appointment in advance, it may as well know the ID instead.



It is absolutely possible for the SSP to perform Provider system endpoint lookups in HSCD, however it's almost certain that SDS will continue for the foreseeable future to allow / block the flow of traffic based on Interactions registered against entries in SDS. We may be able to get SSP to inspect the JWT and block unauthorised traffic, but it is highly unlikely that we could get it to ignore SDS and allow traffic based only on the contents of the JWT.

Migration
In order to switch over from our temporary identity provider to HSCD, the expected changes required centrally are:

New App Registration required for each Provider and Consumer.
Issue new client_id to each Consumer and Provider.
Generate new keys for each Consumer.
Issue new keys.
Manage transition, and switch off of old identity provider.
The changes for a Consumer are as follows:

New client_id and client_secret issued and set in application.
The changes for a Provider are:

New Group identifiers to check for in the tokens.


In order to switch over to NHS Identity, the expected changes are similar, unless we converge on the intended approach for authorisation defined at: https://nhsconnect.github.io/FHIR-SpineCore/security_jwt.html   If we do adopt this, then while we're still using the same standards (OAuth and JWT), there would need to be significant changes, for example the permissions would be represented in a token as a Scope, rather than by Group membership.
