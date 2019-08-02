---
title: Proof of Concept / Demonstrator
sidebar: poc_sidebar
keywords: guidance
permalink: implementation_poc.html
toc: false
Summary: "Summary of POC goes here"
folder: implementation
---

## Scope
The proof of concept demonstrates the appointment booking workflow, specifically, how consumers can locate endpoints and retrieve appointment slots from providers. It is a technical demonstration of how the APIs can support the appointment booking workflow and not a full end to end solution.

## Objectives
The following lists the key objectives of the proof of concept demonstrator:

* Demonstrate what information needs to be added to pathways DoS to identify the services that expose an appointment booking capability
* Demonstrate what endpoint information needs to be added to SDS and which identifier should be used for nhsMhs
* Handle volatility of DoS service information against need for stable endpoint in SDS
* Provide example LDAP queries for retrieving endpoint data from SDS
* Initial demonstration of FHIR appointment slot retrieval API
* Deomonstrate how queries for slots where more than one organisations slots are stored on one FHIR server should be constructed

## Use Cases/User Stories
**As a** user of a 111 system

**I want** to see which services accept appointments

**So that** I can have a discussion with the patient before choosing a service

## Workflow
!! workflow diagram here !!

## Architecture

### Interactions
* Pathways DoS
  * CheckCapacitySummary()
  * FindServiceByID() 
* SDS
  * LDAP Query - Look up ASID
  * LDAP Query - Look up nhsMhs
* Proxy
  * GET appointment slots
* Solution Requirements
  * Hosting
  
## Solution Design
!! Sequence Diagram Here !!
