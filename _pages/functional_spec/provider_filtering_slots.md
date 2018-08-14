---
title: Filtering Slots
sidebar: overview_sidebar
permalink: provider_filtering_slots.html
---

## Background
It is common for system suppliers to present a single API endpoint that is shared between multiple healthcare services - this is particularly common where a system is centrally-hosted and multi-tenanted, or where an organisation has a single IT system that is used to provide multiple healthcare services.

The Directory of Services (DoS) lists services at the granular healthcare service level i.e. for each of the above example healthcare services, the DoS will have 1 or more service records defined. It is these individual service records that are presented to users when searching the DoS.

*Example: An NHS provider organisation, 'Trumpton Urgent Care Services', which provides several healthcare services including an NHS 111 call centre, an Out of Hours (OOH) GP service, and an Urgent Treatment Centre (UTC). The OOH GP service may offer two sub-services on DoS: OOH GP Telephone Consultations, and OOH GP Face to face Consultations.*

When an appointments consumer (e.g. NHS 111) requests available slots from a healthcare service, it needs to identify exactly which healthcare service it is targeting. This will allow provider systems to correctly route requests and filter the responses to be relevant to the specific request.

## Using 'searchFilter' to filter slots requests to specific healthcare services
The GP Connect specification includes an optional request parameter called 'searchFilter' - this can be included when performing a Slot request. [Details on the GP Connect searchFilter parameter are here.](https://nhsconnect.github.io/gpconnect/appointments_use_case_search_for_free_slots.html#enhanced-slot-filtering)

### As a consumer, include the DoS Service ID as a searchFilter parameter
As a consumer, you should include a `searchFilter` parameter specifying the DoS Service ID of the healthcare service to which you are directing the query. 

#### Example
If the DoS has returned a service "Village Urgent Treatment Centre (ID:124459850)", and you would like to book an appointmnent at that service, you will want to ensure the available slots you are presented with are specifically for that service.

You would include a `searchFilter` parameter in your Slot request containing:

* **A parameter system URI** e.g. `https://directoryofservices.nhs.uk/Id/serviceId` 
    * This identifies the type of the parameter that we are providing
* **A parameter value** `124459850`
    * This identifies the specific service, using the DoS Service ID, that you are requesting slots from

So in a Slot request, this might look like:

```http
GET /Slot?start=ge2018-08-01T09:00:00&end=le2018-08-01T14:00:00&status=free&_include=Slot:schedule&_include:recurse=Schedule:actor:Practitioner&_include:recurse=Schedule:actor:Location&searchFilter=https://fhir.nhs.uk/Id/ods-organization-code|FA890&searchFilter=https://fhir.nhs.uk/STU3/ValueSet/GPConnect-OrganisationType-1|Urgent%20Care&searchFilter=https://directoryofservices.nhs.uk/Id/serviceId|124459850
```

