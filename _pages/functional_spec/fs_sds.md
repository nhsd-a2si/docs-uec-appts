---
title: Interactions with the SDS
sidebar: overview_sidebar
keywords: specification
permalink: fs_sds.html
toc: false
folder: functional_spec
---

## Introduction

The <a href="https://nhsconnect.github.io/FHIR-SpineCore/build_directory.html" target="_blank">Spine   Directory Services (known as the "SDS")</a> is the national directory of organisations, people and systems registered with the Spine and although this standard supports booking workflows that do not need to use the SDS it is envisaged that it will provide the end point discovery element in the majority of booking workflows that use this standard.

Within the four key elements in the booking sequence.

* Service discovery
* End point discovery
* Slot discovery
* Booking a slot

The SDS supports end point discovery, that is, consumer systems use the SDS to obtain a FHIR Endpoint Server Root URL that can be invoked.  A precursor to this end point discovery is the establishment of the service provider ASID, see [Workflow and Interactions](/fs_workflow.md).

The discovery of the FHIR end point is a two stage process, first using the ASID mentioned above the consumer system obtains the nhsAS object that contains an MHS Party Key, then from the nhsMHS object the consumer system can then extract the nhsMHSEndPoint.



<dl>
  <dt>Example</dt>
  
  <dt>Step 1</dt>
  <dd>ASID of 123456789012 obtained from DoS is used to obtain the nhsMHSPartyKey of the nhsAS object.</dd>
  <dd>Query - ldapsearch -b uniqueIdentifier=123456789012,ou=Services,o=nhs nhsMHSPartyKey</dd>
  <dd>Response - nhsMHSPartyKey : A12345-1234567</dd>

  <dt>Step 2</dt>
  <dd>nhsMHSPartyKey of 12345-1234567 is used to obtain the nhsMHSEndPoint</dd>
  <dd>Query - ldapsearch -b ou=Services,o=nhs "(&(nhsMHSPartyKey= A12345-1234567)(urn:nhs:names:services:careconnect:fhir:rest:create:appointment))" nhsMHSEndPoint</dd>
  <dd>Response - nhsMHSEndPoint : https://server.domain.nhs.uk/fhir_base</dd>

</dl>
