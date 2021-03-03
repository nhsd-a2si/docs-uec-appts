---
title: DoS Workflow - Transfer of care and ITK Messages
sidebar: overview_sidebar
keywords: specification
permalink: dos_itk.html
toc: false
folder: dos
---

Most booking solutions including standards booking do not require a transfer of care message to be transmitted using ITK.

Ther are however the following considerations:

* If it is decided by a service that accepting ITK referrals is desirable and their system is capable of receiving them then they can. 
  * However, there is a clear responsibility that they will be receiving these referrals and they need to be managed appropriately.
  
* Ultimately the DoS lead in an area is in control of profiling a service for ITK messaging. 
  * It is therefore part of their assurance responsibility for adding an endpoint to make sure that the receiving service is both configured technically and also prepared operationally to start receiving ITK referrals. 
  * If this assurance is not obtained, the DoS lead must not add the endpoint to enable ITK messaging. It is their responsibility to ensure this.

## Linking between the CDA and Appointment

Current practice is that a CDA document (an Integrated Urgent Care Report) is (almost) always sent when referring a patient on from NHS 111 to a UTC.

The introduction of this API capability will mean that in addition to the CDA report, the UTC will receive a profiled FHIR Appointment resource for the same case. It is important that the UTC are able to link the two objects together to have one complete case, rather than two separate and incomplete cases.

The CDA document has a new component in it, which holds a <linkHtml href="URL here"><red>Link title here</red></linkHtml>, for example:

``` json
<component typeCode="COMP" contextConductionInd="true">
  <npfitlc:contentId root="2.16.840.1.113883.2.1.3.2.4.18.16" extension="COCD_TP146246GB01#Section1"/>
    <section classCode="DOCSECT" moodCode="EVN">
      <templateId root="2.16.840.1.113883.2.1.3.2.4.18.2" extension="COCD_TP146246GB01#Section1"/>
      <id root="773110DB-288F-4B32-8DE1-362646A65E8C"/>
      <title>Booked Appointment Information </title>
      <text>
        <linkHtml href="https://servername.orgname.nhs.uk/FHIR/Appointment/1234567">https://servername.orgname.nhs.uk/FHIR/Appointment/1234567</linkHtml>
      </text>
  </section>
</component>
```

The Appointment resource has a <a href="https://www.hl7.org/fhir/references.html#contained" target="_blank">contained</a> resource of type <a href="https://www.hl7.org/fhir/documentreference.html" target="_blank">DocumentReference</a> resource, which identifies the CDA document, for example:

``` xml
{
    "resourceType": "Appointment",
    "id": "81fc8fc9-de26-4ae7-a838-23317a64e2ab",
    "text": {
        "status": "generated",
        "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\">Brian Appointment</div>"
    },
    "status": "booked",
    "contained": [
        {
            "resourceType": "DocumentReference",
            "id": "4350ae81-5c75-4fa1-99bb-e5693d411332",
        }
    ],
    "description": "A description",
    "slot": "https://server.organisation.nhs.uk/fhirbase/Slot/1234554321",
    "created": "2018-12-04T13:16:05Z",
    "comment": "A comment",
    "participant": [
        {
            "actor": {
                "reference": "https://demographics.spineservices.nhs.uk/Patient/1234567890",
                "display": "Peter James Chalmers"
            }
        }
    ]
}
```
The process for being able to link the two together is complicated by the fact that the identifier for the CDA is created by the Consumer, while the identifier for the Appointment is created by the Provider. As a result of this, the following process needs to be followed:

1. Generate a UUID which will be used to identify the CDA.
2. Generate the Appointment resource.
3. Insert the UUID (from #1) into a contained DocumentReference resource in the appointment resource.
4. POST the Appointment resource to the Provider, on success the response will include a Location http header which contains the URL of the newly created Appointment.
5. Ensure the Appointment URL is a fully qualified URL (by prefixing with the Provider system's FHIR server base URL if necessary) into the new component in the CDA.
6. Complete the CDA generation as normal.
7. Send the CDA as normal.

On receipt, the Provider must then do the following:

When a CDA arrives.

1. First receive CDA.
2. Find matched cases (probably none) based on ID of the CDA == Appointment.DocumentReference.identifier.
3. Create Case.
4. Lookup / Create the Patient.
   * **Optionally** (Appointment might or might not arrive)
   * Then receive Appointment.
   * Find matched cases based on Appointment.DocumentReference.identifier == ID of the CDA that triggered the case.
   * Merge Appointment into Case.

When an Appointment arrives:

1. First receive Appointment.
2. Find existing matched cases (probably none) based on Appointment.DocumentReference.identifier == ID of the CDA that triggered the case.
3. Create a new Case.
4. Lookup / Create the Patient.
   * **Optionally** (CDA might or might not arrive)
   * Then receive CDA.
   * Find matched cases based on ID of the CDA == Appointment.DocumentReference.identifier of the Appointment that triggered the case.
   * Merge CDA into Case.

This isolates the process from any sensitivity about whether both messages arrive, and will work regardless of what sequence they arrive. 
