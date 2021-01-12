---
title: Deployment Toolkit - Test Plan
sidebar: deployment_sidebar
keywords: guidance
permalink: dep_testplan.html
toc: false
folder: deployment
---

## Test Plans Overview

Planning is essential to successful testing when numerous parties are involved, especially when prior configuration is required outside of the scope of the test. The co-ordination needs careful orchestration and for each of the actors involved to know their roles and resposibilities. 

This section will outline the precurive steps, the actors and the provide an example of a typcial test run. 

### Types of Test

In the process of building a solution a supplier will be involved in several rounds of testing, at different maturity levels and environments. 

* Like-Live (INT)
* Provider (Live)
* Technical Live

## Roles & Responsibilities 

The actors from the numerous parties must know what is expected of them during a planned test. This ensure the test has the best chance of success and valuable time is not wasted through trial-and-error attempts.

### Actors 
There may be others involved but there is a requirement to cover these core roles for any level of arranged test. 

* NHS Digital - UEC Booking - Delivery Manager
* NHS Digital - DoS - Configuration Lead 
* Supplier - Consumer - Technical
* Service Provider - Consumer (software) - Project Lead
* Service Provider - Consumer (software) - User 
* Supplier - Provider - Technical
* Service Provider - Provider (software) - Project Lead
* Service Provider - Provider (software) - User 

## Prerequisites 

### All Supplier Systems
* Certs obtained and installed – Provider & Consumer
* Connected to INT – Provider & Consumer
*	ASID supplied for connecting system/service 
*	Interactions for ASID added to SDS
* Identify PDS traceable patient

### Provider 
*	Confirm Booking endpoint is running and accessible (firewalls updated)
*	Confirm Referral endpoint is running and accessible (firewalls updated)
*	Slots added to Schedule accessible via DoS

### Consumer
*	Access to DoS 
*	Local configuration to make requests of Provider endpoints
    *	Scheduling
    * Referral 

### DoS
*	Service for Provider System configured 
*	Scheduling Endpoint configured 
*	ITK Endpoint configured 
*	Optional ‘requirebooking’ attribute added and set to TRUE
*	Note following supported by service to assist Consumer
    * Age range
    * DX code
    * Opening Times

## Test Plan Management 
* Arrange the meeting 
* Ensure everyone is ready 

## Test Run 
*	Consumer system performs triage/consultation resulting in appropriate outcome code to make request of DoS Service
*	Views DoS services
*	Selects configured DoS service 
*	Selects option to initiate request for Slots 
*	View available slots 
    *	Indicate where no slots are available to user
*	Slots outside of outcome code timeframe adhere to user type (Clinical/Non-clinical) requirements
*	Select Slot 
*	Request Booking 
    * Indication Booking has been made
* User is able to Rebook 
*	User is able to Cancel booking 
*	Referral is made 
*	Triage/consultation complete 
* SMS transferred to patient

After triage/consultation 
*	User is able to cancel booking outside of triage/consultation window


## Test Plan Resources 

Here you will find some links to testing files that will be useful for **providers** looking to perform end to end testing prior to go-live:
<p>
<a href="_pages/deployment/toolkit/files/111_to_GP_Hub-Operational_Test_Plan_v2.xlsx" download>111 to GP Hub, operational test plan (excel file)</a>
<p>
<a href="_pages/deployment/toolkit/files/111_to_Registered_GP-Operational_Test_Plan_v3.xlsx" download>111 to registered GP Practice, operational test plan (excel file) (excel file)</a>
<p>
<a href="_pages/deployment/toolkit/files/111_to_UTC_Care_Connect-Operational_Test_Plan.xlsx" download>111 to UTC Care Connect, operational test plan (excel file)</a>

Here you will find some links to testing files that will be useful for **suppliers** looking to perform product assurance:
<p>
<a href="_pages/deployment/toolkit/files/Care_Connect_Consumer_Assurance_Test_Scripts.xlsx" download>Care Connect <b>Consumer</b> Assurance Test Script (excel file)</a>
<p>
<a href="_pages/deployment/toolkit/files/Care_Connect_Provider_Assurance_Test_Scripts.xlsx" download>Care Connect <b>Provider</b> Assurance Test Script (excel file)</a>



