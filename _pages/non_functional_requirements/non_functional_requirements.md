---
title: Non-Functional Requirements
toc: True
sidebar: overview_sidebar
permalink: non_functional_requirements.html
---

{% include callout.html content="Details of non-functional requirements (NFRs) that describe system attributes such as security, reliability, maintainability, scalability, and usability."%}

### Security 
Provider systems SHALL resist unauthorized, accidental or unintended usage and provide access only to legitimate users. 

Please refer to the [Security guidance](security_guidance.html) page for technical details. 

### Volume and performance 

####Volumetric 

Provider systems MUST meet the agreed volumetric performance targets. 

Please refer to the Volumetric guidance page for technical details. 

### Performance 

Provider systems MUST meet the agreed response time performance targets. 

 

Please refer to the Performance guidance page for technical details. 

 

### Capacity 

Provider systems MUST meet the agreed capacity requirements. 

 

### Scalability 

Provider systems SHALL be designed to accommodate increased volumes, workloads and users. 

 

### Availability 

Provider systems SHALL meet the agreed availability targets (service time and/or hours and planned downtime) as defined in the operational level agreement (OLA). 

 

### Recoverability 

Provider systems SHALL meet the agreed recoverability targets as documented in the Operational Level Agreement (OLA). 

 

### Audit & provenance 

Provider systems SHALL audit all API access and actions. 

 

Please refer to the cross organization audit and provenance page for technical details. 

 

### Maintainability 

Provider systems SHALL be designed to optimise the ability of maintenance personnel to revise or enhance it. 

 

## Serviceability 

Provider systems SHALL be designed so that technical support personnel are able to monitor and manage it in operation. 

 

### Data retention 

Provider systems SHALL retain data in line with existing relevant Informational Governance and data protection regulation. 

 

### Usability 

Provider and consumer systems SHOULD follow the ISO 13407 / ISO 9241-210 to explain a user-centred design process. 

 

### Accessibility 

Provider and consumer systems MUST maintain a compliance of minimum Double “A” of the WCAG 1.0 (or equivalent in WCAG 2.0) or, as stipulated by UK Government guidelines, for all user interfaces. Please see the Web Accessibility Initiative for more details. 

 

Please refer to the ‘UEC Technical Standards’ for details. 

 

### Deployment 

Provider systems SHALL release a new major version of their UEC Booking API alongside a previous major version, until such time as consumers have migrated to the new major version. 

 

Provider systems SHOULD release a new minor or patch version, replacing the previous minor or patch version. 

 

Provider systems SHALL be deployed with the provider APIs enabled by default. 

 

Provider systems MAY provide a mechanism for a data controller at an organisation to choose to globally disable/enable the provider APIs (that is, turn on/off the overall UEC Booking technical capability). 

{% include developer_journey.html %}
