---
title: Endpoint Structure
sidebar: dos_sidebar
keywords: specification
permalink: dos_endpoints.html
toc: true
folder: dos
---

{% include note-notpublished.html %}

## Current Endpoint Configuration in the DoS

The DoS currently has several different types of endpoints to support existing onward distribution of information for varios different types of interction scenarios. There s a UI to allow DoS administration users to create and manage these endpoints:

<img src="_pages/functional_spec/dos/img/Current_endpoint_stucture.png">

The endpoint data is currently shared with systems that are looking up the DoS through the look up API. This information gets returned as part of the response to a "GetServiceDetailsByID" API call. It is returned in the form of a long string with the endpoint data delimited into key/value pairs.

The DoS is being updated to change this response structure and incorporate a new set of endpoint data to support appointment booking.

There are five key data items that define an endpoint:

### Transports

The DoS currently supports the following transports:
<img src="_pages/functional_spec/dos/img/transports.png">

### Interactions

The DoS currently supports the following interactions
<img src="_pages/functional_spec/dos/img/interactions.png">

### Formats

The DoS currently supports the following formats
<img src="_pages/functional_spec/dos/img/formats.png">

### Business Scenarios

The DoS currently supports the following business scenarios:
* Primary
* Copy

### Endpoints Address

The endpoint address is a free text field synonomous to a "URI".

### Current XML Response

The majority of the above fields are combined into a single "\|" delimited string.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<env:Envelope xmlns:env="http://www.w3.org/2003/05/soap-envelope" xmlns:ns1="https://nww.pathwaysdos.nhs.uk/app/api/webservices">
    <env:Body>
        <ns1:ServiceDetailsByIdResponse>
            <ns1:services>
                <ns1:service>
                    <ns1:id>1482418198</ns1:id>
                    <ns1:odsCode>1424900070 001</ns1:odsCode>
                    <ns1:contactDetails>
                        <ns1:contactDetail>
                            <ns1:tag>itk</ns1:tag>
                            <ns1:name>111 Routing Details</ns1:name>
                            <ns1:value>https://NQ7.oneoneone.nhs.uk:1880/NHS111/NHS111v2.svc\|urn:nhs-itk:interaction:primaryOutofHourRecipientNHS111CDADocument-v2-0\|CDA\|Primary\|\|uncompressed</ns1:value>
                            <ns1:order>1</ns1:order>
                        </ns1:contactDetail>
                    </ns1:contactDetails>
                </ns1:service>
            </ns1:services>
        </ns1:ServiceDetailsByIdResponse>
    </env:Body>
</env:Envelope>
```

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

# Proposed Changes to support Appointment Booking

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
     <ns1:endpointOrder>1</ns1:endpointOrder>
     <ns1:transport>http</ns1:transport>
     <ns1:format>FHIR</ns1:format>
     <ns1:interaction>Scheduling</ns1:interaction>
     <ns1:asid>an ASID (eg 918999198999 Usually 12 (but could be more) digits, stored as a string)</ns1:asid>
     <ns1:comment>a comment</ns1:comment>
  </ns1:EndPoint>
</ns1:serviceEndPoints>
```
