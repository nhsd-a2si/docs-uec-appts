---
title: GP Connect - Key Requirements
sidebar: gpc_sidebar
keywords: specification
permalink: gpc_requirement.html
toc: false
folder: functional_spec
---

For UEC GP Connect consuming system there are the following key requirments:

* The appointment consumer (for example a 111/IUC system):
  * MUST be able to retreive the SDS record pointer (e.g. ASID or ODS code) from the endpoint details returned from the DoS
  * MUST be able to identify the ODS code for the patients registered GP Practice from the PDS
  * MUST be able to identify the patients preferred GP Practice location from the PDS (where present)
  * MUST clearly indicate to users a patients preferred GP Practice location where this information is available
  * MUST ensure that the booking functionality invoked is compliant with the national standards when a booking endpoint is returned
  * MUST ensure that if no booking endpoint is returned by the relvant DoS API call that any proprietary booking mechanisms are then tried and still work
  * MUST store and make accessible appropriate data to allow reporting on the metrics identified in the reporting specification <a href="fs_reporting.html" target="_blank">here</a>
