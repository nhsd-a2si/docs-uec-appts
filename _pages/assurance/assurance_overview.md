---
title: Overview of Assurance Process
toc: True
sidebar: overview_sidebar
permalink: assurance_overview.html
summary: "Overview of the assurance processes involved in developing and deploying a solution"
---
{% include note-notpublished.html %}

## Assurance principles 
High-level design principles related to the assurance processes 
* assurance should be lightweight but appropriate 
* testing should be automated where possible to establish technical conformance 
* a level of self-certified solution assurance will be made available to organisations deploying the APIs 
* all artefacts related to assurance and testing should be made available as part of the ecosystem (public domain) prior to engaging in a formal NHS Digital assurance process 
* a set of evidence based around self-assurance activities will speed up the assurance process 


<div class="mxgraph" style="max-width:100%;border:1px solid transparent;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;target&quot;:&quot;blank&quot;,&quot;nav&quot;:true,&quot;resize&quot;:true,&quot;toolbar&quot;:&quot;zoom lightbox&quot;,&quot;xml&quot;:&quot;&lt;mxfile modified=\&quot;2019-04-15T15:25:13.504Z\&quot; host=\&quot;www.draw.io\&quot; agent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/8.8.0 Chrome/61.0.3163.100 Electron/2.0.2 Safari/537.36\&quot; etag=\&quot;VrLV5bFS8c98vIu1mcbU\&quot; version=\&quot;10.6.2\&quot; type=\&quot;device\&quot;&gt;&lt;diagram id=\&quot;PTt-hyj0bQr8gjIvqhx4\&quot; name=\&quot;Page-1\&quot;&gt;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&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>



## Testing Assets 
TBC - Details of POC? 

## Test Environments 
TBC - Details of POC?
