---
title: Supplier Assurance Prerequisites and Requirements
toc: True
sidebar: overview_sidebar
permalink: assurance_supplier.html
summary: "Details of what activities form the basis of assurance for a supplier involved in developing and deploying a solution"
---

## Technical accreditation 
Consuming supplier systems **MUST** have been tested and accredited to establish baseline Spine connectivity prerequisites:
* N3 connectivity / ASID / PKI Certificate 
* Personal Demographic Service (PDS) integration 
* Spine Directory Service (SDS) integration 

## Technical conformance 
Supplier systems SHALL be tested for technical conformance of the following before they can be listed on the conformance catalog:
* Spine Directory Service (SDS)
* Spine Security Proxy (SSP) integration
* CareConnect FHIR Appointment API standards

## Solution assurance 
Solution assurance ensures that the correct level of safety, governance, and security has been accepted, understood and signed off by the organisation providing the APIs. 

 {% include important.html content="Important: Suppliers are responsible for their own testing and the clinical safety of the delivered system. Supplier-authored tests must be traceable back to the published specification." %}

## Witness testing 
Supplier systems **SHALL** undergo witness testing to validate conformance to requirements which can’t easily be automated. 
