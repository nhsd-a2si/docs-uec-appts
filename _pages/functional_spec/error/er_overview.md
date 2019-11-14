---
title: FHIR&reg; implementation
keywords: fhir development
tags: [fhir,development]
sidebar: error_sidebar
permalink: er_overview.html
summary: "Implementation guidance for developers - focusing on error handling"
---

## Introduction

There are several points at which an error may occur to prevent the appointment booking operations completing successfully.

The following guidance is for Care Connect Appointment booking.  GP Connect is very similar but has specific guidance here: https://nhsconnect.github.io/gpconnect/development_fhir_error_handling_guidance.html.

## Overview

Error codes are returned by the APIs used to connect to each service.  Error codes are meant for developer use only - they should not be presented to end-users.  Instead, Consumer applications should interpret the codes and provide user-friendly resolution steps on failure.  Consumer and Provider systems should record the detailed error codes in local logs in order to support service incident investigation.

As the process is initiated by a Consumer there could be several stages that create issues - this table provides a high-level overview of each stage and then follows with specific sections to detail the error handling process and Consumer and Provider responsibilities.
