---
title: Versioning
sidebar: overview_sidebar
keywords: Versioning
permalink: versioning.html
toc: false
---

## Introduction

This page details how  multiple versions of the the NHS Booking Standard will be managed and published.

## Lifecycle
>TODO - Agree standard publication lifecycle with team



### FHIR
The current version of the NHS Booking Standard [0.1.16 ALPHA](release_notes.html#0116-alpha) is aligned to [FHIR R3](
http://hl7.org/fhir/STU3/index.html), however, from release 1.0.0 the standard will been aligned to [FHIR UK Core](#fhir_uk_core).


### FHIR UK Core {#fhir_uk_core}

[FHIR UK Core](https://digital.nhs.uk/services/fhir-uk-core) is aligned with [FHIR R4 ](http://hl7.org/fhir/R4/) the most current iteration of FHIR.  Please refer to the [FHIR UK Core](https://digital.nhs.uk/services/fhir-uk-core) site for more information.


### Versioning

The NHS Booking standard will follow [Semantic Versioning](https://semver.org/), i.e. a three-part version number consisting of major, minor and patch versions.  There will also be support for pre-releases versioning by use of ALPHA and BETA extensions

Full details can be found at the [Semantic Versioning](https://semver.org/) site, however, here are the key points.

#### Major version {#major_version_heading}
The major version is increment when an incompatible changes is made aka non backward compatible.


#### Minor version {#minor_version_heading}
The minor version increments when changes are made in a backwards compatible manner.


#### Patch version {#patch_version_heading}
The patch version is incremented when backwards compatible bug fixes are implemented in the standard.

#### Extensions {#extension_version_heading}
The extensions ALPHA and BETA will be used to indicate the maturity of a pre-release version of the standard.



### Provider Requirements
Providers MUST support multiple versions of the NHS Booking Standard.  

Providers MUST support a minimum of 2 NHS Booking Standard versions, this support MUST when appropriate include support for multiple [Major Version](#major_version_heading) iterations.

Providers MUST specify their version support in their [Capability Statement](TBC)

>TODO - Need Capability URL from IOPS once it has been published


### Consumer Requirements
Consumers MUST use the Provider's [Capability Statement](TBC) to establish.......
