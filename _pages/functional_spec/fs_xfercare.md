---
title: Referencing Transfer of Care Documentation
sidebar: overview_sidebar
keywords: specification
permalink: fs_xfercare.html
toc: false
folder: functional_spec
---

### How do we reference transfer of care documentation?

Consumer Requirements

The CDA should have a new component in it, which holds a <linkHtml href="URL here">Link title here</linkHtml>, for example:

### Appointment reference 

```XML 
<component typeCode="COMP" contextConductionInd="true">  <npfitlc:contentId root="2.16.840.1.113883.2.1.3.2.4.18.16" extension="COCD_TP146246GB01#Section1"/>    <section classCode="DOCSECT" moodCode="EVN">      <templateId root="2.16.840.1.113883.2.1.3.2.4.18.2" extension="COCD_TP146246GB01#Section1"/>      <id root="773110DB-288F-4B32-8DE1-362646A65E8C"/>      <title>Booked Appointment Information </title>      <text>        <linkHtml href="https://servername.orgname.nhs.uk/FHIR/Appointment/1234567">https://servername.orgname.nhs.uk/FHIR/Appointment/1234567</linkHtml>      </text>  </section></component>
```

The process for being able to link the two together is complicated by the fact that the identifier for the CDA is created by the Consumer, while the identifier for the Appointment is created by the Provider. As a result of this, the following process needs to be followed:
 
 * Generate the UUID to be used as the identity of the CDA 
 * Generate the Appointment resource 
 * Insert the UUID from #1 into the Appointment resource. 
 * POST the Appointment, response has a Location header that gives the URL of the saved Appointment. 
 * Ensure the URL is a fully qualified, (so starting with https:// etc not just /Appointment/xxx-yyy-1234- etc). 
 * Complete the CDA generation as normal. 
 * Add the ODS into the CDA as shown above.

### Provider Requirements

On receipt, the Provider must then do the following:

When a CDA arrives:
1. First receive CDA. 
2. Find matched cases (probably none) based on ID of the CDA == Appointment.DocumentReference.identifier. 
3. Create Case. 
4. Lookup / Create the Patient. 
 a. Optionally(Appointment might or might not arrive) 
 b. Then receive Appointment. 
 c.Find matched cases based on Appointment.DocumentReference.identifier == ID of the CDA that triggered the case. 
 d.Merge Appointment into Case. 

When anappointment arrives:
1. First receive Appointment.
2. Find existing matched cases (probably none) based on Appointment.DocumentReference.identifier == ID of the CDA that triggered the case.
3.Create a new Case.
4.Lookup / Create the Patient.
 a.Optionally(CDA might or might not arrive)
 b.Then receive CDA.
 c.Find matched cases based on ID of the CDA == Appointment.DocumentReference.identifier of the Appointment that triggered the case.
 d.Merge CDA into Case.This isolates the process from any sensitivity about whether both messages arrive, and will work regardless of what sequence they arrive.
