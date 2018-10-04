---
title: Differences from GP Connect
sidebar: overview_sidebar
keywords: specification
permalink: fs_gpcdiff.html
toc: false
folder: functional_spec
---

{% include note-notpublished.html %}

Stage       | GP Connect           | Care Connect            | Difference         | Rational for change
------------|----------------------|-------------------------|--------------------|-------------------
Identify Patient | Use PDS to get a verified NHS Number DBS? | Use PDS to get a verified NHS Number DBS? | None | NA
Select Service | Get Registered GP Practice from PDS record | Use DoS to select a DoS profile | In GP Connect, this is done as part of the PDS lookup, in Care Connect, it's a separate call to the DOS, but one which is MOSTLY already taking place. Some change needed to the DOS to return the ASID. | GP Connect is all about booking appointments with a GP Practice, which is a known ODS code. We're looking beyond this to services as identified from the DOS, or by ASID. These can also be found from SDS using ODS code.



Stage       | GP Connect           | Care Connect            | Difference         | Rational for change
------------|----------------------|-------------------------|--------------------|-------------------
 | Identify Patient | Use PDS to get a verified NHS Number DBS? | Use PDS to get a verified NHS Number | None | N/A
 | Select service | "Get Registered GP Practice from PDS record

Federations something else..." | Use DOS to select a DOS profile | "In GP Connect |  this is done as part of the PDS lookup |  in Care Connect |  it's a separate call to the DOS |  but one which is MOSTLY already taking place. Some change needed to the DOS to return the ASID." | "GP Connect is all about booking appointments with a GP Practice |  which is a known ODS code. We're looking beyond this to services as identified from the DOS |  or by ASID. These can also be found from SDS using ODS code."
 | Calls via SSP | Target URL is concatenated onto SSP URL | Target URL is concatenated onto SSP URL | No change | "The Interaction IDs are different to allow them to be individually authorised |  and to permit different endpoints to be offered per interaction. If there were no differences elsewhere they COULD be the same.

SSP Could inspect the Authorization header and make decisions based on that (not currently in scope)."
 |  | http headers are as follows | http headers are as follows | Interaction IDs are different | 
 |  | Ssp-TraceID | Ssp-TraceID = a UUID | No change | 
 |  | Ssp-From | Ssp-From = Client system ASID | No change | 
 |  | Ssp-To | Ssp-To = Server ASID | No change | 
 |  | Ssp-InteractionID | Ssp-InteractionID = Interaction ID from SDS specific to the call being made. | "Specific set for GP Connect |  and another for Care Connect" | 
 |  | N/A | Authorization | Uses a JWT token in an Authorization http header (not used by SSP) | 
 | TLS/MA | "Spine issued digital certificate required to talk to PDS |  SDS and SSP" | "Spine issued digital certificate required to talk to PDS |  SDS and SSP" | No change | N/A
 |  |  |  | "If client is only assured for appointment booking |  a certificate with a specific prefix will be issued |  to prevent it being used to do anything else." | 
 | SSP authorisation | Uses the following | Uses the following | No Data Sharing Agreement required | "For MVP we're not requesting Patient info |  hence lower IG concerns. The DSA approach doesn't scale for ""any to any"" as the scope expands.

Could be implemented in Authorization headers rather than config file."
 |  | SDS lookup for ASIDs | SDS lookup for ASIDs | No change | 
 |  | Data Sharing agreement between Client and Server | N/A | Not required | 
 | Find Patient | FHIR Search operation on the endpoint via SSP | N/A | Patient find is not used in Care Connect | GP Connect works on the GP concept of patients being registered in a practice. Many other services will not have this concept.
 |  | GET https://[proxy_server]/https://[provider_server]/[fhir_base]/Patient?identifier=[system]|[value] |  |  | 
 |  | NB: in the above [system] will always be https://fhir.nhs.uk/Id/nhs-number and [value] will always be the NHS Number |  |  | 
 | Register Patient | Patient is registered if not found. | N/A | Register Patient is not done in Care Connect | "If the service requires a patient to be registered |  it can perform this within the atomic booking process |  rather than have a separate routine."
 | Find Endpoint | Use SDS to get endpoint from nhsMHS object | Use SDS to get endpoint from nhsMHS object | Different LDAP searches | "Knowing the ASID allows a simpler and faster / more efficient LDAP query |  it also supports a more granular approach than ODS codes alone |  including one server endpoint for multiple DOS profiles."
 |  | "ldapsearch -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk –b ""ou=services |  o=nhs"" ""(&(nhsIDCode=T99999) (objectClass=nhsAS)(nhsAsSvcIA=urn:nhs:names:services:gpconnect:fhir:rest:search:slot-1))"" uniqueIdentifier nhsMhsPartyKey" | "ldapsearch -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk –b ""ou=services |  o=nhs"" ""(&(uniqueIdentifier=ABC123) (objectClass=nhsAS)(nhsAsSvcIA=urn:nhs:names:services:a2si:fhir:rest:search:slot))"" nhsMhsPartyKey" | "LDAP search is based on ODS code for GP Connect |  ASID for Care Connect.
Interaction name is different." | 
 |  | T99999 = ODS Code of the GP Practice | ABC123 = ASID of the service as returned from DOS |  | 
 |  | gpconnect:fhir:rest:search:slot-1 is the Interaction being performed | a2si:fhir:rest:search:slot is the Interaction being performed |  | 
 |  | "ldapsearch -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk -b ""ou=services |  o=nhs"" ""(&(nhsMhsPartyKey=T99999-9999999) (objectClass=nhsMhs) (nhsMhsSvcIA=urn:nhs:names:services:gpconnect:fhir:rest:search:slot-1))"" nhsMhsEndPoint nhsMHSFQDN" | "ldapsearch -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk -b ""ou=services |  o=nhs"" ""(&(nhsMhsPartyKey=T99999-9999999) (objectClass=nhsMhs) (nhsMhsSvcIA=urn:nhs:names:services:a2si:fhir:rest:search:slot))"" nhsMhsEndPoint nhsMHSFQDN" | Search is identical apart from the Interaction ID being specific. | 
 |  | T99999-9999999 is the partyKey from previous step | T99999-9999999 is the partyKey from previous step |  | 
 |  | …:gpconnect:fhir:rest:search:slot-1 is the Interaction being performed | …:a2si:fhir:rest:search:slot is the Interaction being performed |  | 
 | Get free slots | FHIR Search operation on the endpoint via SSP | FHIR Search operation on the endpoint via SSP | "No searchFilter parameter used in Care Connect |  see below for more details. Also resource profiles are different." | "searchFilter is open to abuse. |  and not neeed if we use JWT (below)."
 |  | GET https://[proxy_server]/https://[provider_server]/[fhir_base]/Slot?[start={search_prefix}start_date][&end=[{search_prefix}end_date][&status=free][&_include=Slot:schedule]{&_include:recurse=Schedule:actor:Practitioner}{&_include:recurse=Schedule:actor:Location}{&searchFilter={OrgTypeSystem}|{OrgTypeValue}}{&searchFilter={OrgODSCodeSystem}|{OrgODSCode}} | GET https://[proxy_server]/https://[provider_server]/[fhir_base]/Slot?[start={search_prefix}start_date][&end=[{search_prefix}end_date][&status=free][&_include=Slot:schedule]{&_include:recurse=Schedule:actor:Practitioner}{&_include:recurse=Schedule:actor:Location} |  | 
 | Identify requester | searchFilter parameter | JWT | GP Connect expects an assertion of the type of organisation making the request and their ODS Code in a searchFilter querystring parameter. Care Connect expects to get this information from a signed JWT issued by Strat Auth. | "This is a combination of authentication (who is the client) and authorisation (what can they do) and therefore should be handled as such. Implementing this removes the need for searchFilter. Using a signed JWT gives the server significant confidence in the identity of the client |  which should help to reduce IG challenges."
 |  | GET https://[proxy_server]/https://[provider_server]/[fhir_base]/Slot?[start={search_prefix}start_date][&end=[{search_prefix}end_date][&status=free][&_include=Slot:schedule]{&_include:recurse=Schedule:actor:Practitioner}{&_include:recurse=Schedule:actor:Location}{&searchFilter={OrgTypeSystem}|{OrgTypeValue}}{&searchFilter={OrgODSCodeSystem}|{OrgODSCode}} | "See: https://developer.nhs.uk/apis/spine-core/security_jwt.html
ToDo: Provide a sample JWT" | JWT can be verified by checking signature. | 
 | Book an appointment | FHIR Create operation on the endpoint via SSP | FHIR Create operation on the endpoint via SSP | Resources are (will be) different. | See FHIR Resource rationale.
 |  | POST https://[proxy_server]/https://[provider_server]/[fhir_base]/Appointment | POST https://[proxy_server]/https://[provider_server]/[fhir_base]/Appointment |  | 
 | FHIR Resource profiles | GP Connect specific ones | Care Connect Generic where possible | Resources are still based on FHIR STU3 but are (or will be) different. | GP Connect resources are by definition (it's part of their name) for GP Connect. Where possible we try to use generic resources. Each has been profiled to include the necessary information.
 | Slot Profile | https://fhir.nhs.uk/STU3/StructureDefinition/GPConnect-Slot-1 | https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-Slot-1 |  | Uses standard CareConnect profile
 | Appointment Profile | https://fhir.nhs.uk/STU3/StructureDefinition/GPConnect-Appointment-1 | https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-Appointment-1 |  | Uses standard CareConnect profile
 | Patient Profile | https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Patient-1 | https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1 |  | Uses standard CareConnect profile
 | LocationProfile | https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Location-1 | https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1 |  | Uses standard CareConnect profile
 | Practitioner Profile | https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Practitioner-1 | https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1 |  | Uses standard CareConnect profile
 | Schedule profile | https://fhir.nhs.uk/STU3/StructureDefinition/GPConnect-Schedule-1 | TBC |  | 
 | PractitionerRole Profile | N/A | https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1 |  | Uses standard CareConnect profile
 | Organisation profile | https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Organization-1 | https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1 |  | Uses standard CareConnect profile
 | Search for appointments | Described | Out of current scope | Not in scope for Care Connect | "Not in current scope. IG concerns are higher |  so excluded from MVP."
 |  | https://nhsconnect.github.io/gpconnect/appointments_use_case_retrieve_a_patients_appointments.html |  |  | 
 | Cancel Appointment | Described | Out of current scope | Not in scope for Care Connect | "Not in current scope. IG concerns are higher |  so excluded from MVP."
 |  | https://nhsconnect.github.io/gpconnect/appointments_use_case_cancel_an_appointment.html |  |  | 
 | Amend Appointment | Described | Out of current scope | Not in scope for Care Connect | "Not in current scope. IG concerns are higher |  so excluded from MVP."
 |  | https://nhsconnect.github.io/gpconnect/appointments_use_case_amend_an_appointment.html |  |  | 
