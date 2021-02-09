---
title: Deployment Toolkit - Provider Resources
sidebar: deployment_sidebar
keywords: guidance
permalink: dep_provoverview.html
toc: false
folder: deployment
---

## Overview

The ability to control patient encounters has a significant benefit for service providers, whether managing who walks through the door or being able to directly refer to a service and provide the patient with accurate data on when they can expect to be dealt with. 

The UEC Booking Standard support these, and other related scenarios, for software suppliers to build booking functionality which is interoperable between their systems and, therefore, services. 

## Benefits

There are two elements to booking; providing slots and making a booking 

### Slot Providers

The ability to advertise capacity, through offering available slots, to other services should help with managing patient contacts and reduce periods of influx. Other services will know when there is capacity and direct a steady stream of patients. If capacity peaks, Slot Providers can reduce available slots to better manage service resource. 
If multiple services are run from the same physical building, these can be mapped separately and made available through service discovery tools such as the DoS (Directory of Services).

When a booking is made, the Standard includes sending supporting clinical information, allowing the service provider accepting the booking to have sight of the patient need before they arrive.

### Booking Consumers

When it has been identified a patient need to be sent to another service having the ability to view the capacity of that service and direct the patient there at an appropriate time helps maintain continuity of care. Moreover, the patient is less likely to wait as long to be seen, further supporting better patient experience of the care they receive. 

## Implementing Booking 

### Initiating a project 

There are numerous stages to enabling booking and the steps will differ depending on whether the Service Provider intends to offer booking availability (Provider) or request bookings (Consumer).

Firstly, the software used by the service must provide booking functionality which adheres to the UEC Booking Standard. A full list of conformant system suppliers can be found here <url>. 
  
Implementing booking within a service may take one of many routes to arrive at the point of wanting to engage a project. Whatever the path, one of the first things to establish is a project scope and team to support (including stakeholders) and the UEC Booking Team and related resources will be an invaluable to ensuring a successful go live. 

This is not an exhaustive plan of the stages of implementation but gives a flavour of some key considerations.  

### Technical 

Integrating systems with each other is always going to present some technical challenges and booking is no exception. There are numerous prerequisites to being able to enable the functionality listed on the path-to-live section <url>. Suppliers are likely to help with many of the steps listed but key roles around the service, such as DoS Leads, will need to be engaged. If the service is also established and using core services, many of the prerequisites are likely to already be met. 
  
One of the principal technical requirements will be the configuration of the supplier software to support the new process of bookings, whether Providing slot capacity or making bookings. 

### Process change 

Altering or extending the service business processes is a significant undertaking, involving Leads for the Service, DoS, Clinical, Training etc., mapping the scope and implications of the change. The new process will need documenting (Standard Operating Procedure - SOP) and signing off by all key stakeholders.
 
A system supplier Consultant will discuss potential workflow and outline options to meet the service need, designing and implement the necessary configuration. 

Testing of the implementation and configuration will be undertaken in an isolated setting in the Production environment, following a strictly outlined Test Plan. Once confirmed successful, a plan for Business Go-Live can be agreed, involving training staff, completing the project phase and communicating the service processes to the Business-as-usual teams.
