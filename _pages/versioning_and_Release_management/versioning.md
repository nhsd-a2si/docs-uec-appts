---
title: Versioning
sidebar: overview_sidebar
keywords: Versioning
permalink: versioning.html
toc: true
summary: How multiple versions of the the NHS Booking Standard will be managed and published.
---

## Introduction
This page details the NHS Booking Standard approach to versioning and release management.  


## Lifecycle
This diagram shows the NHS Booking Standards lifecycle.

<img src="_pages/versioning_and_Release_management/img/NHS_ Booking_Lifecycle_Process.png">

### Discovery and Elaboration
- New Requirement/s Emerge
- Requirement Elaborated

### Uplift
- Standard Uplifted
- Articfacts Uplifted
  - Swagger - Interface Definition
  - Testing Toolkit
  - SCAL
- Booking Standard Site Uplifted
- FHIR NHS Booking API Uplifted

### Review 
- Uplift Reviewed

### Versioning 
- Standard Version Incremented
- Standard Marked As Pre-release

### Publishing (Pre-Release)
- Booking Standard Published
- FHIR NHS Booking API Published
- Artefacts Published  

### External Review
- Suppliers Engaged
- Supplier Feedback
  - Optional - Back to Discovery and Elaboration

### Publishing (Alpha/Beta/Public)
  - Booking Standard Published
  - FHIR NHS Booking API Published
  - Artefacts Published  


### Versioning

The NHS Booking standard will follow [Semantic Versioning](https://semver.org/), i.e. a three-part version number consisting of major, minor and patch versions.  There will also be support for pre-releases versioning by use of ALPHA and BETA extensions

Full details can be found at the [Semantic Versioning](https://semver.org/) site, however, here are the key points.

#### Major version {#major_version_heading}
The major version is incremented when an incompatible changes is made, i.e. a non backwards compatible change.


#### Minor version {#minor_version_heading}
The minor version increments when changes are made in a backwards compatible manner.


#### Patch version {#patch_version_heading}
The patch version is incremented when backwards compatible bug fixes are implemented in the standard.

#### Extensions {#extension_version_heading}
The extensions ALPHA and BETA will be used to indicate the maturity of a pre-release version of the standard.


#### Associated technical artefacts
The following artefacts will be released as part standard, taking the same version number as the specification.

>TODO - Need correct URLS for these

- [Interactive Swagger API documentation](https://app.swaggerhub.com/apis/Sphinx/CareConnect-Alpha/2.0.0)
- [Automated test toolkit](sims_install.html)


### FHIR
The current version of the NHS Booking Standard [0.1.16 ALPHA](release_notes.html#0116-alpha) is aligned to [FHIR R3](
http://hl7.org/fhir/STU3/index.html), however, from release 2.0.0 the standard will been aligned to [FHIR UK Core](#fhir_uk_core), which in turn is based on [FHIR R4 ](http://hl7.org/fhir/R4/)


### Provider Requirements
- Providers MUST support multiple versions of the NHS Booking Standard.  

- Providers MUST support a minimum of 2 NHS Booking Standard versions, this support MUST when appropriate include support for multiple [Major Version](#major_version_heading) iterations.

- Providers MUST specify their version support in their [Capability Statement](TBC)

>TODO - Need Capability URL from IOPS once it has been published


### Consumer Requirements
- Consumers MUST use the Provider's [Capability Statement](TBC) to establish the version/s of the NHS Booking Standard supported by the Provider.
