---
title: Endpoint Structure - booking changes
sidebar: overview_sidebar
keywords: specification
permalink: dos_endpoints_booking.html
toc: false
folder: dos
---

## Changes to support Appointment Booking

For appointment booking there is a new transport type, format and interaction. There are also two new address types, ASID and ODS.

The new items are listed below:

* Transport: http
* Format: FHIR
* Interaction: Scheduling
* address: and ODS or ASID referencing the AS Object in SDS for the booking endpoint for this service (with the form "ODS:xxxx" or "ASID:xxxx")

An example of how this will look in XML is below:


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
  <ns1:EndPoint>
     <ns1:endpointOrder>2</ns1:endpointOrder>
     <ns1:transport>http</ns1:transport>
     <ns1:format>FHIR</ns1:format>
     <ns1:interaction>Scheduling</ns1:interaction>
     <ns1:address>ASID:918999198999|or|ODS:ABC123</ns1:address>
     <ns1:comment>a comment</ns1:comment>
  </ns1:EndPoint>
</ns1:serviceEndPoints>
```

