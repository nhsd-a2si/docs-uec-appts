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

{% include infocard.html 
  title1="GP Connect" 
  content1_line1="Use PDS to get a verified NHS Number" 
  content1_line2="" 
  content1_line3=""  
  content1_line4="" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="Use PDS to get a verified NHS Number" 
  content2_line2="" 
  content2_line3=""  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="No Change" 
  content3_line2="" 
  content3_line3=""  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="NA" 
  content4_line2="" 
  content4_line3=""  
  content4_line4="" 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

## Select Service

{% include infocard.html 
  title1="GP Connect" 
  content1_line1="Get Registered GP Practice from PDS record" 
  content1_line2="" 
  content1_line3=""  
  content1_line4="" 
  content1_line5="" 
  content1_line6="" 
  content1_line7="" 
  
  title2="CareConnect" 
  content2_line1="Use DOS to select a DOS profile" 
  content2_line2="" 
  content2_line3=""  
  content2_line4="" 
  content2_line5="" 
  content2_line6="" 
  content2_line7="" 
  
  title3="Difference" 
  content3_line1="In GP Connect, this is done as part of the PDS lookup, in Care Connect, it is a separate call to the DOS, but one which is MOSTLY already taking place." 
  content3_line2="" 
  content3_line3="Some change needed to the DOS to return the ASID."  
  content3_line4="" 
  content3_line5="" 
  content3_line6="" 
  content3_line7="" 
  
  title4="Rationale for change" 
  content4_line1="GP Connect is all about booking appointments with a GP Practice, which is a known ODS code." 
  content4_line2="" 
  content4_line3="CareConnect is looking beyond this to services as identified from the DOS, or by ASID."  
  content4_line4="These can also be found from SDS using ODS code." 
  content4_line5="" 
  content4_line6="" 
  content4_line7="" 
%}

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
