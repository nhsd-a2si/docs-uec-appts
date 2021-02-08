---
title: How to store patient contact details
sidebar: overview_sidebar
keywords: specification
permalink: fs_patientcontact.html
toc: false
folder: functional_spec
---

When storing patient contact details against the {%include FHIRSpecificationLink.html link="patient.html" text="Patient Resource" %}





Patient.address | 1..*
At least one address should be populated. you MUST also populate the Patient.Address.Use

Patient.telecom | 1..* OR Patient.contact.telecom | 1..*
At least one telecom MUST be populated, either Patient.telecom OR Patient.contact.telecom. You MUST also populate the Patient.telecom.rank OR Patient.contact.telecom.rank and there must be a clear indication or priority by ONLY ONE element with Patient.telecom.rank = 1 OR Patient.contact.rank = 1.
