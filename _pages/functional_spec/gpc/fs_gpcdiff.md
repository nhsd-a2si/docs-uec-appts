---
title: Differences between GP Connect and CareConnect
sidebar: gpc_sidebar
keywords: specification
permalink: fs_gpcdiff.html
toc: true
folder: functional_spec
---

## Introduction
This page Identifies the key differences between the CareConnect API specification and the GP Connect API specification. It is imprtant to note that the CareConnect standard is under development and some of these items may change so please keep reviewing this page. It is also not comprehensive and only covers the significant changes, there may be some small detail differences that are not documented here.

## Identify Patient

{% include infocard-small.html 
  title1="GP Connect" 
  content1_line1="Use PDS to get a verified NHS Number" 
  content1_line2="" 
  content1_line3=""  
  content1_line4="" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="Use PDS to get a verified NHS Number" 
  content2_line2="" 
  content2_line3=""  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="No Change" 
  content3_line2="" 
  content3_line3=""  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="NA" 
  content4_line2="" 
  content4_line3=""  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## Select Service

{% include infocard-medium.html 
  title1="GP Connect" 
  content1_line1="Get Registered GP Practice from PDS record" 
  content1_line2="" 
  content1_line3=""  
  content1_line4="" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="Use DoS to select a DoS profile" 
  content2_line2="" 
  content2_line3=""  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="In GP Connect, this is done as part of the PDS lookup, in Care Connect, it is a separate call to the DoS, but one which is MOSTLY already taking place." 
  content3_line2="" 
  content3_line3="Some change needed to the DoS to return the ASID."  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="GP Connect is all about booking appointments with a GP Practice, which is a known ODS code." 
  content4_line2="" 
  content4_line3="CareConnect is looking beyond this to services as identified from the DoS, or by ASID."  
  content4_line4="These can also be found from SDS using ODS code." 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## Calls via SSP

{% include infocard-large.html 
  title1="GP Connect" 
  content1_line1="Target URL is concatenated onto SSP URL" 
  content1_line2="http headers are as follows:" 
  content1_line3="<i>Ssp-TraceID</i>"  
  content1_line4="<i>Ssp-From</i>" 
  content1_line5="<i>Ssp-To</i>" 
  content1_line6="<i>Ssp-InteractionID</i>" 
  content1_line7="<i><i>Authorization</i></i>" 
  
  title2="CareConnect" 
  content2_line1="Target URL is concatenated onto SSP URL" 
  content2_line2="http headers are as follows:" 
  content2_line3="<i>Ssp-TraceID = a UUID</i>"  
  content2_line4="<i>Ssp-From = Client system ASID</i>" 
  content2_line5="<i>Ssp-To = Server ASID</i>" 
  content2_line6="<i>Ssp-InteractionID = Interaction ID from SDS specific to the call being made.</i>" 
  content2_line7="<i>Authorization</i>" 
  
  title3="Difference" 
  content3_line1="Calls via SSP: No change" 
  content3_line2="Interaction ID's are different in http headers" 
  content3_line3="<i>Ssp-TraceID: no change</i>"  
  content3_line4="<i>Ssp-From: no change</i>" 
  content3_line5="<i>Ssp-To: no change</i>" 
  content3_line6="<i>Ssp-InteractionID: specific set for GP Connect and another for CareConnect</i>" 
  content3_line7="<i>Authorization</i>: Both uses JWT token in an Authorisation http header (not used by SSP) however CareConnect token is signed and is issued by an auth server. GPC is unsigned and created by the consumer system. Care connect includes Group values which represent groups. GPC has a set of claims." 
  
  title4="Rationale for change" 
  content4_line1="Target URL is concatenated onto SSP URL" 
  content4_line2="The Interaction IDs are different to allow them to be individually authorised, and to permit different endpoints to be offered per interaction. If there were no differences elsewhere they COULD be the same." 
  content4_line3=""  
  content4_line4="" 
  content4_line5="SSP Could inspect the Authorization header and make decisions based on that (not currently in scope)." 
  content4_line6="" 
  content4_line7="" 
%}

## TLS/MA

{% include infocard-small.html 
  title1="GP Connect" 
  content1_line1="Spine issued digital certificate required to talk to PDS, SDS and SSP" 
  content1_line2="" 
  content1_line3=""  
  content1_line4="" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="Spine issued digital certificate required to talk to PDS, SDS and SSP" 
  content2_line2="" 
  content2_line3=""  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="No change" 
  content3_line2="" 
  content3_line3="If the client is only assured for appointment booking, a certificate with a specific prefix will be issued, to prevent it being used to do anything else."  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="NA" 
  content4_line2="" 
  content4_line3=""  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## SSP authorisation

{% include infocard-medium.html 
  title1="GP Connect" 
  content1_line1="Uses the following:" 
  content1_line2="" 
  content1_line3="<i>SDS lookup for ASIDs</i>"  
  content1_line4="<i>Data Sharing agreement between Client and Server</i>" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="Uses the following:" 
  content2_line2="" 
  content2_line3="<i>SDS lookup for ASIDs</i>"  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="No Data Sharing Agreement required for CareConnect" 
  content3_line2="" 
  content3_line3=""  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="For MVP CareConnect is not requesting Patient info, hence lower IG concerns. The DSA approach doesn't scale for any-to-any booking as the scope expands." 
  content4_line2="" 
  content4_line3="Could be implemented in Authorization headers rather than config file."  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## Find Patient

{% include infocard-medium.html 
  title1="GP Connect" 
  content1_line1="FHIR Search operation on the endpoint via SSP" 
  content1_line2="" 
  content1_line3="<i>GET https://[proxy_server]/https://[provider_server]/[fhir_base]/Patient?identifier=[system]|[value]</i>"  
  content1_line4="<i>NB: in the above [system] will always be https://fhir.nhs.uk/Id/nhs-number and [value] will always be the NHS Number</i>" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="Not used" 
  content2_line2="" 
  content2_line3=""  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="Patient find is not used in Care Connect" 
  content3_line2="" 
  content3_line3=""  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="GP Connect works on the GP concept of patients being registered in a practice. Many other services will not have this concept." 
  content4_line2="" 
  content4_line3=""  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## Register Patient

{% include infocard-small.html 
  title1="GP Connect" 
  content1_line1="Patient is registered if not found." 
  content1_line2="" 
  content1_line3=""  
  content1_line4="" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="Not used" 
  content2_line2="" 
  content2_line3=""  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="Register Patient is not done in Care Connect" 
  content3_line2="" 
  content3_line3=""  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="If the service requires a patient to be registered, it can perform this within the atomic booking process, rather than have a separate routine." 
  content4_line2="" 
  content4_line3=""  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## Find Endpoint

{% include infocard-large.html 
  title1="GP Connect" 
  content1_line1="Use SDS to get endpoint from nhsMHS object" 
  content1_line2="<i>ldapsearch -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk –b &quot;ou=services, o=nhs&quot; &quot;(&(nhsIDCode=<mark>T99999</mark>) (objectClass=nhsAS)(nhsAsSvcIA=<mark>urn:nhs:names:services:gpconnect:fhir:rest:search:slot-1</mark>))&quot; uniqueIdentifier nhsMhsPartyKey</i>" 
  content1_line3="<i><mark>T99999</mark> = ODS Code of the GP Practice</i>"  
  content1_line4="<i><mark>gpconnect:fhir:rest:search:slot-1</mark> is the Interaction being performed</i>" 
  content1_line5="<i>ldapsearch -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk -b &quot;ou=services, o=nhs&quot; &quot;(&(nhsMhsPartyKey=<mark>T99999-9999999</mark>) (objectClass=nhsMhs) (nhsMhsSvcIA=<mark>urn:nhs:names:services:gpconnect:fhir:rest:search:slot-1</mark>))&quot; nhsMhsEndPoint nhsMHSFQDN</i>" 
  content1_line6="<i><mark>T99999-9999999</mark> is the partyKey from previous step</i>" 
  content1_line7="<i><mark>…:gpconnect:fhir:rest:search:slot-1</mark> is the Interaction being performed</i>" 
  
  title2="CareConnect" 
  content2_line1="Use SDS to get endpoint from nhsMHS object" 
  content2_line2="<i>ldapsearch -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk –b &quot;ou=services, o=nhs&quot; &quot;(&(uniqueIdentifier=<mark>ABC123</mark>) (objectClass=nhsAS)(nhsAsSvcIA=<mark>urn:nhs:names:services:a2si:fhir:rest:search:slot</mark>))&quot; nhsMhsPartyKey</i>" 
  content2_line3="<i><mark>ABC123</mark> = ASID of the service as returned from DOS</i>"  
  content2_line4="<i><mark>a2si:fhir:rest:search:slot</mark> is the Interaction being performed</i>" 
  content2_line5="<i>ldapsearch -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk -b &quot;ou=services, o=nhs&quot; &quot;(&(nhsMhsPartyKey=<mark>T99999-9999999</mark>) (objectClass=nhsMhs) (nhsMhsSvcIA=<mark>urn:nhs:names:services:a2si:fhir:rest:search:slot</mark>))&quot; nhsMhsEndPoint nhsMHSFQDN</i>" 
  content2_line6="<i><mark>T99999-9999999</mark> is the partyKey from previous step</i>" 
  content2_line7="<i><mark>…:a2si:fhir:rest:search:slot</mark> is the Interaction being performed</i>" 
  
  title3="Difference" 
  content3_line1="Different LDAP searches" 
  content3_line2="" 
  content3_line3="LDAP search is based on ODS code for GP Connect, ASID for Care Connect.
Interaction name is different."  
  content3_line4="The search is identical apart from the Interaction ID being specific." 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="Knowing the ASID allows a simpler and faster / more efficient LDAP query, it also supports a more granular approach than ODS codes alone, including one server endpoint for multiple DOS profiles." 
  content4_line2="" 
  content4_line3=""  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## Get free slots

{% include infocard-medium.html 
  title1="GP Connect" 
  content1_line1="FHIR Search operation on the endpoint via SSP" 
  content1_line2="<i>GET https://[proxy_server]/https://[provider_server]/[fhir_base]/Slot?[start={search_prefix}start_date][&end=[{search_prefix}end_date][&status=free][&_include=Slot:schedule]{&_include:recurse=Schedule:actor:Practitioner}{&_include:recurse=Schedule:actor:Location}{&searchFilter={OrgTypeSystem}|{OrgTypeValue}}{&searchFilter={OrgODSCodeSystem}|{OrgODSCode}}</i>" 
  content1_line3=""  
  content1_line4="" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="FHIR Search operation on the endpoint via SSP" 
  content2_line2="<i>GET https://[proxy_server]/https://[provider_server]/[fhir_base]/Slot?[start={search_prefix}start_date][&end=[{search_prefix}end_date][&status=free][&_schedule.actor:healthcareservice=xxxxx][&_include=Slot:schedule]{&_include:recurse=Schedule:actor:Practitioner}{&_include:recurse=Schedule:actor:Location}</i>" 
  content2_line3=""  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="No searchFilter parameter used in Care Connect, see below for more details." 
  content3_line2="Also resource profiles are different." 
  content3_line3=""  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="SearchFilter is open to abuse and not needed if we use JWT (below)." 
  content4_line2="" 
  content4_line3=""  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## Identify Requestor

{% include infocard-medium.html 
  title1="GP Connect" 
  content1_line1="searchFilter parameter" 
  content1_line2="<i>GET https://[proxy_server]/https://[provider_server]/[fhir_base]/Slot?[start={search_prefix}start_date][&end=[{search_prefix}end_date][&status=free][&_include=Slot:schedule]{&_include:recurse=Schedule:actor:Practitioner}{&_include:recurse=Schedule:actor:Location}<mark>{&searchFilter={OrgTypeSystem}|{OrgTypeValue}}{&searchFilter={OrgODSCodeSystem}|{OrgODSCode}}</mark></i>" 
  content1_line3=""  
  content1_line4="" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="JWT" 
  content2_line2="See: https://developer.nhs.uk/apis/spine-core/security_jwt.html for example specification (although this is not currently implemented in a complete way and a CareConnect authorisation service is likely to deviate to some extent." 
  content2_line3=""  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="GP Connect expects an assertion of the type of organisation making the request and their ODS Code in a searchFilter querystring parameter." 
  content3_line2="Care Connect expects to get this information from a signed JWT issued by an authentication service." 
  content3_line3=""  
  content3_line4="JWT can be verified by checking signature." 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="This is a combination of authentication (who is the client) and authorisation (what can they do) and therefore should be handled as such. Implementing this removes the need for searchFilter." 
  content4_line2="" 
  content4_line3="Using a signed JWT gives the server significant confidence in the identity of the client, which should help to reduce IG challenges."  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## Book an Appointment

{% include infocard-small.html 
  title1="GP Connect" 
  content1_line1="FHIR Create operation on the endpoint via SSP" 
  content1_line2="<i>POST https://[proxy_server]/https://[provider_server]/[fhir_base]/Appointment</i>" 
  content1_line3=""  
  content1_line4="" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="FHIR Create operation on the endpoint via SSP" 
  content2_line2="<i>POST https://[proxy_server]/https://[provider_server]/[fhir_base]/Appointment</i>" 
  content2_line3=""  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="Resources are (will be) different." 
  content3_line2="" 
  content3_line3=""  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="See FHIR Resource rationale." 
  content4_line2="" 
  content4_line3=""  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## FHIR Resource Profiles

{% include infocard-large.html 
  title1="GP Connect" 
  content1_line1="GP Connect has specific profiles" 
  content1_line2="Slot Profile: <i>https://fhir.nhs.uk/STU3/StructureDefinition/GPConnect-Slot-1</i>" 
  content1_line3="Appointment Profile: <i>https://fhir.nhs.uk/STU3/StructureDefinition/GPConnect-Appointment-1</i>"  
  content1_line4="Patient Profile: <i>https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Patient-1</i>" 
  content1_line5="Location Profile: <i>https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Location-1</i>" 
  content1_line6="Practitioner Profile: <i>https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Practitioner-1</i>" 
  content1_line7="Schedule Profile: <i>https://fhir.nhs.uk/STU3/StructureDefinition/GPConnect-Schedule-1</i>"
  content1_line8="PractitionerRole Profile: <i>N/A</i>" 
  content1_line9="Organisation Profile: <i>https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Organization-1</i>" 
  
  title2="CareConnect" 
  content2_line1="Care Connect has Generic profiles where possible" 
  content2_line2="Slot Profile: <i>https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-Slot-1</i>" 
  content2_line3="Appointment Profile: <i>https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-Appointment-1</i>"  
  content2_line4="Patient Profile: <i>https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1</i>" 
  content2_line5="Location Profile: <i>https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1</i>" 
  content2_line6="Practitioner Profile: <i>https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1</i>" 
  content2_line7="Schedule Profile: <i>TBC</i>"
  content2_line8="PractitionerRole Profile: <i>https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1</i>" 
  content2_line9="Organisation Profile: <i>https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1</i>"
  
  title3="Difference" 
  content3_line1="Resources are still based on FHIR STU3 but are (or will be) different." 
  content3_line2="" 
  content3_line3=""  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="GP Connect resources are by definition (it's part of their name) for GP Connect. Where possible CareConnect tries to use generic resources. Each has been profiled to include the necessary information." 
  content4_line2="" 
  content4_line3=""  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## Search for booked Appointments

{% include infocard-small.html 
  title1="GP Connect" 
  content1_line1="Described" 
  content1_line2="<i>https://nhsconnect.github.io/gpconnect/ appointments_use_case_retrieve_a_patients_appointments.html</i>" 
  content1_line3=""  
  content1_line4="" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="Emerging Capability" 
  content2_line2="" 
  content2_line3=""  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="Emerging capability for CareConnect and currently not described" 
  content3_line2="" 
  content3_line3=""  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="IG concerns are higher, so excluded from MVP." 
  content4_line2="" 
  content4_line3=""  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## Cancel Appointment

{% include infocard-small.html 
  title1="GP Connect" 
  content1_line1="Described" 
  content1_line2="<i>https://nhsconnect.github.io/gpconnect/ appointments_use_case_cancel_an_appointment.html</i>" 
  content1_line3=""  
  content1_line4="" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="Emerging Capability" 
  content2_line2="" 
  content2_line3=""  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="Emerging capability for CareConnect and currently not described" 
  content3_line2="" 
  content3_line3=""  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="IG concerns are higher, so excluded from MVP." 
  content4_line2="" 
  content4_line3=""  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## Amend Appointment

{% include infocard-small.html 
  title1="GP Connect" 
  content1_line1="Described" 
  content1_line2="<i>https://nhsconnect.github.io/gpconnect/ appointments_use_case_amend_an_appointment.html</i>" 
  content1_line3=""  
  content1_line4="" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="Emerging Capability" 
  content2_line2="" 
  content2_line3=""  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="Emerging capability for CareConnect and currently not described" 
  content3_line2="" 
  content3_line3=""  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="IG concerns are higher, so excluded from MVP." 
  content4_line2="" 
  content4_line3=""  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}
