---
title: Interactions with the SDS
sidebar: overview_sidebar
keywords: specification
permalink: fs_sds.html
toc: true
folder: functional_spec
---

## Introduction

The <a href="https://nhsconnect.github.io/FHIR-SpineCore/build_directory.html" target="_blank">Spine   Directory Services (known as the "SDS")</a> is the national directory of organisations, people and systems registered with the Spine and although this standard supports booking workflows that do not need to use the SDS it is envisaged that it will provide the end point discovery element in the majority of booking workflows that use this standard.

Within the four key elements in the booking sequence.

* Service discovery
* End point discovery
* Slot discovery
* Booking a slot

The SDS supports end point discovery, that is consumer systems use the SDS to obtain a FHIR Endpoint Server Root URL that can be invoked.  A precursor to this end point discovery is the establishment of the service provider ASID, see [Workflow and Interactions](/fs_workflow.md).

The discovery of the FHIR end point is a two stage process, first using the ASID mentioned above the consumer system obtains the nhsAS object that contains an MHS Party Key.  From the nhsMHS object the consumer system can then extract the nhsMHSEndPoint.



### Example

#### Step 1.

ASID of 123456789012 obtained from DoS is used to obtain the nhsMHSPartyKey of the nhsAS object.

**Query**<br>
ldapsearch -b uniqueIdentifier=123456789012,ou=Services,o=nhs nhsMHSPartyKey

**Response**<br>
nhsMHSPartyKey : A12345-1234567

#### Step 2.

**Query**<br>
ldapsearch -b ou=Services,o=nhs "(&(nhsMHSPartyKey= A12345-1234567)(urn:nhs:names:services:careconnect:fhir:rest:create:appointment))" nhsMHSEndPoint

**Response**<br>
nhsMHSEndPoint : https://server.domain.nhs.uk/fhir_base
