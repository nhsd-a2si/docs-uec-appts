---
title: Deployment Toolkit - Test Plan
sidebar: deployment_sidebar
keywords: guidance
permalink: dep_testplan.html
toc: false
folder: deployment
---

## Test Plans Overview

Planning is essential to successful testing when numerous parties are involved. The test needs careful orchestration and for each of the actors involved to know the plan and their roles and resposibilities. 

This section will outline the precursive steps, the actors involved and provide an example of a typcial Test Run. 

### Types of Test

In the process of building a solution a supplier will be involved in several [phases of testing](https://developer.nhs.uk/apis/uec-appointments/dep_testtesting.html), at different maturity levels and environments - 

* Like-Live (INT)
* Provider (Production)
* Business Go Live 

Test Plans must be adopted for testing on any of these environment. However, there are circumstances where testing could occur on INT in isolation, without the paraphernalia of a full Test Plan, for example, when a supplier is initially deploying and configuring their solution and testing against those already assured. 

## Roles & Responsibilities 

The actors from the numerous parties must know what is expected of them during a planned test. This ensures the test has the best chance of success and valuable time is not wasted through trial-and-error attempts.

### Actors 
There is a requirement to cover these core roles for any level of arranged test. There may be others involved or some individuals may perform multiple roles.  

|Organisation|Expertise|Individual Role|
|:---|:---|:---|
|NHS Digital|UEC Booking|Delivery Manager|
|NHS England (regional)|DoS|Configuration Lead|
|Supplier (Software solution*)|Consumer (software)|Technical Support|
|Service Provider (e.g. 111 Provider)|Consumer|Project Lead|
|Service Provider (e.g. 111 Provider)|Consumer|System User|
|Supplier (Software solution*)|Provider (software)|Technical Support|
|Service Provider (e.g. ED)|Provider|Project Lead|
|Service Provider (e.g. ED)|Provider|System User|

\* Potentially the same organisation. Some suppliers have developed both Booking Provider and Consumer functionality.

## Prerequisites 

### Both Service Systems (Provider & Consumer)
* Certs obtained and installed – Provider & Consumer
* Connected to INT – Provider & Consumer
    * ASID supplied for connecting system/service 
    *	Interactions for ASID added to SDS
* Software upgraded to appropriate version 
* Software configured to support functionality 
* Users with appropriate system access and knowledge to perform and verify functionality, including 
    * Smartcard access & roles
    * Workstations being used adhere to the WES (Warranted Environment Specification)?  See link https://digital.nhs.uk/services/spine/spine-technical-information-warranted-environment-specification-wes 
    
### Provider 
*	Confirm Booking endpoint is running and accessible (firewalls updated)
*	Confirm Referral endpoint is running and accessible (firewalls updated)
*	Slots added to Schedule accessible via DoS

### Consumer
*	Access to DoS or Service Discovery Tool 
*	Local configuration of firewalls/ports to make requests of spine services (SSP/SDS)
*  Identify PDS traceable patient

### DoS
*	Service for Provider System configured 
*	Scheduling Endpoint configured 
*	Referral Endpoint configured 
*	Optional ‘requirebooking’ attribute added and set to TRUE
*	Note following supported by service to assist Consumer
    * Age range
    * DX code
    * Opening Times

## Test Plan Management 

Pre test - 
* Arrange the meeting date agreed by all
* Provide contact details for - 
    * DoS Lead
    * Software Supplier - Product Lead
    * Consumer service - Project Lead
    * Provider service - Project Lead
* Share Test Plan with all key stakeholders, including
    * DoS Service(s) to be utilised
* Verify all parties have completed the prerequisites

Post test - 
* Brief review of test, stating sucess or failure 
* Document actions and next steps

## Test Run 
The steps below outline a typical test run but the agreed Test Plan should be adhered to. 

The recording of the session as a whole or snapshot of screens and log data should be taken where appropriate to verify functionality (especially, if being submitted for the SCAL) or record error data for later investigation. 

Steps in the test -  
*	Consumer system performs triage/consultation resulting in appropriate outcome code to make request of DoS Service
*  Perform Service Discovery (DoS or alternative)
*	Selects configured DoS service
*	Selects option to initiate request for Slots 
*	View available slots 
    *	Indicate where no slots are available to user
*  Confirm slot data offered by the Provider is reflected on the Consumer system
*	Verify slots outside of outcome code timeframe adhere to user type (Clinical/Non-clinical) requirements
*	Select slot 
*	Request booking 
    * Indication Booking has been made
*  Confirm booking exists in the Provider system
*  Send referral 
*	Verify referral (supporting document) exists and marrys up to booking (Provider System) 
*	Triage/consultation complete 
* SMS transferred to patient

Additional test within Consultation 
*  Verify user is able to change the booking 
*	Verify user is able to cancel the booking

After triage/consultation 
*	User is able to cancel booking outside of triage/consultation window

## Test Plan Resources 

Here you will find some links to testing files that will be useful for **providers** looking to perform end to end testing prior to go-live:

1. <a href="_pages/deployment/toolkit/files/111_to_GP_Hub-Operational_Test_Plan_v2.xlsx" download>111 to GP Hub, operational test plan (excel file)</a>
2. <a href="_pages/deployment/toolkit/files/111_to_Registered_GP-Operational_Test_Plan_v3.xlsx" download>111 to registered GP Practice, operational test plan (excel file) (excel file)</a>
3. <a href="_pages/deployment/toolkit/files/111_to_UTC_Care_Connect-Operational_Test_Plan.xlsx" download>111 to UTC Care Connect, operational test plan (excel file)</a>

Here you will find some links to testing files that will be useful for **suppliers** looking to perform product assurance:
1. <a href="_pages/deployment/toolkit/files/Care_Connect_Consumer_Assurance_Test_Scripts.xlsx" download>Care Connect <b>Consumer</b> Assurance Test Script (excel file)</a>
2. <a href="_pages/deployment/toolkit/files/Care_Connect_Provider_Assurance_Test_Scripts.xlsx" download>Care Connect <b>Provider</b> Assurance Test Script (excel file)</a>



