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

{% include infocard.html 
  title1="GP Connect" 
  content1_line1="Target URL is concatenated onto SSP URL" 
  content1_line2="http headers are as follows:" 
  content1_line3="<i>Ssp-TraceID</i>"  
  content1_line4="<i>Ssp-From</i>" 
  content1_line5="<i>Ssp-To</i>" 
  content1_line6="<i>Ssp-InteractionID</i>" 
  content1_line7="<i>N/A</i>" 
  
  title2="CareConnect" 
  content2_line1="Target URL is concatenated onto SSP URL" 
  content2_line2="http headers are as follows:" 
  content2_line3="<i>Ssp-TraceID = a UUID</i>"  
  content2_line4="<i>Ssp-From = Client system ASID</i>" 
  content2_line5="<i>Ssp-To = Server ASID</i>" 
  content2_line6="<i>Ssp-InteractionID = Interaction ID from SDS specific to the call being made.</i>" 
  content2_line7="<i>Authorization</i>" 
  
  title3="Difference" 
  content3_line1="Calls via SSP: No change" 
  content3_line2="Interaction ID's are different in http headers" 
  content3_line3="<i>Ssp-TraceID: no change</i>"  
  content3_line4="<i>Ssp-From: no change</i>" 
  content3_line5="<i>Ssp-To: no change</i>" 
  content3_line6="<i>Ssp-InteractionID: specific set for GP Connect and another for CareConnect</i>" 
  content3_line7="<i>Authorization: Uses JWT token in an Authorisation http header (not used by SSP)</i>" 
  
  title4="Rationale for change" 
  content4_line1="Target URL is concatenated onto SSP URL" 
  content4_line2="The Interaction IDs are different to allow them to be individually authorised, and to permit different endpoints to be offered per interaction. If there were no differences elsewhere they COULD be the same." 
  content4_line3=""  
  content4_line4="" 
  content4_line5="SSP Could inspect the Authorization header and make decisions based on that (not currently in scope)." 
  content4_line6="" 
  content4_line7="" 
%}

## NextOne

{% include infocard.html 
  title1="GP Connect" 
  content1_line1="" 
  content1_line2="" 
  content1_line3="<i></i>"  
  content1_line4="<i></i>" 
  content1_line5="<i></i>" 
  content1_line6="<i></i>" 
  content1_line7="<i></i>" 
  
  title2="CareConnect" 
  content2_line1="L" 
  content2_line2="" 
  content2_line3="<i></i>"  
  content2_line4="<i></i>" 
  content2_line5="<i></i>" 
  content2_line6="<i></i>" 
  content2_line7="<i></i>" 
  
  title3="Difference" 
  content3_line1="" 
  content3_line2="" 
  content3_line3="<i></i>"  
  content3_line4="<i></i>" 
  content3_line5="<i></i>" 
  content3_line6="<i></i>" 
  content3_line7="<i></i>" 
  
  title4="Rationale for change" 
  content4_line1="" 
  content4_line2="" 
  content4_line3=""  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}
