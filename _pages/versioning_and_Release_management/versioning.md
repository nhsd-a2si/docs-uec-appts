---
title: Versioning
sidebar: overview_sidebar
keywords: Versioning
permalink: versioning.html
toc: false
---

## Versioning

This page details how  versioning is implemented within the NHS Booking Standard


### FHIR
The current version of the NHS Booking Standard is aligned to [FHIR R3](
http://hl7.org/fhir/STU3/index.html), however, from release 2.0.0 the standard has been aligned to [FHIR R4](http://hl7.org/fhir/R4/).


### FHIR UK Core
Whilst [FHIR R4 ](http://hl7.org/fhir/R4/) is the most current iteration of FHIR, from release 2.0.0 the NHS Booking Standard will aligned with the [UK FHIR Core](https://digital.nhs.uk/services/fhir-uk-core) releases.

### Version

#### Major version {#major_version_heading}
TBC


#### Minor version {#minor_version_heading}
TBC



### Provider Requirements
Providers MUST support multiple versions of the NHS Booking Standard.  

Providers MUST support a minimum of 2 NHS Booking Standard versions, this support MUST when appropriate include support for multiple [Major Versions](##major_version_heading) iterations.

Providers MUST specify their version support in their [Capability Statement](TBC)


### Consumer Requirements
Consumers MUST use the Provider's [Capability Statement](TBC) to establish.......
