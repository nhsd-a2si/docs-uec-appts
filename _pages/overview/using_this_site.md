---
title: Using this site
sidebar: overview_sidebar
keywords: guidance
permalink: using_this_site.html
toc: false
tags: [getting_started]
folder: getting_started
---
To help get the most out of the published resources, understanding what exists and how it is intended to be used is documented here.

There are two core resources - 

## Standard
This site, which can be thought of as an [**implementation guide**](https://developer.nhs.uk/apis/uec-appointments/), covering everything from use cases for booking through to the what an authentication token needs to include. 

Initially, it can be used to guide analysis and define the scope of a solution. **Developers** will need to use it in conjunction with the *Specification* (outlined below) to understand workflow, error handling and non-functional requirements a solution needs to fulfil. There are also resources for **Project Managers** and stakeholders who are involved in moving the solution to live environments, namely the <a href="deployment_toolkit.html" target="_blank">Deployment Toolkit</a>.

## Specification 
A [**technical document**](https://developer.nhs.uk/apis/nhsbooking-2.0.1-beta/) which explicitly defines the NHS FHIR(STU3) Booking API resources and structures, along with the method operations (GET, PUT & POST) used. 

***
## Planning a project 
There is a <a href="getting_started.html" target="_blank"><strong>Quick Start Guide</strong></a> which assists suppliers through all key areas of a project when building a solution. This should be reviewed in detail as part of the analysis process and subsequent project planning. It is also a useful resource to return to, at any of the project phases, to keep track of progress but also for links to more detailed information. 

## Other key areas 
### Use Cases 
<a href="use_overview.html" target="_blank">User Stories</a> which define the scope of capabilites the booking Standard aims to cover. 

### Workflows 
The Functional Specification outlines the <a href="fs_workflow.html" target="_blank">workflows</a> involved in the booking Standard and goes on to breakdown the key areas in more detail. This section covers some of the very technical points of the Standard and will be used by anyone (Developers, Solution Architects, Technical Business Analysts) involved in documenting or building these aspects of a solution. 

### Tooling
There is a <a href="demo_overview.html" target="_blank">Demonstrator</a> (deprecated) which replicates examples of the requests and responses expected to be exchanged at API level. It is internet facing but doesn't support all the components seen in a live workflow e.g. SDS, SSP and DoS. 

A new suite of tools are available called <a href="sims_install.html" target="_blank">TKW Simulators</a> (replicating Provider and Consumer behaviour). These are Docker Containers, capable of being deployed locally, but with equivalent endpoints within the Path-to-Live environments, OpenTest, DEV and INT. The Simulators will assist with both development and assurance, logging, validating messages and capturing and packaging evidence which can be appended to a SCAL submission. 

### Assurance 
The solution developed is self assured by the supplier using the <a href="assurance_scal.html" target="_blank">SCAL</a>. This is a manual process of confirming the solution meets certain capabilities and providing evidence to support this. The new suite of <a href="sims_install.html" target="_blank">tools</a> (as described above) is capable of capturing and colating the evidence required for the SCAL submission.

### Deployment 
There is a clearly defined <a href="dep_devptl.html" target="_blank">Path-to-Live</a>, taking a solution through all levels of <a href="dep_testtesting.html" target="_blank">testing maturity</a> and into Production go-live.
