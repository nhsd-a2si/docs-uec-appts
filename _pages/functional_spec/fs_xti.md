---
title: Transactional Integrity
sidebar: overview_sidebar
keywords: specification
permalink: fs_xti.html
toc: false
folder: functional_spec
---

For more in depth discussion on this subject please see the HL7 R4 page providing guidance on [restful API's](https://www.hl7.org/fhir/http.html){:target="_blank"}

## General Principles

When a booking provider is processing create and update operations, there is no general-purpose method to make merging with existing content or altering the content by business rules safe or predictable. Even though the resource may be retrieved by the consumer systems through a read interaction prior to attempting an update for example, the resource on the provider may be different. These differences may arise for several reasons:

* The provider merged updated content with existing content
* The provider applied business rules and altered the content
* The provider does not fully support all the features or possible values of the resource

This is why all updates (such as when performing a cancel operation) **must** be version aware. However, to further mitigate the problems of inconsistencies in the content between client and server, the following rules can be applied:

* The provider *must* support a read interaction for any resource it accepts update interactions on
* Before updating, the consumer *must* read the latest version of the resource
* The consumer applies the changes it wants to the resource, leaving other information intact
* The consumer writes the result back as an update interaction, and is able to handle a 409 (conflict) or 412 (precondition failed) response (usually by trying again)
* If consumers follow this pattern, then information from other systems that they do not understand will be maintained through the update.

Both consumer and provider systems *should* clearly document how transaction integrity is handled by specifying in the documentation inside the [CapabilityStatement](uec_capability.html){:target="_blank"}.
