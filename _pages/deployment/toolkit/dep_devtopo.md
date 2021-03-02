---
title: Deployment Toolkit - System Topologies
sidebar: overview_sidebar
keywords: guidance
permalink: dep_devtopo.html
toc: false
folder: deployment
---

There are several different types of deployment topologies for brokering API calls through the SSP:

### Consumer models

- [`Simple Model`](#simple-model)
- [`Aggregator Model`](#aggregator-model)

### Provider Models

- [`Single Practice System`](#single-practice-system)
- [`Data Centre Hosted Practice System`](#data-centre-hosted-practice-system)

### Consumer models

#### Simple Model

In this model, each different Care Connect consumer systems, all connecting directly to an appointment provider via the SSP. Each consumer in this example is registered as a CMA endpoint. The key point is that each consumer system has its own ASID

<img src="https://developer.nhs.uk/apis/spine-core/images/integration/consumer-topology1-simple.png" alt=" see: https://developer.nhs.uk/apis/spine-core/ssp_system_topologies.html">

#### Aggregator Model

Here, several different consumer systems connect to the Spine via a single middleware instance (Message Handling Server / MHS)

<img src="https://developer.nhs.uk/apis/spine-core/images/integration/consumer-topology2-aggregator.png" alt="see: https://developer.nhs.uk/apis/spine-core/ssp_system_topologies.html">

### Provider Models

#### Single System Model

Here a single instance of an appointment provider system is service a single service:

<img src="https://developer.nhs.uk/apis/spine-core/images/integration/provider-topology1-single.png" alt="see: https://developer.nhs.uk/apis/spine-core/ssp_system_topologies.html">

#### Data Centre Hosted System Model

Finally, an appointment provider system instance hosted in a supplier’s data centre. Note each individual service has a logical CMA endpoint with its own ASID but sharing the Party Key:

<img src="https://developer.nhs.uk/apis/spine-core/images/integration/provider-topology2-datacentre.png" alt="see: https://developer.nhs.uk/apis/spine-core/ssp_system_topologies.html">

### See also:

Legend for diagrams: 
<img src="https://developer.nhs.uk/apis/spine-core/images/integration/topologies-legend.png" alt="see: https://developer.nhs.uk/apis/spine-core/ssp_system_topologies.html">


For further information and source for this page, please see <a href="https://developer.nhs.uk/apis/spine-core/ssp_system_topologies.html" target="_blank">here</a> (links to core SPINE documentation)
