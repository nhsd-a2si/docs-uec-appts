---
title: Endpoint Structure - new approach
sidebar: dos_sidebar
keywords: specification
permalink: dos_endpoints_new.html
toc: true
folder: dos
---

{% include note-notpublished.html %}

## Proposed changes to the way endpoints are stored in and returned by the DoS

It is proposed that the endpoint format that is returned by the DoS API will change. The target release date for this is January 2019.
An example of the XML in the new format returned by the API is below:

```xml
<ns1:serviceEndPoints>
  <ns1:EndPoint>
     <ns1:endpointOrder>1</ns1:endpointOrder>
     <ns1:transport>email</ns1:transport>
     <ns1:format>HTML</ns1:format>
     <ns1:interaction>urn:nhs-itk:interaction:primaryEmergencyDepartmentRecipientNHS111CDADocument-v2-0</ns1:interaction>
     <ns1:businessScenario>Primary</ns1:businessScenario>
     <ns1:address>an address</ns1:address>
     <ns1:isCompressionEnabled>uncompressed</ns1:isCompressionEnabled>
     <ns1:comment>a comment</ns1:comment>
  </ns1:EndPoint>
<ns1:serviceEndPoints/>
```
