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




<table border=3D0 cellpadding=3D0 cellspacing=3D0 width=3D2488 style=3D'bor=
der-collapse:
 collapse;table-layout:fixed;width:1868pt'>
 <col width=3D27 style=3D'mso-width-source:userset;mso-width-alt:768;width:=
20pt'>
 <col width=3D225 style=3D'mso-width-source:userset;mso-width-alt:6400;widt=
h:169pt'>
 <col width=3D566 span=3D2 style=3D'mso-width-source:userset;mso-width-alt:=
16099;
 width:425pt'>
 <col class=3Dxl65 width=3D566 style=3D'mso-width-source:userset;mso-width-=
alt:16099;
 width:425pt'>
 <col width=3D538 style=3D'mso-width-source:userset;mso-width-alt:15303;wid=
th:404pt'>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 width=3D27 style=3D'height:15.0pt;width:20pt'></td>
  <td width=3D225 style=3D'width:169pt'></td>
  <td width=3D566 style=3D'width:425pt'></td>
  <td width=3D566 style=3D'width:425pt'></td>
  <td class=3Dxl65 width=3D566 style=3D'width:425pt'></td>
  <td width=3D538 style=3D'width:404pt'></td>
 </tr>
 <tr height=3D21 style=3D'height:15.75pt'>
  <td height=3D21 style=3D'height:15.75pt'></td>
  <td class=3Dxl75>Stage</td>
  <td class=3Dxl75 style=3D'border-left:none'>GP Connect</td>
  <td class=3Dxl75 style=3D'border-left:none'>Care Connect</td>
  <td class=3Dxl76 width=3D566 style=3D'border-left:none;width:425pt'>Diffe=
rence</td>
  <td class=3Dxl75 style=3D'border-left:none'>Rationale for change</td>
 </tr>
 <tr height=3D21 style=3D'height:15.75pt'>
  <td height=3D21 class=3Dxl66 style=3D'height:15.75pt'></td>
  <td class=3Dxl67 style=3D'border-top:none'>Identify Patient</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>Use PDS to ge=
t a
  verified NHS Number DBS?</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>Use PDS to ge=
t a
  verified NHS Number</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>None</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>N/A</td>
 </tr>
 <tr height=3D80 style=3D'height:60.0pt'>
  <td height=3D80 class=3Dxl66 style=3D'height:60.0pt'></td>
  <td class=3Dxl77 style=3D'border-top:none'>Select service</td>
  <td class=3Dxl79 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>Get
  Registered GP Practice from PDS record<br>
    <br>
    Federations something else...</td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'>Use DOS to se=
lect a
  DOS profile</td>
  <td class=3Dxl79 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>In
  GP Connect, this is done as part of the PDS lookup, in Care Connect, it's=
 a
  separate call to the DOS, but one which is MOSTLY already taking place. S=
ome
  change needed to the DOS to return the ASID.</td>
  <td class=3Dxl79 width=3D538 style=3D'border-top:none;border-left:none;wi=
dth:404pt'>GP
  Connect is all about booking appointments with a GP Practice, which is a
  known ODS code. We're looking beyond this to services as identified from =
the
  DOS, or by ASID. These can also be found from SDS using ODS code.</td>
 </tr>
 <tr height=3D60 style=3D'mso-height-source:userset;height:45.0pt'>
  <td height=3D60 class=3Dxl66 style=3D'height:45.0pt'></td>
  <td rowspan=3D7 class=3Dxl67 style=3D'border-top:none'>Calls via SSP</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>Target URL is
  concatenated onto SSP URL</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>Target URL is
  concatenated onto SSP URL</td>
  <td class=3Dxl69 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>No
  change</td>
  <td rowspan=3D7 class=3Dxl69 width=3D538 style=3D'border-top:none;width:4=
04pt'>The
  Interaction IDs are different to allow them to be individually authorised,
  and to permit different endpoints to be offered per interaction. If there
  were no differences elsewhere they COULD be the same.<br>
    <br>
    SSP Could inspect the Authorization header and make decisions based on =
that
  (not currently in scope).</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 class=3Dxl66 style=3D'height:15.0pt'></td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>http headers =
are as
  follows</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>http headers =
are as
  follows</td>
  <td class=3Dxl69 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>Interaction
  IDs are different</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 class=3Dxl66 style=3D'height:15.0pt'></td>
  <td class=3Dxl70 style=3D'border-top:none;border-left:none'>Ssp-TraceID</=
td>
  <td class=3Dxl70 style=3D'border-top:none;border-left:none'>Ssp-TraceID =
=3D a UUID</td>
  <td class=3Dxl71 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>No
  change</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 class=3Dxl66 style=3D'height:15.0pt'></td>
  <td class=3Dxl70 style=3D'border-top:none;border-left:none'>Ssp-From</td>
  <td class=3Dxl70 style=3D'border-top:none;border-left:none'>Ssp-From =3D =
Client
  system ASID</td>
  <td class=3Dxl71 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>No
  change</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 class=3Dxl66 style=3D'height:15.0pt'></td>
  <td class=3Dxl70 style=3D'border-top:none;border-left:none'>Ssp-To</td>
  <td class=3Dxl70 style=3D'border-top:none;border-left:none'>Ssp-To =3D Se=
rver ASID</td>
  <td class=3Dxl71 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>No
  change</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 class=3Dxl66 style=3D'height:15.0pt'></td>
  <td class=3Dxl70 style=3D'border-top:none;border-left:none'>Ssp-Interacti=
onID</td>
  <td class=3Dxl70 style=3D'border-top:none;border-left:none'>Ssp-Interacti=
onID =3D
  Interaction ID from SDS specific to the call being made.</td>
  <td class=3Dxl71 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>Specific
  set for GP Connect, and another for Care Connect</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 class=3Dxl66 style=3D'height:15.0pt'></td>
  <td class=3Dxl89 style=3D'border-left:none'>N/A</td>
  <td class=3Dxl89 style=3D'border-left:none'>Authorization</td>
  <td class=3Dxl71 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>Uses
  a JWT token in an Authorization http header (not used by SSP)</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 class=3Dxl66 style=3D'height:15.0pt'></td>
  <td rowspan=3D2 class=3Dxl77 style=3D'border-top:none'>TLS/MA</td>
  <td rowspan=3D2 class=3Dxl78>Spine issued digital certificate required to=
 talk to
  PDS, SDS and SSP</td>
  <td rowspan=3D2 class=3Dxl78>Spine issued digital certificate required to=
 talk to
  PDS, SDS and SSP</td>
  <td class=3Dxl79 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>No
  change</td>
  <td rowspan=3D2 class=3Dxl78 style=3D'border-top:none'>N/A</td>
 </tr>
 <tr height=3D34 style=3D'height:25.5pt'>
  <td height=3D34 class=3Dxl66 style=3D'height:25.5pt'></td>
  <td class=3Dxl80 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>If
  client is <font class=3D"font11">only </font><font class=3D"font7">assure=
d for
  appointment booking, a certificate with a specific prefix will be issued,=
 to
  prevent it being used to do anything else.</font></td>
 </tr>
 <tr height=3D40 style=3D'mso-height-source:userset;height:30.0pt'>
  <td height=3D40 class=3Dxl66 style=3D'height:30.0pt'></td>
  <td rowspan=3D3 class=3Dxl67 style=3D'border-top:none'>SSP authorisation<=
/td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>Uses the foll=
owing</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>Uses the foll=
owing</td>
  <td class=3Dxl69 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>No
  Data Sharing Agreement required</td>
  <td rowspan=3D3 class=3Dxl69 width=3D538 style=3D'border-top:none;width:4=
04pt'>For
  MVP we're not requesting Patient info, hence lower IG concerns. The DSA
  approach doesn't scale for &quot;any to any&quot; as the scope expands.<b=
r>
    <br>
    Could be implemented in Authorization headers rather than config file.<=
/td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 class=3Dxl66 style=3D'height:15.0pt'></td>
  <td class=3Dxl70 style=3D'border-top:none;border-left:none'>SDS lookup fo=
r ASIDs</td>
  <td class=3Dxl70 style=3D'border-top:none;border-left:none'>SDS lookup fo=
r ASIDs</td>
  <td class=3Dxl71 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>No
  change</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 class=3Dxl66 style=3D'height:15.0pt'></td>
  <td class=3Dxl70 style=3D'border-top:none;border-left:none'>Data Sharing
  agreement between Client and Server</td>
  <td class=3Dxl70 style=3D'border-top:none;border-left:none'>N/A</td>
  <td class=3Dxl71 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>Not
  required</td>
 </tr>
 <tr height=3D40 style=3D'mso-height-source:userset;height:30.0pt'>
  <td height=3D40 class=3Dxl66 style=3D'height:30.0pt'></td>
  <td rowspan=3D3 class=3Dxl77 style=3D'border-top:none'>Find Patient</td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'>FHIR Search o=
peration
  on the endpoint via SSP</td>
  <td rowspan=3D3 class=3Dxl78 style=3D'border-top:none'>N/A</td>
  <td rowspan=3D3 class=3Dxl79 width=3D566 style=3D'border-top:none;width:4=
25pt'>Patient
  find is not used in Care Connect</td>
  <td rowspan=3D3 class=3Dxl79 width=3D538 style=3D'border-top:none;width:4=
04pt'>GP
  Connect works on the GP concept of patients being registered in a practic=
e.
  Many other services will not have this concept.</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 class=3Dxl66 style=3D'height:15.0pt'></td>
  <td class=3Dxl81 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>GET
  https://[proxy_server]/https://[provider_server]/[fhir_base]/Patient?iden=
tifier=3D[system]|[value]</td>
 </tr>
 <tr height=3D41 style=3D'mso-height-source:userset;height:30.75pt'>
  <td height=3D41 class=3Dxl66 style=3D'height:30.75pt'></td>
  <td class=3Dxl82 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>NB:
  in the above [system] will always be https://fhir.nhs.uk/Id/nhs-number and
  [value] will always be the NHS Number</td>
 </tr>
 <tr height=3D40 style=3D'height:30.0pt'>
  <td height=3D40 class=3Dxl66 style=3D'height:30.0pt'></td>
  <td class=3Dxl67 style=3D'border-top:none'>Register Patient</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>Patient is re=
gistered
  if not found.</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>N/A</td>
  <td class=3Dxl69 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>Register
  Patient is not done in Care Connect</td>
  <td class=3Dxl69 width=3D538 style=3D'border-top:none;border-left:none;wi=
dth:404pt'>If
  the service requires a patient to be registered, it can perform this with=
in
  the atomic booking process, rather than have a separate routine.</td>
 </tr>
 <tr height=3D60 style=3D'mso-height-source:userset;height:45.0pt'>
  <td height=3D60 style=3D'height:45.0pt'></td>
  <td rowspan=3D7 class=3Dxl77 style=3D'border-top:none'>Find Endpoint</td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'>Use SDS to get
  endpoint from nhsMHS object</td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'>Use SDS to get
  endpoint from nhsMHS object</td>
  <td class=3Dxl79 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>Different
  LDAP searches</td>
  <td rowspan=3D7 class=3Dxl79 width=3D538 style=3D'border-top:none;width:4=
04pt'>Knowing
  the ASID allows a simpler and faster / more efficient LDAP query, it also
  supports a more granular approach than ODS codes alone, including one ser=
ver
  endpoint for multiple DOS profiles.</td>
 </tr>
 <tr height=3D45 style=3D'height:33.75pt'>
  <td height=3D45 style=3D'height:33.75pt'></td>
  <td class=3Dxl83 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>ldapsearch
  -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk –b &quot;ou=3Dservices,
  o=3Dnhs&quot; &quot;(&amp;(nhsIDCode=3D<font class=3D"font9">T99999</font=
><font
  class=3D"font8">) (objectClass=3DnhsAS)(nhsAsSvcIA=3D</font><font class=
=3D"font9">urn:nhs:names:services:gpconnect:fhir:rest:search:slot-1</font><=
font
  class=3D"font8">))&quot; uniqueIdentifier nhsMhsPartyKey</font></td>
  <td class=3Dxl83 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>ldapsearch
  -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk –b &quot;ou=3Dservices,
  o=3Dnhs&quot; &quot;(&amp;(uniqueIdentifier=3D<font class=3D"font9">ABC12=
3</font><font
  class=3D"font8">) (objectClass=3DnhsAS)(nhsAsSvcIA=3D</font><font class=
=3D"font9">urn:nhs:names:services:a2si:fhir:rest:search:slot</font><font
  class=3D"font8">))&quot; nhsMhsPartyKey</font></td>
  <td rowspan=3D3 class=3Dxl80 width=3D566 style=3D'border-top:none;width:4=
25pt'>LDAP
  search is based on ODS code for GP Connect, ASID for Care Connect.<br>
    Interaction name is different.</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'><font class=
=3D"font5">T99999</font><font
  class=3D"font0"> =3D ODS Code of the GP Practice</font></td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'><font class=
=3D"font5">ABC123</font><font
  class=3D"font0"> =3D ASID of the service as returned from DOS</font></td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'><font class=
=3D"font5">gpconnect:fhir:rest:search:slot-1</font><font
  class=3D"font0"> is the Interaction being performed</font></td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'><font class=
=3D"font5">a2si:fhir:rest:search:slot</font><font
  class=3D"font0"> is the Interaction being performed</font></td>
 </tr>
 <tr height=3D45 style=3D'height:33.75pt'>
  <td height=3D45 style=3D'height:33.75pt'></td>
  <td class=3Dxl83 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>ldapsearch
  -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk -b &quot;ou=3Dservices,
  o=3Dnhs&quot; &quot;(&amp;(nhsMhsPartyKey=3D<font class=3D"font9">T99999-=
9999999</font><font
  class=3D"font8">) (objectClass=3DnhsMhs) (nhsMhsSvcIA=3D</font><font clas=
s=3D"font9">urn:nhs:names:services:gpconnect:fhir:rest:search:slot-1</font>=
<font
  class=3D"font8">))&quot; nhsMhsEndPoint nhsMHSFQDN</font></td>
  <td class=3Dxl83 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>ldapsearch
  -x -H ldaps://ldap.vn03.national.ncrs.nhs.uk -b &quot;ou=3Dservices,
  o=3Dnhs&quot; &quot;(&amp;(nhsMhsPartyKey=3D<font class=3D"font9">T99999-=
9999999</font><font
  class=3D"font8">) (objectClass=3DnhsMhs) (nhsMhsSvcIA=3D</font><font clas=
s=3D"font9">urn:nhs:names:services:a2si:fhir:rest:search:slot</font><font
  class=3D"font8">))&quot; nhsMhsEndPoint nhsMHSFQDN</font></td>
  <td rowspan=3D3 class=3Dxl80 width=3D566 style=3D'border-top:none;width:4=
25pt'>Search
  is identical apart from the Interaction ID being specific.</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'><font class=
=3D"font5">T99999-9999999</font><font
  class=3D"font0"> is the partyKey from previous step</font></td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'><font class=
=3D"font5">T99999-9999999</font><font
  class=3D"font0"> is the partyKey from previous step</font></td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'><font class=
=3D"font5">…:gpconnect:fhir:rest:search:slot-1</font><font
  class=3D"font0"> is the Interaction being performed</font></td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'><font class=
=3D"font5">…:a2si:fhir:rest:search:slot</font><font
  class=3D"font0"> is the Interaction being performed</font></td>
 </tr>
 <tr height=3D40 style=3D'mso-height-source:userset;height:30.0pt'>
  <td height=3D40 style=3D'height:30.0pt'></td>
  <td rowspan=3D2 class=3Dxl67 style=3D'border-top:none'>Get free slots</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>FHIR Search o=
peration
  on the endpoint via SSP</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>FHIR Search o=
peration
  on the endpoint via SSP</td>
  <td rowspan=3D2 class=3Dxl69 width=3D566 style=3D'border-top:none;width:4=
25pt'>No
  searchFilter parameter used in Care Connect, see below for more details. =
Also
  resource profiles are different.</td>
  <td rowspan=3D2 class=3Dxl69 width=3D538 style=3D'border-top:none;width:4=
04pt'>searchFilter
  is open to abuse., and not neeed if we use JWT (below).</td>
 </tr>
 <tr height=3D75 style=3D'height:56.25pt'>
  <td height=3D75 style=3D'height:56.25pt'></td>
  <td class=3Dxl72 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>GET
  https://[proxy_server]/https://[provider_server]/[fhir_base]/Slot?[start=
=3D{search_prefix}start_date][&amp;end=3D[{search_prefix}end_date][&amp;sta=
tus=3Dfree][&amp;_include=3DSlot:schedule]{&amp;_include:recurse=3DSchedule=
:actor:Practitioner}{&amp;_include:recurse=3DSchedule:actor:Location}{&amp;=
searchFilter=3D{OrgTypeSystem}|{OrgTypeValue}}{&amp;searchFilter=3D{OrgODSC=
odeSystem}|{OrgODSCode}}</td>
  <td class=3Dxl72 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>GET
  https://[proxy_server]/https://[provider_server]/[fhir_base]/Slot?[start=
=3D{search_prefix}start_date][&amp;end=3D[{search_prefix}end_date][&amp;sta=
tus=3Dfree][&amp;_include=3DSlot:schedule]{&amp;_include:recurse=3DSchedule=
:actor:Practitioner}{&amp;_include:recurse=3DSchedule:actor:Location}</td>
 </tr>
 <tr height=3D100 style=3D'mso-height-source:userset;height:75.0pt'>
  <td height=3D100 style=3D'height:75.0pt'></td>
  <td rowspan=3D2 class=3Dxl77 style=3D'border-top:none'>Identify requester=
</td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'>searchFilter
  parameter</td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'>JWT</td>
  <td class=3Dxl79 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>GP
  Connect expects an assertion of the type of organisation making the reque=
st
  and their ODS Code in a searchFilter querystring parameter. Care Connect
  expects to get this information from a signed JWT issued by Strat Auth.</=
td>
  <td rowspan=3D2 class=3Dxl79 width=3D538 style=3D'border-top:none;width:4=
04pt'>This
  is a combination of authentication (who is the client) and authorisation
  (what can they do) and therefore should be handled as such. Implementing =
this
  removes the need for searchFilter. Using a signed JWT gives the server
  significant confidence in the identity of the client, which should help to
  reduce IG challenges.</td>
 </tr>
 <tr height=3D75 style=3D'height:56.25pt'>
  <td height=3D75 style=3D'height:56.25pt'></td>
  <td class=3Dxl83 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>GET
  https://[proxy_server]/https://[provider_server]/[fhir_base]/Slot?[start=
=3D{search_prefix}start_date][&amp;end=3D[{search_prefix}end_date][&amp;sta=
tus=3Dfree][&amp;_include=3DSlot:schedule]{&amp;_include:recurse=3DSchedule=
:actor:Practitioner}{&amp;_include:recurse=3DSchedule:actor:Location}<font
  class=3D"font9">{&amp;searchFilter=3D{OrgTypeSystem}|{OrgTypeValue}}{&amp=
;searchFilter=3D{OrgODSCodeSystem}|{OrgODSCode}}</font></td>
  <td class=3Dxl84 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'><font
  class=3D"font13">See:
  https://developer.nhs.uk/apis/spine-core/security_jwt.html<br>
    </font><font class=3D"font12">ToDo: Provide a sample JWT</font></td>
  <td class=3Dxl79 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>JWT
  can be verified by checking signature.</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td rowspan=3D2 class=3Dxl67 style=3D'border-top:none'>Book an appointmen=
t</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>FHIR Create o=
peration
  on the endpoint via SSP</td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>FHIR Create o=
peration
  on the endpoint via SSP</td>
  <td rowspan=3D2 class=3Dxl69 width=3D566 style=3D'border-top:none;width:4=
25pt'>Resources
  are (will be) different.</td>
  <td rowspan=3D2 class=3Dxl90 style=3D'border-top:none'>See FHIR Resource =
rationale.</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl73 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>POST
  https://[proxy_server]/https://[provider_server]/[fhir_base]/Appointment<=
/td>
  <td class=3Dxl73 width=3D566 style=3D'border-top:none;border-left:none;wi=
dth:425pt'>POST
  https://[proxy_server]/https://[provider_server]/[fhir_base]/Appointment<=
/td>
 </tr>
 <tr height=3D60 style=3D'height:45.0pt'>
  <td height=3D60 style=3D'height:45.0pt'></td>
  <td class=3Dxl77 style=3D'border-top:none'>FHIR Resource profiles</td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'>GP Connect sp=
ecific
  ones</td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'>Care Connect =
Generic
  where possible</td>
  <td rowspan=3D9 class=3Dxl79 width=3D566 style=3D'border-top:none;width:4=
25pt'>Resources
  are still based on FHIR STU3 but are (or will be) different.</td>
  <td class=3Dxl79 width=3D538 style=3D'border-top:none;border-left:none;wi=
dth:404pt'>GP
  Connect resources are by definition (it's part of their name) for GP Conn=
ect.
  Where possible we try to use generic resources. Each has been profiled to
  include the necessary information.</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl78 style=3D'border-top:none'>Slot Profile</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
nhs.uk/STU3/StructureDefinition/GPConnect-Slot-1</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
nhs.uk/STU3/StructureDefinition/CareConnect-Slot-1</td>
  <td class=3Dxl86 style=3D'border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl78 style=3D'border-top:none'>Appointment Profile</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
nhs.uk/STU3/StructureDefinition/GPConnect-Appointment-1</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
nhs.uk/STU3/StructureDefinition/CareConnect-Appointment-1</td>
  <td class=3Dxl86 style=3D'border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl78 style=3D'border-top:none'>Patient Profile</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Patient-1</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1</td>
  <td class=3Dxl86 style=3D'border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl78 style=3D'border-top:none'>LocationProfile</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Location-1</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1</td>
  <td class=3Dxl86 style=3D'border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl87 style=3D'border-top:none'>Practitioner Profile</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Practitioner-1</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1</td>
  <td class=3Dxl86 style=3D'border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=3D21 style=3D'height:15.75pt'>
  <td height=3D21 style=3D'height:15.75pt'></td>
  <td class=3Dxl87 style=3D'border-top:none'>Schedule profile</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
nhs.uk/STU3/StructureDefinition/GPConnect-Schedule-1</td>
  <td class=3Dxl88 style=3D'border-top:none;border-left:none'>TBC</td>
  <td class=3Dxl86 style=3D'border-top:none;border-left:none'>&nbsp;</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl87 style=3D'border-top:none'>PractitionerRole Profile</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>N/A</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1</td>
  <td class=3Dxl86 style=3D'border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl87 style=3D'border-top:none'>Organisation profile</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Organization-1</td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://fhir.=
hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1</td>
  <td class=3Dxl86 style=3D'border-top:none;border-left:none'>Uses standard
  CareConnect profile</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td rowspan=3D2 class=3Dxl91 style=3D'border-top:none'>Search for appoint=
ments</td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'>Described</td>
  <td rowspan=3D2 class=3Dxl68 style=3D'border-top:none'>Out of current sco=
pe</td>
  <td rowspan=3D2 class=3Dxl69 width=3D566 style=3D'border-top:none;width:4=
25pt'>Not in
  scope for Care Connect</td>
  <td rowspan=3D2 class=3Dxl93 style=3D'border-top:none'>Not in current sco=
pe. IG
  concerns are higher, so excluded from MVP.</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'><a
  href=3D"https://nhsconnect.github.io/gpconnect/appointments_use_case_retr=
ieve_a_patients_appointments.html"
  target=3D"_parent"><span style=3D'color:black;font-size:8.0pt;text-decora=
tion:
  none'>https://nhsconnect.github.io/gpconnect/appointments_use_case_retrie=
ve_a_patients_appointments.html</span></a></td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td rowspan=3D2 class=3Dxl92 style=3D'border-top:none'>Cancel Appointment=
</td>
  <td class=3Dxl78 style=3D'border-top:none;border-left:none'>Described</td>
  <td rowspan=3D2 class=3Dxl78 style=3D'border-top:none'>Out of current sco=
pe</td>
  <td rowspan=3D2 class=3Dxl79 width=3D566 style=3D'border-top:none;width:4=
25pt'>Not in
  scope for Care Connect</td>
  <td rowspan=3D2 class=3Dxl94 style=3D'border-top:none'>Not in current sco=
pe. IG
  concerns are higher, so excluded from MVP.</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl85 style=3D'border-top:none;border-left:none'>https://nhsco=
nnect.github.io/gpconnect/appointments_use_case_cancel_an_appointment.html<=
/td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td rowspan=3D2 class=3Dxl91 style=3D'border-top:none'>Amend Appointment<=
/td>
  <td class=3Dxl68 style=3D'border-top:none;border-left:none'>Described</td>
  <td rowspan=3D2 class=3Dxl68 style=3D'border-top:none'>Out of current sco=
pe</td>
  <td rowspan=3D2 class=3Dxl69 width=3D566 style=3D'border-top:none;width:4=
25pt'>Not in
  scope for Care Connect</td>
  <td rowspan=3D2 class=3Dxl93 style=3D'border-top:none'>Not in current sco=
pe. IG
  concerns are higher, so excluded from MVP.</td>
 </tr>
 <tr height=3D20 style=3D'height:15.0pt'>
  <td height=3D20 style=3D'height:15.0pt'></td>
  <td class=3Dxl74 style=3D'border-top:none;border-left:none'>https://nhsco=
nnect.github.io/gpconnect/appointments_use_case_amend_an_appointment.html</=
td>
 </tr>
 <![if supportMisalignedColumns]>
 <tr height=3D0 style=3D'display:none'>
  <td width=3D27 style=3D'width:20pt'></td>
  <td width=3D225 style=3D'width:169pt'></td>
  <td width=3D566 style=3D'width:425pt'></td>
  <td width=3D566 style=3D'width:425pt'></td>
  <td width=3D566 style=3D'width:425pt'></td>
  <td width=3D538 style=3D'width:404pt'></td>
 </tr>
 <![endif]>
</table>
