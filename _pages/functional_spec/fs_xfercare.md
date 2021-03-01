---
title: Referencing Transfer of Care Documentation
sidebar: overview_sidebar
keywords: specification
permalink: fs_xfercare.html
toc: false
---

## How do we reference transfer of care documentation?

The UEC Booking standard specifically does not include any transfer of care information. The booking process typically forms a part of an overall referral workflow and the standard allows for reference to any transfer of care documentation that might be sent.

The intention is to allow the booking message to include a reference to any referral document (e.g. 111CDA, Kettering, and FHIR documents) and in the FHIR profile for an appointment it is possible to add this reference, this is detailed in the <a href="https://developer.nhs.uk/apis/nhsscheduling-1.0.5-alpha/appointment.html" target="_blank">message specification</a>.

The reference is in the form of a contained FHIR <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-DocumentReference-1" target="_blank">document reference</a> resource. This resource allows the reference to be made in a standardised and structured way.

Ideally the referral documentation will also include a reference to the appointment too. This will then allow for cross referencing which will help with the asynchronous relationship between the booking and referral messages. Depending on use case, the referral documentation may be sent first, at the same time or after the appointment message. In the cases where the appointment is created before the referral document, the reference to the booking would have to be included to allow them to be matched by the appointment provider.

The intention is that any standards that govern referral messaging and documentation will include references to appointments in due course.


### How this might work in practice

Below is an example of how one type of transfer of care process can be linked with appointment booking.

In this illustration we have a referral from 111 using a 111CDA document containing a coded entry which holds the appointment reference / identifier and a coded section heading which holds a text representation of appointment details.  

```XML
<entry typeCode="COMP" contextConductionInd="true">
  <npfitlc:contentId root="2.16.840.1.113883.2.1.3.2.4.18.16" extension="COCD_TP146093GB01#AppointmentReference"/>
  <encounter classCode="ENC" moodCode="APT">
    <templateId root="2.16.840.1.113883.2.1.3.2.4.18.2" extension="COCD_TP146093GB01#AppointmentReference"/>
    <id root="2.16.840.1.113883.2.1.3.2.4.17.541" extension="eb4f7f21-3962-4416-9a29-a46dd6ee5f17"/>
    <code code="01" codeSystem="2.16.840.1.113883.2.1.3.2.4.17.542" displayName="Patient booking"/>
    <effectiveTime value="201706011400+00"/>
    <participant typeCode="LOC" contextControlCode="OP">
      <templateId root="2.16.840.1.113883.2.1.3.2.4.18.2" extension="COCD_TP146093GB01#location"/>
      <participantRole classCode="ASSIGNED">
        <templateId root="2.16.840.1.113883.2.1.3.2.4.18.2" extension="COCD_TP146093GB01#assignedEntity"/>
        <id root="2.16.840.1.113883.2.1.3.2.4.19.1" extension="Q36"/>
        <addr use="WP">
          <streetAddressLine>Great George Street</streetAddressLine>
          <city>Leeds</city>
          <postalCode>LE13EX</postalCode>
        </addr>
        <playingEntity classCode="ORG" determinerCode="INSTANCE">
          <templateId root="2.16.840.1.113883.2.1.3.2.4.18.2" extension="COCD_TP146093GB01#assignedOrganization"/>
          <name>CENTRAL LONDON COMMUNITY HEALTHCARE NHS TRUST</name>
          <desc>Psychiatric Community Care Services</desc>
        </playingEntity>
      </participantRole>
    </participant>
    <component typeCode="COMP" contextConductionInd="true">
        <npfitlc:contentId extension="COCD_TP146246GB01#Section1" root="2.16.840.1.113883.2.1.3.2.4.18.16"/>
        <section classCode="DOCSECT" moodCode="EVN">
            <templateId extension="COCD_TP146246GB01#Section1" root="2.16.840.1.113883.2.1.3.2.4.18.2"/>
            <id root="90611FD4-6616-11EB-B9BD-00155D70280A"/>
            <title>Booked Appointment Information</title>
            <text>
                <linkHtml href="https://<generic-address-here>/fhir/Appointment/28BCD0FC-F01F-4DB2-B6F1-92A36A37B348/">https://NHSD.Test.INT.nhs.uk/fhir/Appointment/28BCD0FC-F01F-4DB2-B6F1-92A36A37B348</linkHtml>
            </text>
        </section>
    </component>
  </encounter>
</entry>
```

Key to the linking is the ```COMP``` component, specifically the ```linkHtml``` element where the appointment URL is specified.

```XML
<component typeCode="COMP" contextConductionInd="true">
    <npfitlc:contentId extension="COCD_TP146246GB01#Section1" root="2.16.840.1.113883.2.1.3.2.4.18.16"/>
    <section classCode="DOCSECT" moodCode="EVN">
        <templateId extension="COCD_TP146246GB01#Section1" root="2.16.840.1.113883.2.1.3.2.4.18.2"/>
        <id root="90611FD4-6616-11EB-B9BD-00155D70280A"/>
        <title>Booked Appointment Information</title>
        <text>
            <linkHtml href="https://<generic-address-here>/fhir/Appointment/28BCD0FC-F01F-4DB2-B6F1-92A36A37B348/">https://NHSD.Test.INT.nhs.uk/fhir/Appointment/28BCD0FC-F01F-4DB2-B6F1-92A36A37B348</linkHtml>
        </text>
    </section>
</component>
```

The process for being able to link the two together is complicated by the fact that the identifier for the CDA is created by the Consumer, while the identifier for the Appointment is created by the Provider. As a result of this, the following process needs to be followed:

 * Generate the UUID to be used as the identity of the CDA
 * Generate the Appointment resource
 * Insert the UUID from #1 into the Appointment resource.
 * POST the Appointment, response has a Location header that gives the URL of the saved Appointment.
 * Ensure the URL is a fully qualified, (so starting with https:// etc not just /Appointment/xxx-yyy-1234- etc).
 * Complete the CDA generation as normal.
 * Add the ODS into the CDA as shown above.

{% include important.html content="The URL **MUST** be taken from the ```linkHtml``` ```href``` tag and a whilst the URL must be fully qualified it **MUST NOT** include the specific version of the appointment.  

For example the following is a correctly formed appointment URL https://servername.orgname.nhs.uk/FHIR/Appointment/1234567 whereas https://servername.orgname.nhs.uk/FHIR/Appointment/1234567/_history/1 is invalid.
" %}

It **must** be noted, CDA messages offer operations which the Booking Standard does not support. 111CDA allows for a message to be replaced, the new message superceding the original as the most clinically relevant, rendering the original out-of-date and not to be used for clinical decision making. 

The process of replacing CDAs is usually acceptable, the documents are versioned and all must be stored by the receiver, providing a complete audit history. However, when a booking is made, it includes reference to a specific CDA document which, if the replace operation is performed, no longer exists as a clinically relevant document.

{% include important.html content="Replace/Update operations **must** not be performed against CDA messages once transmitted and linked to a booking" %}

### Provider Requirements

On receipt, the Provider must then do the following:

##### When a CDA arrives:

1. First receive CDA.
2. Find matched cases based on ID of the CDA->Appointment.DocumentReference.identifier.
3. If no case found:
     a. Lookup / Create the Patient.
     b. Create case.
     c. Save the CDA to the record against this case.
4. If case is found (as appointment was created first), merge CDA into case - save against the record so that the CDA information is easily accessible by a clinician against the case when the patient attends the appointment.

##### When an appointment arrives:

1. First receive Appointment.
2. Find existing matched cases based on Appointment.DocumentReference.identifier->ID of the CDA document.
3. If no case found:
     a. Lookup / Create the Patient.
     b. Create case
     c. Create appointment- with the reference to the CDA document within it.
4. If case is found (as CDA was received first), link appointment to the case - save against the record so that the appointment is linked to the clinical case that has been transferred using the CDA. This ensures that when the patient attends the appointment it is linked to the transfer of care information.


This isolates the process from any sensitivity about whether both messages arrive, and will work regardless of what sequence they arrive.
