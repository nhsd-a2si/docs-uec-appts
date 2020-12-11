---
title: Deployment Toolkit - DoS Lead Resources
sidebar: deployment_sidebar
keywords: guidance
permalink: dep_dosoverview.html
toc: false
folder: deployment
---

## What do I need to know?


## Why do I need to be involved?


## How can I get involved?


## Configuring the DoS for Appointment Booking

### Endpoints 

### Service Attributes

The DoS supports configuration of [Attributes](https://developer.nhs.uk/apis/dos-api/ccs_fields_v1.5_service_attribute.html) against a service which, in the case of appointment booking, informs system behvaiour to ensure the service is appropriately engaged with.
*NB: Not all system supplier have implemented system behaviour based on attributes.*

The attribute used for apointment booking is entitled 'requirebooking' and is of a boolean data type (TRUE/FALSE).

If this attribute is assigned to a service it means a referral cannot be made unless an appointment has been booked. 

#### Configuring DoS 
1. Find the service you wish to add the Attribute to
2. On the 'Service Attributes' tab, click the pencil icon to edit 
<img src="_pages/deployment/toolkit/img/DoS_attribute_Add.png">
3. Select the Attribute option, Service Attibute - 'requirebooking' and Value - 'TRUE' 
<img src="_pages/deployment/toolkit/img/DoS_attribute_Configure.png">
4. Click the green 'plus' symbol and click 'Save' 
<img src="_pages/deployment/toolkit/img/DoS_attribute_Save.png">
5. You will return to the Service Attributes tab and see the addition listed
<img src="_pages/deployment/toolkit/img/DoS_attribute_Added.png">




