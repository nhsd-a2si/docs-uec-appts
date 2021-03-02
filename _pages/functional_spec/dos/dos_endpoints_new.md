---
title: Endpoint Structure - new approach
sidebar: overview_sidebar
keywords: specification
permalink: dos_endpoints_new.html
toc: false
folder: dos
---

## Recent changes to the way endpoints are stored in and returned by the DoS

Recently the endpoint format that is returned by the DoS API has changed. This change was included in the January 2019 release (1.5).

The main change is to move away from a single string value with endpoint items delimited into key/value pairs and to have explicit separate entries in the XML structure for each of the endpoint values.

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

As can be seen above each value has its own entry in the XML structure.
