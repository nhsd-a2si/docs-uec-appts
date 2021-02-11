---
title: Deployment Toolkit - DoS Lead Resources
sidebar: deployment_sidebar
keywords: guidance
permalink: dep_dosoverview.html
toc: false
folder: deployment
---

## What do I need to know? 

When a service engages a project to open their booking schedules, and allow other services to discover them and consume their resources, there are going to need to work closely with DoS leads. The way in which a service exposes their schedule resource (slots for booking into) will be entirely down to how the service discovery tool used, in the example to follow the DoS (Directory of Services), is configured.

System suppliers will build to the Booking Standard and support Service Providers to offer their schedule resource in a very granular way, splitting services using the DoS Service Id or combining them, as detailed under the <a href="fs_slotmanagement.html" target="_blank">functional specification</a>. The DoS Service Id is central to exposing the service schedules, marrying up the Service Provider’s schedules with entries on the DoS.

## Configuring the DoS for Appointment Booking

### Scheduling Endpoint

A scheduling endpoint must be configured against a service to enabling booking. If a Service Provider opts to divide their schedule resource, it is permissable to configure the same endpoint against multiple DoS Service Ids. The services making a request (the consumers) of the Service Providers resource will use the DoS Service Id to distinguish between different schedules the Service Provider offers. 

#### Configuring DoS
1. Find or create the service you wish to add the scheduling endpoint to 
2. On the 'Endpoint Details' tab, click 'Add an Endpoint'
<img src="_pages/deployment/toolkit/img/DoS_FHIR_Endpoints.png">
3. Configure the endpoint options, as detailed in the screenshot below
<img src="_pages/deployment/toolkit/img/DoS_FHIR_EndpointsConfig.png">
4. The Address field is important, it must have the 'ASID:' prefix before the ASID value
<img src="_pages/deployment/toolkit/img/DoS_FHIR_ASID_Prefix.png">
5. Click 'Save' to commit the configuration, followed by 'OK'
<img src="_pages/deployment/toolkit/img/DoS_FHIR_Endpoint_Save.png">
6. The scheduling endpoint should not be visible under 'Endpoint Details'
<img src="_pages/deployment/toolkit/img/DoS_FHIR_Endpoint_Complete.png">
{% include important.html content="Services consuming the schedule resoure to request bookings rely on the **ASID:** prefix and without it booking will not work" %}

### Service Attributes

The DoS supports configuration of [Attributes](https://developer.nhs.uk/apis/dos-api/ccs_fields_v1.5_service_attribute.html) against a service which, in the case of appointment booking, informs system behvaiour to ensure the service is appropriately engaged with.
*NB: Not all system suppliers have implemented system behaviour based on attributes, therefore, the workflow (outlined below) cannot be guaranteed by adding this configuration to the DoS.*

The attribute used for apointment booking is entitled '**requirebooking**' and is of a boolean data type (TRUE/FALSE).

If this attribute is assigned to a service it means a referral cannot be made unless an appointment has been booked. 

#### Configuring DoS
1. Find the service you wish to add the Attribute to
2. On the 'Service Attributes' tab, click the pencil icon to edit 
<img src="_pages/deployment/toolkit/img/DoS_attribute_Add.png#1">
3. Select the Attribute option, *Service Attribute* - '**requirebooking**' and *Value* - '**TRUE**' 
<img src="_pages/deployment/toolkit/img/DoS_attribute_Configure.png">
4. Click the green 'plus' symbol and then click 'Save' 
<img src="_pages/deployment/toolkit/img/DoS_attribute_Save.png">
5. You will return to the Service Attributes tab and see the addition listed
<img src="_pages/deployment/toolkit/img/DoS_attribute_Added.png">
