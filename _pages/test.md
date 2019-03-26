---
title: Test Page
sidebar: overview_sidebar
keywords: test
permalink: test.html
toc: false
---

{% include note-notpublished.html %}

{% include codebox.html title="Sample Proposed Appointment Pointer"
code="
{
    &quotresourceType&quot: &quotAppointment&quot,
    &quotid&quot: &quot0c55f3f6-6e7c-4a3e-b891-286b6a97f0ca&quot,
    &quotmeta&quot: {
        &quotprofile&quot: &quothttps://fhir.hl7.org.uk/STU3/StructureDefinition/[New Profile Name Goes Here]&quot
    },
    &quottext&quot: &quot<div>Empty</div>&quot,
    &quotidentifier&quot: [
        {
            &quotuse&quot: &quotofficial&quot,
            &quotsystem&quot: &quoturn:ietf:rfc:3986&quot,
            &quotvalue&quot: &quothttps://actual.resource.location/base/Appointment/[id]&quot
        }
    ],
    &quotstatus&quot: &quotbooked&quot,
    &quotcreated&quot: &quot2018-01-17T13:36:00.000Z&quot,
    &quotstart&quot: &quot2018-04-01T09:00:15.000Z&quot,
    &quotparticipant&quot: [
        {
            &quotactor&quot: {
                &quotidentifier&quot: {
                    &quotuse&quot: &quotofficial&quot,
                    &quotsystem&quot: &quothttps://fhir.nhs.uk/Id/nhs-number&quot,
                    &quotvalue&quot: &quot12341234123&quot
                }
            }
        }
    ]
}
"
%}
