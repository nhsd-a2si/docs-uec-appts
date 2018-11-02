---
title: Differences from GP Connect
sidebar: overview_sidebar
keywords: specification
permalink: fs_gpcdiff.html
toc: false
folder: functional_spec
---

{% include note-notpublished.html %}

## Identify Patient

GP Connect | CareConnect | Difference | Rationale for Change
-----------|-------------|------------|---------
Use PDS to get a verified NHS Number | Use PDS to get a verified NHS Number | No Change | NA

## Select Service

GP Connect | CareConnect | Difference | Rationale for Change
-----------|-------------|------------|---------
Get Registered GP Practice from PDS record | Use DoS to select a service | n GP Connect, this is done as part of the PDS lookup, in Care Connect, it's a separate call to the DOS, but one which is MOSTLY already taking place. Some change needed to the DOS to return the ASID. | GP Connect is all about booking appointments with a GP Practice, which is a known ODS code. We're looking beyond this to services as identified from the DOS, or by ASID. These can also be found from SDS using ODS code.

## Calls via SSP

{% include infocard.html title1="GP Connect" content_line1="Target URL is concatenated onto SSP URL" content_line2="http headers are as follows:" content_line3="Ssp-TraceID"  content_line4="Ssp-From" content_line5="Ssp-To" content_line6="Ssp-InteractionID" content_line7="N/A" title2="CareConnect" content2="http headers are as follows" %}
