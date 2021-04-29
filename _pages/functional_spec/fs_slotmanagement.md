---
title: Slot Management
sidebar: overview_sidebar
keywords: specification
permalink: fs_slotmanagement.html
toc: false
folder: functional_spec
---

## Introduction

As already described some form of a service discovery tool is envisaged to be used as part of the booking workflow. One aspect of using a service discovery tool (such as the UEC DoS) that has not been described is how outcomes from the prior clinical assessment map to services and subsequent booking workflows. 

### With booking based on this standard

It is the intention that with booking using this standard, the clinical profiling of the service will solely determine the requirement for booking. This is because of the effective 1:1 mapping between service and booking diary. This means that for example with UEC appointment booking using this standard, if a service is returned and has a booking endpoint, then a booking should be attempted with no further check on the outcome of the prior clinical assessment.

### Support for "booking only" type services

Some services that are profiled on the Urgent Care Directory of Services are comissioned as "booking only" services. That is to say that they only accept referrals with an booking. If no booking is available then a referral should not be made.

A "service attribute" is configurable against services. This will allow the service to be flagged as "booking only". Therefore if this attribute is present on the service all consumer systems should withold referrals. More information can be found <a href="dos_bookingonly.html" target="_blank">here</a>


## Background
It is common for system suppliers to present a single API endpoint that is shared between multiple healthcare services - this is particularly common where a system is centrally-hosted and multi-tenanted, or where an organisation has a single IT system that is used to provide multiple healthcare services.

> *Example: An NHS provider organisation, 'Trumpton Urgent Care Services', which provides several healthcare services including an NHS 111 call centre, an Out of Hours (OOH) > GP service, and an Urgent Treatment Centre (UTC). The OOH GP service may offer two sub-services on DoS: OOH GP Telephone Consultations, and OOH GP Face to face Consultations.* 

Each of the above would be represented in the DoS as discrete services.

Some service discovery tools (such as the UEC Directory of Services (DoS)) list services at the granular healthcare service level i.e. for each of the above example healthcare services, the DoS will have 1 or more service records defined. It is these individual service records that are presented to users when searching the DoS.

When a booking consumer (e.g. NHS 111) requests available slots from a healthcare service, it needs to identify exactly which healthcare service it is targeting. This will allow provider systems to correctly route requests and filter the responses to be relevant to the specific request.

> A Key concept here is that it is the Provider of appointments that controls what is returned. The Consumer does NO filtering and is "dumb", just showing all the slots that are returned.

## Use Healthcare Service ID to filter slot requests to specific healthcare services
A search parameter of the HealthcareService (an intrinsic part of FHIR RESTful search) will be sent.

### As a consumer, include the ID of the healthcare service as a parameter
As a consumer, you should include a search parameter specifying the Service Discovery tool ID of the healthcare service to which you are directing the query.

#### Example
If the DoS has returned a service "Village Urgent Treatment Centre (Dos Service ID:124459850)", and you would like to book an appointmnent at that service, you will want to ensure the available slots you are presented with are specifically for that service.

You would include a Service ID parameter in your Slot request.

### As a provider, use the healthcare service ID to filter the slots returned in your response
As a provider of slots, you will likely want to ensure that you only return slots in your response for which you would be happy receiving a booking.

Filtering is based both on the JWT received in the http Authorization header (to filter slots appropriate to be released to that specific Consumer) and on the healthcareservice specified in the query (to filter slots provided by that specific service)

#### Example
You run three healthcare services from the same system:

1. Walk-in Centre
2. OOH GP Service
3. Urgent Treatment Centre

Within your system you might have a separate booking schedule for each of these services. 

You should configure a mapping between the healthcare services for which you might receive queries, and the booking schedules against which you'd like those queries to be run.

| Service                 | DoS ID | Linked Schedule |
|-------------------------|------------|-----------------|
| Walk-in Centre          | 124459850 | Schedule 1      |
| Urgent Treatment Centre | 2329483525 | Schedule 2      |
| OOH GP Service          | 0123944122 | Schedule 3      |

You might want to share schedules between healthcare services, so you could include multiple mappings like this:

| Service                 | DoS ID | Linked Schedule |
|-------------------------|------------|-----------------|
| Walk-in Centre          | 124459850 | Schedule 1      |
| Urgent Treatment Centre | 2329483525 | Schedule 1      |
| Urgent Treatment Centre | 2329483525 | Schedule 2      |
| OOH GP Service          | 0123944122 | Schedule 2      |
| OOH GP Service          | 0123944122 | Schedule 3      |

As a provider, it is essentially up to you to decide how you filter the slots that you return but it is important to consider that a consumer will assume that any returned slot is a valid slot for booking - it is important that the slots you return are genuinely available to the patient within the context of the request you've received.
