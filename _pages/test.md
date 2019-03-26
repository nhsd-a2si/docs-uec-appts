---
title: Test Page
sidebar: overview_sidebar
keywords: test
permalink: test.html
toc: false
---

{% include note-notpublished.html %}

{% include codebox.html title="Sample Proposed Appointment Pointer"
contnent="
{
    "resourceType": "Appointment",
    "id": "0c55f3f6-6e7c-4a3e-b891-286b6a97f0ca",
    "meta": {
        "profile": "https://fhir.hl7.org.uk/STU3/StructureDefinition/[New Profile Name Goes Here]"
    },
    "text": "<div>Empty</div>",
    "identifier": [
        {
            "use": "official",
            "system": "urn:ietf:rfc:3986",
            "value": "https://actual.resource.location/base/Appointment/[id]"
        }
    ],
    "status": "booked",
    "created": "2018-01-17T13:36:00.000Z",
    "start": "2018-04-01T09:00:15.000Z",
    "participant": [
        {
            "actor": {
                "identifier": {
                    "use": "official",
                    "system": "https://fhir.nhs.uk/Id/nhs-number",
                    "value": "12341234123"
                }
            }
        }
    ]
}
"
%}
