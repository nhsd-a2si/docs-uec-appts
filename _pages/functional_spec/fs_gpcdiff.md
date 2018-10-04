---
title: Differences from GP Connect
sidebar: overview_sidebar
keywords: specification
permalink: fs_gpcdiff.html
toc: false
folder: functional_spec
---

{% include note-notpublished.html %}



<table border=0 cellpadding=0 cellspacing=0 width=2488 style='border-collapse:
 collapse;table-layout:fixed;width:1868pt'>
 <col width=27 style='mso-width-source:userset;mso-width-alt:768;width:20pt'>
 <col width=225 style='mso-width-source:userset;mso-width-alt:6400;width:169pt'>
 <col width=566 span=2 style='mso-width-source:userset;mso-width-alt:16099;
 width:425pt'>
 <col class=xl65 width=566 style='mso-width-source:userset;mso-width-alt:16099;
 width:425pt'>
 <col width=538 style='mso-width-source:userset;mso-width-alt:15303;width:404pt'>
 <tr height=20 style='height:15.0pt'>
  <td height=20 width=27 style='height:15.0pt;width:20pt'></td>
  <td width=225 style='width:169pt'></td>
  <td width=566 style='width:425pt'></td>
  <td width=566 style='width:425pt'></td>
  <td class=xl65 width=566 style='width:425pt'></td>
  <td width=538 style='width:404pt'></td>
 </tr>
 <tr height=21 style='height:15.75pt'>
  <td height=21 style='height:15.75pt'></td>
  <td class=xl75>Stage</td>
  <td class=xl75 style='border-left:none'>GP Connect</td>
  <td class=xl75 style='border-left:none'>Care Connect</td>
  <td class=xl76 width=566 style='border-left:none;width:425pt'>Difference</td>
  <td class=xl75 style='border-left:none'>Rationale for change</td>
 </tr>
 <tr height=21 style='height:15.75pt'>
  <td height=21 class=xl66 style='height:15.75pt'></td>
  <td class=xl67 style='border-top:none'>Identify Patient</td>
  <td class=xl68 style='border-top:none;border-left:none'>Use PDS to get a
  verified NHS Number DBS?</td>
  <td class=xl68 style='border-top:none;border-left:none'>Use PDS to get a
  verified NHS Number</td>
  <td class=xl68 style='border-top:none;border-left:none'>None</td>
  <td class=xl68 style='border-top:none;border-left:none'>N/A</td>
 </tr>
 <tr height=80 style='height:60.0pt'>
  <td height=80 class=xl66 style='height:60.0pt'></td>
  <td class=xl77 style='border-top:none'>Select service</td>
  <td class=xl79 width=566 style='border-top:none;border-left:none;width:425pt'>Get
  Registered GP Practice from PDS record<br>
    <br>
    Federations something else...</td>
  <td class=xl78 style='border-top:none;border-left:none'>Use DOS to select a
  DOS profile</td>
  <td class=xl79 width=566 style='border-top:none;border-left:none;width:425pt'>In
  GP Connect, this is done as part of the PDS lookup, in Care Connect, it's a
  separate call to the DOS, but one which is MOSTLY already taking place. Some
  change needed to the DOS to return the ASID.</td>
  <td class=xl79 width=538 style='border-top:none;border-left:none;width:404pt'>GP
  Connect is all about booking appointments with a GP Practice, which is a
  known ODS code. We're looking beyond this to services as identified from the
  DOS, or by ASID. These can also be found from SDS using ODS code.</td>
 </tr>
 <tr height=60 style='mso-height-source:userset;height:45.0pt'>
  <td height=60 class=xl66 style='height:45.0pt'></td>
  <td rowspan=7 class=xl67 style='border-top:none'>Calls via SSP</td>
  <td class=xl68 style='border-top:none;border-left:none'>Target URL is
  concatenated onto SSP URL</td>
  <td class=xl68 style='border-top:none;border-left:none'>Target URL is
  concatenated onto SSP URL</td>
  <td class=xl69 width=566 style='border-top:none;border-left:none;width:425pt'>No
  change</td>
  <td rowspan=7 class=xl69 width=538 style='border-top:none;width:404pt'>The
  Interaction IDs are different to allow them to be individually authorised,
  and to permit different endpoints to be offered per interaction. If there
  were no differences elsewhere they COULD be the same.<br>
    <br>
    SSP Could inspect the Authorization header and make decisions based on that
  (not currently in scope).</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl66 style='height:15.0pt'></td>
  <td class=xl68 style='border-top:none;border-left:none'>http headers are as
  follows</td>
  <td class=xl68 style='border-top:none;border-left:none'>http headers are as
  follows</td>
  <td class=xl69 width=566 style='border-top:none;border-left:none;width:425pt'>Interaction
  IDs are different</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl66 style='height:15.0pt'></td>
  <td class=xl70 style='border-top:none;border-left:none'>Ssp-TraceID</td>
  <td class=xl70 style='border-top:none;border-left:none'>Ssp-TraceID = a UUID</td>
  <td class=xl71 width=566 style='border-top:none;border-left:none;width:425pt'>No
  change</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl66 style='height:15.0pt'></td>
  <td class=xl70 style='border-top:none;border-left:none'>Ssp-From</td>
  <td class=xl70 style='border-top:none;border-left:none'>Ssp-From = Client
  system ASID</td>
  <td class=xl71 width=566 style='border-top:none;border-left:none;width:425pt'>No
  change</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl66 style='height:15.0pt'></td>
  <td class=xl70 style='border-top:none;border-left:none'>Ssp-To</td>
  <td class=xl70 style='border-top:none;border-left:none'>Ssp-To = Server ASID</td>
  <td class=xl71 width=566 style='border-top:none;border-left:none;width:425pt'>No
  change</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl66 style='height:15.0pt'></td>
  <td class=xl70 style='border-top:none;border-left:none'>Ssp-InteractionID</td>
  <td class=xl70 style='border-top:none;border-left:none'>Ssp-InteractionID =
  Interaction ID from SDS specific to the call being made.</td>
  <td class=xl71 width=566 style='border-top:none;border-left:none;width:425pt'>Specific
  set for GP Connect, and another for Care Connect</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl66 style='height:15.0pt'></td>
  <td class=xl89 style='border-left:none'>N/A</td>
  <td class=xl89 style='border-left:none'>Authorization</td>
  <td class=xl71 width=566 style='border-top:none;border-left:none;width:425pt'>Uses
  a JWT token in an Authorization http header (not used by SSP)</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl66 style='height:15.0pt'></td>
  <td rowspan=2 class=xl77 style='border-top:none'>TLS/MA</td>
  <td rowspan=2 class=xl78>Spine issued digital certificate required to talk to
  PDS, SDS and SSP</td>
  <td rowspan=2 class=xl78>Spine issued digital certificate required to talk to
  PDS, SDS and SSP</td>
  <td class=xl79 width=566 style='border-top:none;border-left:none;width:425pt'>No
  change</td>
  <td rowspan=2 class=xl78 style='border-top:none'>N/A</td>
 </tr>
 <tr height=34 style='height:25.5pt'>
  <td height=34 class=xl66 style='height:25.5pt'></td>
  <td class=xl80 width=566 style='border-top:none;border-left:none;width:425pt'>If
  client is <font class="font11">only </font><font class="font7">assured for
  appointment booking, a certificate with a specific prefix will be issued, to
  prevent it being used to do anything else.</font></td>
 </tr>
 <tr height=40 style='mso-height-source:userset;height:30.0pt'>
  <td height=40 class=xl66 style='height:30.0pt'></td>
  <td rowspan=3 class=xl67 style='border-top:none'>SSP authorisation</td>
  <td class=xl68 style='border-top:none;border-left:none'>Uses the following</td>
  <td class=xl68 style='border-top:none;border-left:none'>Uses the following</td>
  <td class=xl69 width=566 style='border-top:none;border-left:none;width:425pt'>No
  Data Sharing Agreement required</td>
  <td rowspan=3 class=xl69 width=538 style='border-top:none;width:404pt'>For
  MVP we're not requesting Patient info, hence lower IG concerns. The DSA
  approach doesn't scale for &quot;any to any&quot; as the scope expands.<br>
    <br>
    Could be implemented in Authorization headers rather than config file.</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl66 style='height:15.0pt'></td>
  <td class=xl70 style='border-top:none;border-left:none'>SDS lookup for ASIDs</td>
  <td class=xl70 style='border-top:none;border-left:none'>SDS lookup for ASIDs</td>
  <td class=xl71 width=566 style='border-top:none;border-left:none;width:425pt'>No
  change</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl66 style='height:15.0pt'></td>
  <td class=xl70 style='border-top:none;border-left:none'>Data Sharing
  agreement between Client and Server</td>
  <td class=xl70 style='border-top:none;border-left:none'>N/A</td>
  <td class=xl71 width=566 style='border-top:none;border-left:none;width:425pt'>Not
  required</td>
 </tr>
 <tr height=40 style='mso-height-source:userset;height:30.0pt'>
  <td height=40 class=xl66 style='height:30.0pt'></td>
  <td rowspan=3 class=xl77 style='border-top:none'>Find Patient</td>
  <td class=xl78 style='border-top:none;border-left:none'>FHIR Search operation
  on the endpoint via SSP</td>
  <td rowspan=3 class=xl78 style='border-top:none'>N/A</td>
  <td rowspan=3 class=xl79 width=566 style='border-top:none;width:425pt'>Patient
  find is not used in Care Connect</td>
  <td rowspan=3 class=xl79 width=538 style='border-top:none;width:404pt'>GP
  Connect works on the GP concept of patients being registered in a practice.
  Many other services will not have this concept.</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl66 style='height:15.0pt'></td>
  <td class=xl81 width=566 style='border-top:none;border-left:none;width:425pt'>GET
  https://[proxy_server]/https://[provider_server]/[fhir_base]/Patient?identifier=[system]|[value]</td>
 </tr>
 <tr height=41 style='mso-height-source:userset;height:30.75pt'>
  <td height=41 class=xl66 style='height:30.75pt'></td>
  <td class=xl82 width=566 style='border-top:none;border-left:none;width:425pt'>NB:
  in the above [system] will always be https://fhir.nhs.uk/Id/nhs-number and
  [value] will always be the NHS Number</td>
 </tr>
 <tr height=40 style='height:30.0pt'>
  <td height=40 class=xl66 style='height:30.0pt'></td>
  <td class=xl67 style='border-top:none'>Register Patient</td>
  <td class=xl68 style='border-top:none;border-left:none'>Patient is registered
  if not found.</td>
  <td class=xl68 style='border-top:none;border-left:none'>N/A</td>
  <td class=xl69 width=566 style='border-top:none;border-left:none;width:425pt'>Register
  Patient is not done in Care Connect</td>
  <td class=xl69 width=538 style='border-top:none;border-left:none;width:404pt'>If
  the service requires a patient to be registered, it can perform this within
  the atomic booking process, rather than have a separate routine.</td>
 </tr>
 <tr height=60 style='mso-height-source:userset;height:45.0pt'>
  <td height=60 style='height:45.0pt'></td>
  <td rowspan=7 class=xl77 style='border-top:none'>Find Endpoint</td>
  <td class=xl78 style='border-top:none;border-left:none'>Use SDS to get
  endpoint from nhsMHS object</td>
  <td class=xl78 style='border-top:none;border-left:none'>Use SDS to get
  endpoint from nhsMHS object</td>
  <td class=xl79 width=566 style='border-top:none;border-left:none;width:425pt'>Different
  LDAP searches</td>
  <td rowspan=7 class=xl79 width=538 style='border-top:none;width:404pt'>Knowing
  the ASID allows a simpler and faster / more efficient LDAP query, it also
  supports a more granular approach than ODS codes alone, including one server
  endpoint for multiple DOS profiles.</td>
 </tr>
 <tr height=45 style='height:33.75pt'>
  <td height=45 style='height:33.75pt'></td>
  <td class=xl83 width=566 style='border-top:none;border-left:none;width:425pt'>ldapsearch
  -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk –b &quot;ou=services,
  o=nhs&quot; &quot;(&amp;(nhsIDCode=<font class="font9">T99999</font><font
  class="font8">) (objectClass=nhsAS)(nhsAsSvcIA=</font><font class="font9">urn:nhs:names:services:gpconnect:fhir:rest:search:slot-1</font><font
  class="font8">))&quot; uniqueIdentifier nhsMhsPartyKey</font></td>
  <td class=xl83 width=566 style='border-top:none;border-left:none;width:425pt'>ldapsearch
  -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk –b &quot;ou=services,
  o=nhs&quot; &quot;(&amp;(uniqueIdentifier=<font class="font9">ABC123</font><font
  class="font8">) (objectClass=nhsAS)(nhsAsSvcIA=</font><font class="font9">urn:nhs:names:services:a2si:fhir:rest:search:slot</font><font
  class="font8">))&quot; nhsMhsPartyKey</font></td>
  <td rowspan=3 class=xl80 width=566 style='border-top:none;width:425pt'>LDAP
  search is based on ODS code for GP Connect, ASID for Care Connect.<br>
    Interaction name is different.</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl78 style='border-top:none;border-left:none'><font class="font5">T99999</font><font
  class="font0"> = ODS Code of the GP Practice</font></td>
  <td class=xl78 style='border-top:none;border-left:none'><font class="font5">ABC123</font><font
  class="font0"> = ASID of the service as returned from DOS</font></td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl78 style='border-top:none;border-left:none'><font class="font5">gpconnect:fhir:rest:search:slot-1</font><font
  class="font0"> is the Interaction being performed</font></td>
  <td class=xl78 style='border-top:none;border-left:none'><font class="font5">a2si:fhir:rest:search:slot</font><font
  class="font0"> is the Interaction being performed</font></td>
 </tr>
 <tr height=45 style='height:33.75pt'>
  <td height=45 style='height:33.75pt'></td>
  <td class=xl83 width=566 style='border-top:none;border-left:none;width:425pt'>ldapsearch
  -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk -b &quot;ou=services,
  o=nhs&quot; &quot;(&amp;(nhsMhsPartyKey=<font class="font9">T99999-9999999</font><font
  class="font8">) (objectClass=nhsMhs) (nhsMhsSvcIA=</font><font class="font9">urn:nhs:names:services:gpconnect:fhir:rest:search:slot-1</font><font
  class="font8">))&quot; nhsMhsEndPoint nhsMHSFQDN</font></td>
  <td class=xl83 width=566 style='border-top:none;border-left:none;width:425pt'>ldapsearch
  -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk -b &quot;ou=services,
  o=nhs&quot; &quot;(&amp;(nhsMhsPartyKey=<font class="font9">T99999-9999999</font><font
  class="font8">) (objectClass=nhsMhs) (nhsMhsSvcIA=</font><font class="font9">urn:nhs:names:services:a2si:fhir:rest:search:slot</font><font
  class="font8">))&quot; nhsMhsEndPoint nhsMHSFQDN</font></td>
  <td rowspan=3 class=xl80 width=566 style='border-top:none;width:425pt'>Search
  is identical apart from the Interaction ID being specific.</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl78 style='border-top:none;border-left:none'><font class="font5">T99999-9999999</font><font
  class="font0"> is the partyKey from previous step</font></td>
  <td class=xl78 style='border-top:none;border-left:none'><font class="font5">T99999-9999999</font><font
  class="font0"> is the partyKey from previous step</font></td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl78 style='border-top:none;border-left:none'><font class="font5">…:gpconnect:fhir:rest:search:slot-1</font><font
  class="font0"> is the Interaction being performed</font></td>
  <td class=xl78 style='border-top:none;border-left:none'><font class="font5">…:a2si:fhir:rest:search:slot</font><font
  class="font0"> is the Interaction being performed</font></td>
 </tr>
 <tr height=40 style='mso-height-source:userset;height:30.0pt'>
  <td height=40 style='height:30.0pt'></td>
  <td rowspan=2 class=xl67 style='border-top:none'>Get free slots</td>
  <td class=xl68 style='border-top:none;border-left:none'>FHIR Search operation
  on the endpoint via SSP</td>
  <td class=xl68 style='border-top:none;border-left:none'>FHIR Search operation
  on the endpoint via SSP</td>
  <td rowspan=2 class=xl69 width=566 style='border-top:none;width:425pt'>No
  searchFilter parameter used in Care Connect, see below for more details. Also
  resource profiles are different.</td>
  <td rowspan=2 class=xl69 width=538 style='border-top:none;width:404pt'>searchFilter
  is open to abuse., and not neeed if we use JWT (below).</td>
 </tr>
 <tr height=75 style='height:56.25pt'>
  <td height=75 style='height:56.25pt'></td>
  <td class=xl72 width=566 style='border-top:none;border-left:none;width:425pt'>GET
  https://[proxy_server]/https://[provider_server]/[fhir_base]/Slot?[start={search_prefix}start_date][&amp;end=[{search_prefix}end_date][&amp;status=free][&amp;_include=Slot:schedule]{&amp;_include:recurse=Schedule:actor:Practitioner}{&amp;_include:recurse=Schedule:actor:Location}{&amp;searchFilter={OrgTypeSystem}|{OrgTypeValue}}{&amp;searchFilter={OrgODSCodeSystem}|{OrgODSCode}}</td>
  <td class=xl72 width=566 style='border-top:none;border-left:none;width:425pt'>GET
  https://[proxy_server]/https://[provider_server]/[fhir_base]/Slot?[start={search_prefix}start_date][&amp;end=[{search_prefix}end_date][&amp;status=free][&amp;_include=Slot:schedule]{&amp;_include:recurse=Schedule:actor:Practitioner}{&amp;_include:recurse=Schedule:actor:Location}</td>
 </tr>
 <tr height=100 style='mso-height-source:userset;height:75.0pt'>
  <td height=100 style='height:75.0pt'></td>
  <td rowspan=2 class=xl77 style='border-top:none'>Identify requester</td>
  <td class=xl78 style='border-top:none;border-left:none'>searchFilter
  parameter</td>
  <td class=xl78 style='border-top:none;border-left:none'>JWT</td>
  <td class=xl79 width=566 style='border-top:none;border-left:none;width:425pt'>GP
  Connect expects an assertion of the type of organisation making the request
  and their ODS Code in a searchFilter querystring parameter. Care Connect
  expects to get this information from a signed JWT issued by Strat Auth.</td>
  <td rowspan=2 class=xl79 width=538 style='border-top:none;width:404pt'>This
  is a combination of authentication (who is the client) and authorisation
  (what can they do) and therefore should be handled as such. Implementing this
  removes the need for searchFilter. Using a signed JWT gives the server
  significant confidence in the identity of the client, which should help to
  reduce IG challenges.</td>
 </tr>
 <tr height=75 style='height:56.25pt'>
  <td height=75 style='height:56.25pt'></td>
  <td class=xl83 width=566 style='border-top:none;border-left:none;width:425pt'>GET
  https://[proxy_server]/https://[provider_server]/[fhir_base]/Slot?[start={search_prefix}start_date][&amp;end=[{search_prefix}end_date][&amp;status=free][&amp;_include=Slot:schedule]{&amp;_include:recurse=Schedule:actor:Practitioner}{&amp;_include:recurse=Schedule:actor:Location}<font
  class="font9">{&amp;searchFilter={OrgTypeSystem}|{OrgTypeValue}}{&amp;searchFilter={OrgODSCodeSystem}|{OrgODSCode}}</font></td>
  <td class=xl84 width=566 style='border-top:none;border-left:none;width:425pt'><font
  class="font13">See:
  https://developer.nhs.uk/apis/spine-core/security_jwt.html<br>
    </font><font class="font12">ToDo: Provide a sample JWT</font></td>
  <td class=xl79 width=566 style='border-top:none;border-left:none;width:425pt'>JWT
  can be verified by checking signature.</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td rowspan=2 class=xl67 style='border-top:none'>Book an appointment</td>
  <td class=xl68 style='border-top:none;border-left:none'>FHIR Create operation
  on the endpoint via SSP</td>
  <td class=xl68 style='border-top:none;border-left:none'>FHIR Create operation
  on the endpoint via SSP</td>
  <td rowspan=2 class=xl69 width=566 style='border-top:none;width:425pt'>Resources
  are (will be) different.</td>
  <td rowspan=2 class=xl90 style='border-top:none'>See FHIR Resource rationale.</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl73 width=566 style='border-top:none;border-left:none;width:425pt'>POST
  https://[proxy_server]/https://[provider_server]/[fhir_base]/Appointment</td>
  <td class=xl73 width=566 style='border-top:none;border-left:none;width:425pt'>POST
  https://[proxy_server]/https://[provider_server]/[fhir_base]/Appointment</td>
 </tr>
 <tr height=60 style='height:45.0pt'>
  <td height=60 style='height:45.0pt'></td>
  <td class=xl77 style='border-top:none'>FHIR Resource profiles</td>
  <td class=xl78 style='border-top:none;border-left:none'>GP Connect specific
  ones</td>
  <td class=xl78 style='border-top:none;border-left:none'>Care Connect Generic
  where possible</td>
  <td rowspan=9 class=xl79 width=566 style='border-top:none;width:425pt'>Resources
  are still based on FHIR STU3 but are (or will be) different.</td>
  <td class=xl79 width=538 style='border-top:none;border-left:none;width:404pt'>GP
  Connect resources are by definition (it's part of their name) for GP Connect.
  Where possible we try to use generic resources. Each has been profiled to
  include the necessary information.</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl78 style='border-top:none'>Slot Profile</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.nhs.uk/STU3/StructureDefinition/GPConnect-Slot-1</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-Slot-1</td>
  <td class=xl86 style='border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl78 style='border-top:none'>Appointment Profile</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.nhs.uk/STU3/StructureDefinition/GPConnect-Appointment-1</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-Appointment-1</td>
  <td class=xl86 style='border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl78 style='border-top:none'>Patient Profile</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Patient-1</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1</td>
  <td class=xl86 style='border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl78 style='border-top:none'>LocationProfile</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Location-1</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1</td>
  <td class=xl86 style='border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl87 style='border-top:none'>Practitioner Profile</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Practitioner-1</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1</td>
  <td class=xl86 style='border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=21 style='height:15.75pt'>
  <td height=21 style='height:15.75pt'></td>
  <td class=xl87 style='border-top:none'>Schedule profile</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.nhs.uk/STU3/StructureDefinition/GPConnect-Schedule-1</td>
  <td class=xl88 style='border-top:none;border-left:none'>TBC</td>
  <td class=xl86 style='border-top:none;border-left:none'>&nbsp;</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl87 style='border-top:none'>PractitionerRole Profile</td>
  <td class=xl85 style='border-top:none;border-left:none'>N/A</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1</td>
  <td class=xl86 style='border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl87 style='border-top:none'>Organisation profile</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Organization-1</td>
  <td class=xl85 style='border-top:none;border-left:none'>https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1</td>
  <td class=xl86 style='border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td rowspan=2 class=xl91 style='border-top:none'>Search for appointments</td>
  <td class=xl78 style='border-top:none;border-left:none'>Described</td>
  <td rowspan=2 class=xl68 style='border-top:none'>Out of current scope</td>
  <td rowspan=2 class=xl69 width=566 style='border-top:none;width:425pt'>Not in
  scope for Care Connect</td>
  <td rowspan=2 class=xl93 style='border-top:none'>Not in current scope. IG
  concerns are higher, so excluded from MVP.</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl85 style='border-top:none;border-left:none'><a
  href="https://nhsconnect.github.io/gpconnect/appointments_use_case_retrieve_a_patients_appointments.html"
  target="_parent"><span style='color:black;font-size:8.0pt;text-decoration:
  none'>https://nhsconnect.github.io/gpconnect/appointments_use_case_retrieve_a_patients_appointments.html</span></a></td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td rowspan=2 class=xl92 style='border-top:none'>Cancel Appointment</td>
  <td class=xl78 style='border-top:none;border-left:none'>Described</td>
  <td rowspan=2 class=xl78 style='border-top:none'>Out of current scope</td>
  <td rowspan=2 class=xl79 width=566 style='border-top:none;width:425pt'>Not in
  scope for Care Connect</td>
  <td rowspan=2 class=xl94 style='border-top:none'>Not in current scope. IG
  concerns are higher, so excluded from MVP.</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl85 style='border-top:none;border-left:none'>https://nhsconnect.github.io/gpconnect/appointments_use_case_cancel_an_appointment.html</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td rowspan=2 class=xl91 style='border-top:none'>Amend Appointment</td>
  <td class=xl68 style='border-top:none;border-left:none'>Described</td>
  <td rowspan=2 class=xl68 style='border-top:none'>Out of current scope</td>
  <td rowspan=2 class=xl69 width=566 style='border-top:none;width:425pt'>Not in
  scope for Care Connect</td>
  <td rowspan=2 class=xl93 style='border-top:none'>Not in current scope. IG
  concerns are higher, so excluded from MVP.</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 style='height:15.0pt'></td>
  <td class=xl74 style='border-top:none;border-left:none'>https://nhsconnect.github.io/gpconnect/appointments_use_case_amend_an_appointment.html</td>
 </tr>
 <![if supportMisalignedColumns]>
 <tr height=0 style='display:none'>
  <td width=27 style='width:20pt'></td>
  <td width=225 style='width:169pt'></td>
  <td width=566 style='width:425pt'></td>
  <td width=566 style='width:425pt'></td>
  <td width=566 style='width:425pt'></td>
  <td width=538 style='width:404pt'></td>
 </tr>
 <![endif]>
</table>
