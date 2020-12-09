---
title: Glossary
keywords: abbreviations, definitions, glossaries, terms
tags: [getting_started]
sidebar: overview_sidebar
permalink: glossary.html
summary: "Glossary of terms used in the UEC Appointment booking standards"
toc: true
---

### Ambulance Service Trust 

Emergency medical services in the United Kingdom provide emergency care to people with acute illness or injury and are predominantly provided free at the point of use. 
The NHS commissions most emergency medical services through the 14 NHS organisations with ambulance responsibility across the UK.  As with other emergency services, the public normally access emergency medical services through one of the valid emergency telephone numbers. There are two aspects to this: -
•	Ambulance Control rooms
•	Ambulance Crews (including Air ambulance services)
Ambulance services Trusts may also provide NHS 111 call handling (see above) however they would be referred to as the NHS 111 service and Patient Transport Services (PTS) which are out of scope.

### Consumer

The IT system that is searching for and placing bookings on behalf of the patient 

### Discovery

This is an early phase in a project. Usually undertaken prior to main activities starting and will be used to define scope and design direction

### Distance-selling pharmacy (Internet Pharmacy)  

These are pharmacies which have, for example, an on-line presence.  The may dispense prescriptions which are delivered potentially within 24hrs.

### DoS

This stands for "Directory of Services"

### Emergency Department (A&E Type 1)  

A consultant led 24-hour service with full resuscitation facilities and designated accommodation for the reception of accident and emergency patients.

### Emergency Department (A&E Type 2)  

A consultant led single specialty accident and emergency service (e.g. ophthalmology, dental) with designated accommodation for the reception of patients.

### Emergency Care Centre, Minor Injuries Unit etc. (A&E Type 3)

These services go by many names: Urgent Care Centre, Minor Injury Unit, Primary Urgent Care Service, Co-located Primary Care Service, Primary Care Walk-in Centre to name some of them.  
The treatments offered and opening times all vary, they even vary if the services are both an Urgent Care Centre.  Which has led to confusion amount patients.   Services who meet (or can meet) the new service specification will be upgraded to Urgent Treatment Centres (see above).  

### ePrescribing pharmacy (Community Pharmacy)  

Community pharmacists were historically called chemists. Like GPs, community pharmacists are part of the NHS.  ePrescribing means that they are using EPS
There are several different types and sizes of community pharmacies, ranging from the large chains with shops on every High Street or in edge of town supermarkets, to small individually owned pharmacies in small communities, in the suburbs and often in deprived areas or rural settings.
The traditional role of the community pharmacist as the healthcare professional who dispenses prescriptions written by doctors has changed. In recent years community pharmacists have been developing clinical services in addition to the traditional dispensing role to allow better integration and team working with the rest of the NHS.
 
### ePrescribing pharmacy (Non-Community Pharmacy)

Other pharmacy services that provide e-prescribing but are not a community pharmacy.

### First of Type

Usually the first instance of a deployment using a new technology or standard. It is highly constrained and closely supported and monitored. This will then drive the next iteration of the standard

### FHIR

This stands for "Fast Healthcare Interoperability Resources"

### GP Connect

[Interoperability Standard for GP Practices](https://developer.nhs.uk/apis/gpconnect-1-2-7/){:target="_blank"}

### GP contract Enhanced Services (Primary Care)  

This is slightly different to GP networks and federations and is not the same as OOH which is commissioned in a different way.  An increasing number of GP practices are considering opening later each day (until 2000) and even on weekends.  GP contract Enhanced Services go by many names: extended hours, enhanced services.  These terms are often used interchangeably to describe practices offering more hours to patient’s.  

### GP networks and federations (Primary Care) 

An increasing number of GP practices are considering entering into collaborative arrangement with other practices. GP networks go by many names: federations, networks, collaborations, joint ventures, alliances. These terms are often used interchangeably to describe multiple practices coming together in some form of collaboration. 
 
Whether the desire to work more collaboratively or at greater scale is driven by the desire to share costs and resources (for instance, workforce or facilities) or as a vehicle to bid for enhanced services contracts, GP networks and federations are increasingly being viewed as a vital part of the future of general practice.

### GP Surgery (Primary Care)  

Patients own registered GP. 

### JWT
This stands for "JSON Web Token"

### NHS 111 Integrated Urgent Care (111 IUC)

The care settings below are part of an Integrate Urgent Care service / area

#### Clinical Assessment Service (CAS)

This is a telephone-only based service, where the 111 elements can warm-transfer patients to the CAS or they can take outbound telephone calls. The CAS is made up of a variety and/or combination of NHS professionals available to assess patients and advise on the next course of treatment. The CAS can be virtual where you have senior clinicians accessing the same ‘pool’ of calls from multiple locations, this will happen where the CAS is procured across boundaries. Note: Where referrals are made via an app/website they would be sent to a CAS.
Some of these services are currently in development and not formalised yet. For services that have a CAS the clinical advisor (from 111 above) is part of the CAS setting. For example, you can have GP, Advanced Nurse Practitioner, Mental Health Nurse, Pharmacist, Paramedic.  They do not use NHS Pathways or any decision support software, they will use professional knowledge and/or critical thinking.  

#### NHS 111 (111)

The NHS non-emergency phone number, access by dialling 111.  This is a telephone based service only, where face to face contact is needed it will be done with one of the care settings defined below such as UTC or OOH
Call handlers triage patients via a series of questions and algorithms using the NHS Pathways and produce a recommendation or instruction, known as a disposition, on what the next action should be.  
The 111 services will have two staff levels; health advisor and clinical advisor.  The health advisor does not have a clinical background and the clinical advisor will normally be a nurse.  

#### Out of Hours (OOH)

These services operate to provider cover for GP surgeries when they are unavailable to the patient” to broaden the situations where OOH GP might be used (e.g. to help manage capacity issues etc.) and not just when the surgery is closed.
There are few areas in Birmingham and London where the GPs taken on responsibilities themselves (and to add confusion) they may contract the GP OOH provider directly instead the CCG taking on such responsibility.  


### NHS Identity (**Strat**egic **Auth**entication)

The NHS Identity service provides a digital identity that can be consumed many times from a single logon. It can also be linked with every day devices to provide extra contextual information about that user (e.g. location, nearby services) and it can profile the characteristics of the owner(usual times of sign-on, services normally used, location, devices linked to the user).

For this booking standard, NHS Identity could validate credentials passed by the consuming system, and subject to this check, issue a short lived (1 hour) access token which the consuming system must include in an http Authorization header in all requests to the provider system.

### OAuth
[This is an Open Authentication Standard](https://oauth.net/){:target="_blank"}

### Open Beta

### PDS
This stands for "Patient Demographic Service"

### Pilot

The pilot phase of a project will usually involve a limited deployment in live service to gather feedback and establish feasibility

### POC
"**P**roof **o**f **C**oncept" - a prototype system that is developed to establish or demonstrate the utility of a new technology

### Private BETA

a typically non-live, constrained period of testing with a number of chosen suppliers to test out an immature standard

### Provider

The IT system that holds the appointments being searched for and booked into 

### RESTful

This is "**Re**presentational **St**ate Transfer" and refers to an API which uses the concept of resources, and http verbs to support CRUD (create, read, update and delete) type operations.

### SDS
This stands for "Spine Directory Service"

### SMSP
This stands for "Spine Mini Service Provider"

### SSP
This stands for "Spine Secure Proxy"

### Urgent Treatment Centre (UTC)

Urgent Treatment Centres are an initiative of the NHS Five Year Forward View.  They will be open 12 hours a day, seven days a week, and offer patients who do not need to go to A&E treatment by clinicians with access to blood tests, ECGs and X-rays.
 They will offer booked appointments to patients calling in to NHS 111 as well as walk-in patients.  They are formed of ‘upgrades’ of existing walk-in centres, minor injury units, urgent care centres, Type 3 & 4 A&E services, or similar services.  
Eventually there will be around 400 UTC’s in total. The first round identifies about 150 so the list is currently incomplete. As they are ‘upgrades’ of existing services then we will be collecting information on those other services and will be able to extrapolate across to the UTC world from that.  

### Walk-in Centres (A&E Type 4)  

The treatments offered and opening times all vary, they even vary if the services are both a Walk-in Centre.  Which has led to confusion amount patients.   Services who meet (or can meet) the new service specification will be upgraded to Urgent Treatment Centres (see above).  
