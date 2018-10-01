---
title: Workflow and Interactions
sidebar: overview_sidebar
keywords: specification
permalink: fs_workflow.html
toc: true
folder: functional_spec
---

{% include note-notpublished.html %}

## Introduction
This section describes the message interactions that happen as part of the main booking workflow. It will define the key parameters and attributes required to progress through the booking flow.

Below is the primary data model that describes the key data items that are required.

### Primary Data Model

<img src="_pages/functional_spec/img/UEC_Appointments_Flow.png">

The sections below will step through the process.

## The Actors

There are a number of different systems involved in the end to end booking process. These fall into the following catagories:

* Consumer System
* National Infrastructure
* Provider System

<img src="_pages/functional_spec/img/Actors.png">

### Consumers

The consuming system belongs to the service that is searching for an appropriate appointment for the patient. The system will participate in discovery of the appropriate service, discovery of its booking endpoint, searching the providing system for appropriate slots and then booking one of those slots for the patient. There are many examples of services that could be fullfilling this role for example NHS111, IUC Clinical Hub, A&E or even a GP Service.

### National Infrastructure

During the booking provess a number of systems that are hosted by NHS Digital as national infrastructure need to be interacted with. These are as follows:

####  National DoS
The national DoS can be used to discover the most appropriate service for the patient. If that service offers appointments the necessary information required to query SDS for the endpoint will be provided. 

#### Spine Directory Service (SDS)
The SDS performs the role of the booking endpoint repository. Endpoints for the booking API of target provider systems will be registered on the SDS as part of <A href="https://nhsd-a2si.github.io/docs-uec-appts/assurance_supplier.html">assurance</a>.

#### Spine Secure Proxy (SSP)
The SSP brokers and routes connections to endpoints. In order to facilitate urgent appointment booking it is important to support the ability to establish connections between systems on-the-fly without prior networking or security configuration between two specific systems. In order to do this all communications between systems are brokered via the SSP. That way systems involved in booking only ever need to establish and accept connections from/to the SSP which can be configured once, as part of <A href="https://nhsd-a2si.github.io/docs-uec-appts/assurance_supplier.html">assurance</a>

### Provider Systems
The provider system is the system that is offering appointments to be booked into. This system will be configured to accept connections from the SSP and will offer the defined capabilities in this standard via its FHIR Interface. There are many different service types that could be a booking provider including UTC's, OOH GP's, Emergency Dental services etc.. 

## Service Discovery

The first step of the booking process involves some form of service discovery. Typically this will use the DoS to identify the most appropriate service to meet the patients needs. 

In the situation the DoS is being used there will be the initial call to the DoS API to return the ordered list of appropriate services ('CheckCapacitySummary'). 
<img src="_pages/functional_spec/img/ServiceDiscovery1.png">

Once the chosen service has been selected the next call to the DoS API is made ('ServiceDetailsByID') and this will return the specific details of the selected service including something called an "ASID".
<img src="_pages/functional_spec/img/ServiceDiscovery2.png">

An ASID (Accredited System Identifier) is used to obtain the endpoint for booking into the Provider system.

## Endpoint Discovery

The consuming system needs to interact with SDS in order to resolve the FHIR Endpoint Server Root URL to be used when constructing the request to be made to the Spine Security Proxy.

In order for the Consuming system to make a request to the SSP it needs to resolve the FHIR endpoints root URL. In order to do this the information that is needed to build the request is stored on the SDS. The SDS can be queried using the ASID

<img src="_pages/functional_spec/img/EndpointDiscovery1.png">
<img src="_pages/functional_spec/img/EndpointDiscovery2.png">
<img src="_pages/functional_spec/img/EndpointDiscovery3.png">
<img src="_pages/functional_spec/img/EndpointDiscovery4.png">

## Get Slots

<img src="_pages/functional_spec/img/GetSlots1.png">
<img src="_pages/functional_spec/img/GetSlots2.png">

## Book Appointment

<img src="_pages/functional_spec/img/BookAppointment1.png">
<img src="_pages/functional_spec/img/BookAppointment2.png">
<img src="_pages/functional_spec/img/BookAppointment3.png">
