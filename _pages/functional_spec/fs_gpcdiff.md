---
title: Differences from GP Connect
sidebar: overview_sidebar
keywords: specification
permalink: fs_gpcdiff.html
toc: false
folder: functional_spec
---

{% include note-notpublished.html %}

Stage       | GP Connect           | Care Connect            | Difference         | Rational for change
Identify Patient | Use PDS to get a verified NHS Number DBS? | Use PDS to get a verified NHS Number DBS? | None | NA
Select Service | Get Registered GP Practice from PDS record | Use DoS to select a DoS profile | In GP Connect, this is done as part of the PDS lookup, in Care Connect, it's a separate call to the DOS, but one which is MOSTLY already taking place. Some change needed to the DOS to return the ASID. | GP Connect is all about booking appointments with a GP Practice, which is a known ODS code. We're looking beyond this to services as identified from the DOS, or by ASID. These can also be found from SDS using ODS code.
