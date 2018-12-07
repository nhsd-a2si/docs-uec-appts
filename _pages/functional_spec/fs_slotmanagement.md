---
title: Slot Management
sidebar: overview_sidebar
keywords: specification
permalink: fs_slotmanagement.html
toc: false
folder: functional_spec
---

{% include note-notpublished.html %}

## Background
It is common for system suppliers to present a single API endpoint that is shared between multiple healthcare services - this is particularly common where a system is centrally-hosted and multi-tenanted, or where an organisation has a single IT system that is used to provide multiple healthcare services.

The Directory of Services (DoS) lists services at the granular healthcare service level i.e. for each of the above example healthcare services, the DoS will have 1 or more service records defined. It is these individual service records that are presented to users when searching the DoS.

*Example: An NHS provider organisation, 'Trumpton Urgent Care Services', which provides several healthcare services including an NHS 111 call centre, an Out of Hours (OOH) GP service, and an Urgent Treatment Centre (UTC). The OOH GP service may offer two sub-services on DoS: OOH GP Telephone Consultations, and OOH GP Face to face Consultations.* Each of these would be represented in the DoS as discreet services.

When an appointments consumer (e.g. NHS 111) requests available slots from a healthcare service, it needs to identify exactly which healthcare service it is targeting. This will allow provider systems to correctly route requests and filter the responses to be relevant to the specific request.

## Use HealthcareServiceID to filter slot requests to specific healthcare services
A search parameter of the HealthcareService (an intrinsic part of FHIR RESTful search) will be sent.

### As a consumer, include the ASID of the healthcare service as a parameter
As a consumer, you should include a search parameter specifying the ASID of the healthcare service to which you are directing the query.

#### Example
If the DoS has returned a service "Village Urgent Treatment Centre (ASID:124459850)", and you would like to book an appointmnent at that service, you will want to ensure the available slots you are presented with are specifically for that service.

You would include a HealthcareServiceID parameter in your Slot request.

### As a provider, use the healthcare service ASID to filter the slots returned in your response
As a provider of slots, you will likely want to ensure that you only return slots in your response for which you would be happy receiving a booking.

Filtering is based both on the JWT received in the http Authorization header (to filter slots appropriate to be released to that specific Consumer) and on the healthcareservice specified in the query (to filter slots provided by that specific service)

#### Example
You run three healthcare services from the same system:

1. Walk-in Centre
2. OOH GP Service
3. Urgent Treatment Centre

Within your system you might have a separate appointment schedule for each of these services. 

You should configure a mapping between the healthcare services for which you might receive queries, and the appointment schedules against which you'd like those queries to be run.

| Service                 | ASID | Linked Schedule |
|-------------------------|------------|-----------------|
| Walk-in Centre          | 124459850 | Schedule 1      |
| Urgent Treatment Centre | 2329483525 | Schedule 2      |
| OOH GP Service          | 0123944122 | Schedule 3      |

You might want to share schedules between healthcare services, so you could include multiple mappings like this:

| Service                 | ASID | Linked Schedule |
|-------------------------|------------|-----------------|
| Walk-in Centre          | 124459850 | Schedule 1      |
| Urgent Treatment Centre | 2329483525 | Schedule 1      |
| Urgent Treatment Centre | 2329483525 | Schedule 2      |
| OOH GP Service          | 0123944122 | Schedule 2      |
| OOH GP Service          | 0123944122 | Schedule 3      |

As a provider, it is essentially up to you to decide how you filter the slots that you return but it is important to consider that a consumer will assume that any returned slot is a valid slot for booking - it is important that the slots you return are genuinely available to the patient within the context of the request you've received.
