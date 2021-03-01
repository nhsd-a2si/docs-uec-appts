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

* The provider **must** support a read interaction for any resource it accepts update interactions on
* Before updating, the consumer **must** read the latest version of the resource
* The consumer applies the changes it wants to the resource, leaving other information intact
* The consumer writes the result back as an update interaction, and is able to handle a 409 (conflict) or 412 (precondition failed) response (usually by trying again)
If consumers follow this pattern, then information from other systems that they do not understand will be maintained through the update.

Both consumer and provider systems **should** clearly document how transaction integrity is handled by specifying in the documentation inside the [CapabilityStatement](uec_capability.html){:target="_blank"}.

## Handling a special case - duplicates arising from retrys

In order to further assist in maintaining the integrity of transactions some custom headers are available. It is expected that two of the custom headers defined in the FHIR standard are used for this purpose: 

* ```X-Request-ID``` is a unique id to for the request/response assigned by either client or server. Request: assigned by the client. Response: assigned by the server
* ```X-Correlation-ID``` a client assigned request id echoed back in the response

Additionally there is a specific scenario that might arise that needs to be mitigated, this is when a provider accepts a booking via a POST and the ```200``` OK response is not received by the Consumer. In this scenario the consumer system is entitled to re-try the POST request until the OK response is recieved or the attempt is abandoned. Under these circumstances, this *might* lead to duplicate appointments being made on the Provider system. Therefore the ```X-Request-ID``` and ```X-Correlation-ID``` can be used to prevent this.

When the consumer makes a request it will assign an ```X-request-ID``` to the header. When the provider system recieves the request, it will retrieve the ```X-request-ID``` and set the ```X-Correlation-ID``` to that value (to echo back). It will then generate an ```X-Request-ID``` of its own and both X-Headers will be assigned to the response.

The following diagram illustrates this:

<div class="mxgraph" style="max-width:100%;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;Electron\&quot; modified=\&quot;2021-02-18T13:27:34.802Z\&quot; agent=\&quot;5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/13.2.2 Chrome/83.0.4103.100 Electron/9.0.3 Safari/537.36\&quot; etag=\&quot;Ap-DLTcFiW8eZRy4fUQ4\&quot; version=\&quot;13.2.2\&quot; type=\&quot;device\&quot;&gt;&lt;diagram id=\&quot;ovqSKI4eBZbKsl1YpQPm\&quot; name=\&quot;Page-1\&quot;&gt;7VlLd9o6EP41LOHY8gN7mZL2pj2np5xm0XQprDGokS1XlgP011e2JcAPAiQQ2nvvCusbaSzNfPOwGDiTZPWPwNniMyfABsgiq4FzO0DItu2x+imRtUas0K2RuaBEY1vgnv4CM1GjBSWQNyZKzpmkWROMeJpCJBsYFoIvm9NizppvzfAcOsB9hFkX/UaJXGjU99yt4A7ofGFebfthLUmwma2Pki8w4csdyHk/cCaCc1k/JasJsNJ8xjD1ug97pJudCUjlMQt+gH0jvj66n5K78Udnvf5Bp2iotTxhVugTD5DPlL53MVdq1a7lWtvC/1lwIxjmladu1ATHylZboXqa699Ky8wAE57mRQLCCNQ+Z+3JCqvfamDU2AASvEgJlMexlXi5oBLuMxyV0qXin8IWMmFa/ARCUuXIG0bnqcISSkip6F1MGZtwxkWl1CEeBMRVeC4Ff4QdSYBmju9vNlIqhNVe49sbl6poAJ6AFGs1RS9wNQl0HAR6uNzllMYWO3QaG/JgzeP5RvPW0+pBO/sExzs9jm+ZWxE2Kx8zwSPI88Mmn+HocV456UshGU1B4y2LxzH4UdRncTIOZ5Z1Hos76KDJvT6TO/alTO7ujbVOJBwbfAj1Bd8UrxnHZG9Y9UXgHt+nXMLLHU+wePyiVlFZOsEaWd6ZfBs2fYv8rnNd1ONc+2LOHe91bp7h9OW+vBBFjJbCAF/hZwF5qfEOMAGR79CkOJio9+f0mTgCMcBoxOWirBHKadUmRqPuqoeh3uvwI6mPqCQ4KSlZHymlSjykpCxuWnBwmwqr/XSw9FiHwwHrksMglj2VSPLsMmFgW8eGgXupMAjOn+P6G4yp4E+qNRQnUfI1/US7iAUR9BexWeC53pmKmPLon9Y4hP+1xsG9fudgFP/fOpw9Z/re1VsH+/UfYc8X+WZle6t+Is/UJx/8qxoK1N9QdDdwVIvR2uvDcMKFAIYl5emZe5s+4x7Fihce7W/sntzw6t2TjY4vrjGD1U15w6WsASnRj7cRw3lOo6ZJ63ppLrD8bmUlGIK4t7L6UQCzeGNxIJ37soP23q2bPeY0WE39p6b6PhPrN0w5rTKWdidqdUrI8Zoqcl6ICPSq3XuylqJ2/e8okljMQXYUVR7fHPsVJDjhauatSQArKh+0vvL5e1WbPT26XekIrwZrM0iVPR7qIm7ZBqhXItszwHZxNWqsnoKgyqwgNHgsF5XNKqc/Y21t7Nqnhz5srsXtYNymZEvFsdwOw/B5RZfmdt8d2B/GbesEbp+RiOFVk2frfnpzoXYqwdpZ2H/r5On9BQQzeXBDsrEfPJ9C1eCCOfCquW3s7fkgO5V6QXAp6qnh9m+6evr2707n/W8=&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://app.diagrams.net/js/viewer.min.js"></script>

Therefore the following requirements apply:

### For the booking consumer:

* each request **must** include an ```X-request-ID```
* any retry of the same request **must** include the original ```X-request-ID``` unchanged
* received responses **should** be correlated with the originating request
* receved ```X-request-ID``` and ```X-Correlation-ID``` **must** be placed in a log or audit trail against the booking attempt

### For the booking provider:

* each response **must** include an ```X-request-ID```
* each response **must** echo the request ```X-request-ID``` as the ```X-Correlation-ID```
* The ```X-request-ID``` from the request message **must** be used to verify a previous successful booking has not already been made from a request with this ```X-request-ID```
* receved ```X-request-ID``` and ```X-Correlation-ID``` **must** be placed in a log or audit trail against the booking attempt
