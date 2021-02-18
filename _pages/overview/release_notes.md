---
title: Release Notes
sidebar: overview_sidebar
keywords: introduction
permalink: release_notes.html
toc: true
tags: [getting_started]
folder: introduction
---

## Current Release

### 0.2.0 BETA

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.2.0  | BETA   | Public Beta | Current Version | 12/02/2021   | Volatile

The 0.2.2 BETA release has the following highlights:

* The FHIR API Specification has been update to 2.0.2 BETA 
  * Resources Overview page has been updated to reflect a generic use case. <mark style="background-color: LightGreen">non-breaking</mark>
  * Guidance around Location resource has been updated.<mark style="background-color: LightGreen">non-breaking</mark>
  * Additional guidance added regarding include and revinclude parameters <mark style="background-color: LightGreen">non-breaking</mark> <mark style="background-color: Yellow">correction</mark>
  * Element Id has been replaced with identifier for HealthcareService resource. <mark style="background-color: #ff8080">breaking</mark><mark style="background-color: Yellow">correction</mark>
  * Updated the description for id for the Schedule resource. <mark style="background-color: LightGreen">non-breaking</mark> <mark style="background-color: Yellow">correction</mark>
  * Practitioner and PractitionerRole pages have been removed. <mark style="background-color: LightGreen">non-breaking</mark>
  * Appointment example has been fixed to reflect the correct format for references. <mark style="background-color: LightGreen">non-breaking</mark> <mark style="background-color: Yellow">correction</mark>
  * References to the registry function has been removed. <mark style="background-color: LightGreen">non-breaking</mark>
  * Additional guidance added to the Appointment.created element. <mark style="background-color: #ff8080">breaking</mark> <mark style="background-color: Yellow">correction</mark>
  * Narrative added to the diagrams on the profile overview page. <mark style="background-color: LightGreen">non-breaking</mark>
  * New page added for the the Bundle resource. <mark style="background-color: LightGreen">non-breaking</mark>
  * Addition of a new FHIR SearchParameter required for searching slots. <mark style="background-color: LightGreen">non-breaking</mark>
  * Guidance added for outputting data in different formats. <mark style="background-color: LightGreen">non-breaking</mark>
  * Additional guidance added for the patient.telecom element. <mark style="background-color: LightGreen">non-breaking</mark>  
* Updated [Authentication Page](fs_authentication.html){:target="_blank"}
  * Some typos were fixed <mark style="background-color: LightGreen">non-breaking</mark>
  * Guidance around the scope claims was updated to provide more clarity on the application of the different scopes <mark style="background-color: LightGreen">non-breaking</mark>
* Removed references to Appointment Registry from [Cancellation section](cr_overview.html){:target="_blank"} <mark style="background-color: LightGreen">non-breaking</mark>
* Updated the name of the standard to "NHS Booking Standard" and removed references specifically referring to the standard as the "UEC Booking Standard" to support future use cases <mark style="background-color: LightGreen">non-breaking</mark>
* Updated most pages to reference booking rather than "appointment" unless specifically appropriate <mark style="background-color: LightGreen">non-breaking</mark>
* Updated some wording on [booking definition](definition.html){:target="_blank"} page to be more generic <mark style="background-color: LightGreen">non-breaking</mark>
* Updated [contact details](contact.html){:target="_blank"} to new contact email address <mark style="background-color: LightGreen">non-breaking</mark>
* A small update to the guidance on [how to handle times](fs_times.html){:target="_blank"} was made. <mark style="background-color: LightGreen">non-breaking</mark>
* A new page on [how to store patient contacts](fs_patientcontact.html){:target="_blank"} has been added. This providers clear business rules on what and where contacts should be stored <mark style="background-color: #ff8080">breaking</mark>
* Based on usability feedback, the menu system has been updated to use a single menu flow rather than break out to "sub-pages" for certain sections <mark style="background-color: LightGreen">non-breaking</mark>
* A new page describing how to [maintain transactional integrity](fs_xti.html){:target="_blank"} and how custom headers can support this <mark style="background-color: #ff8080">breaking</mark>
* Updated the [deployment toolkit](deployment_toolkit.html){:target="_blank"} with a significant amount of new content <mark style="background-color: LightGreen">non-breaking</mark>
* Removed references to the demonstrator and added new pages to support the new [Provider and Consumer simulator tools](sims_install.html){:target="_blank"} ?? <mark style="background-color: LightGreen">non-breaking</mark>
* Fixed some broken links that referenced external resources <mark style="background-color: LightGreen">non-breaking</mark>
* Added a new page providing some [API guidance](implementation_api){:target="_blank"}, removing ambiguity over a number of subjects <mark style="background-color: #ff8080">breaking</mark>
* A new page describing [interactions with SDS](fs_sds.html){:target="_blank"} was created <mark style="background-color: LightGreen">non-breaking</mark>
* A new page describing [interactions with SSP](fs_ssp.html){:target="_blank"} was created <mark style="background-color: LightGreen">non-breaking</mark>
* The overview page on [error handling](er_overview.html){:target="_blank"} was updated to improve clarity and remove ambiguity <mark style="background-color: LightGreen">non-breaking</mark>
* The page on [error handling](er_errorhandling.html){:target="_blank"} was updated to improve clarity and remove ambiguity <mark style="background-color: LightGreen">non-breaking</mark>
* The [booking and referral messages](dos_itk.html.html){:target="_blank"} page was removed as it is duplicating the "transfer of care" page in the "functional spec" section <mark style="background-color: LightGreen">non-breaking</mark>
* The [transfer of care](fs_xfercare.html){:target="_blank"}  page was updated to provide more clarity on how to store appointment references in the 111CDA document <mark style="background-color: LightGreen">non-breaking</mark>
* [IG Pages](ig_overview.html){:target="_blank"} have been updated with new IG statement
* [IG FAQ](ig_overview.html){:target="_blank"} has been updated with new content
* An indication of breaking and non-breaking changes has been added to the release notes <mark style="background-color: LightGreen">non-breaking</mark>

<br>
<br>

## Future releases

### 1.0.0 RC1

Version | Handle  | Phase | State           | Release Date (planned) | Stability
--------|---------|-------|-----------------|--------------|----------------
1.0.0   | RC1 | Release Candidate | Unreleased | TBC   | Volatile

<br>
<br>

## Previous releases

### 0.1.17 ALPHA

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.17  | ALPHA   | Alpha | Current Version | 18/12/2020   | Volatile

The 0.1.17 ALPHA release has the following highlights:

* <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/overview_release_notes.html" target="_blank">Update of FHIR Specification to 2.0.1-beta</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.1-beta/appointment.html" target="_blank">Updated description for ‘supportingInfo’ element for the Appointment resource.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.1-beta/appointment.html" target="_blank">Updated description for ‘participant’ element for the Appointment resource.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.1-beta/appointment.html" target="_blank">Added guidance for using ‘incomingReferral’ element for the Appointment resource.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.1-beta/appointment.html" target="_blank">Updated contained resource guidance for the Appointment resource.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.1-beta/search_free_slots.html" target="_blank">Updated search parameters guidance when searching for free slots.</a>
* <a href="fs_workflow.html#endpoint-discovery" target="_blank">Fixed some incorrect interactions in some diagrams on the workflow page</a>
* <a href="fs_workflow.html#patient-demographic-service-pds" target="_blank">Removed guidance that PDS trace is mandatory for Consumer systems</a>
* <a href="usep_abus13.html" target="_blank">Updated user story (abus13) to be more generic in its guidance, removing specific references to the UEC DoS</a>
* <a href="what_are_we_doing.html" target="_blank">Updated some wording on the "What we are doing?" page</a>
* <a href="caresetting.html" target="_blank">Updated some wording on the "Care Settings" page</a>
* <a href="catalogue.html" target="_blank">Updated the conformance catalogue page to reflect the latest status and add links</a>
* <a href="scope_functional.html" target="_blank">Updated the functional scope page to reflect the latest developments in the standard</a>
* <a href="fs_authentication.html#jwt-payload" target="_blank">Made the "requesting_practitioner" claim optional</a>
* <a href="glossary.html" target="_blank">Added a number of new items to the glossary</a>

### 0.1.16 ALPHA

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.16  | ALPHA   | Alpha | Current Version | 28/08/2020   | Volatile

The 0.1.16 ALPHA release has the following highlights:

* <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/overview_release_notes.html" target="_blank">Update of FHIR Specification to 2.0.0-beta</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/" target="_blank">Renamed from NHS FHIR Scheduling API to NHS FHIR Booking API.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/appointment.html" target="_blank">Updated Appointment guidance to include mandatory Appointment.end to align with the FHIR standard.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/appointment.html" target="_blank">Updated Appointment.created guidance to align with the FHIR standard.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/appointment.html" target="_blank">Updated Appointment.contained to include Slot as a contained resource.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/appointment.html" target="_blank">Updated Appointment examples.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/patient.html" target="_blank">Updated Patient identifier guidance in line with</a> <a href='https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1' target="_blank">CareConnect-Patient-1</a> profile. Notably removing mandatory NHS Number
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/cancel_an_appointment.html" target="_blank">Updated 'success' behaviour for cancelling an Appointment.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/slot.html" target="_blank">Updated Slot elements.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/search_free_slots.html" target="_blank">Updated 'Search for free slots' example.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/search_patient_appointments.html" target="_blank">Updated 'Search for appointments' example.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/get_an_appointment.html" target="_blank">Updated 'Get an appointment' examples.</a>
   - <a href="https://developer.nhs.uk/apis/nhsbooking-2.0.0-beta/developing.html" target="_blank">Updated development guidance on validating resources.</a>
* <a href="fs_times.html" target="_blank">Created a new page describing how to handle times</a>
* <a href="fs_workflow.html#how-times-should-be-handled" target="_blank">References to times have been updated to refer to new page on times</a>
* The "functional specification" menu items were updated to more clearly reflect content
* <a href="scope_functional.html" target="_blank">The Functional Scope page was updated to move Emergency Departments and Patient facing uses into scope</a>
* <a href="fs_deliverychannel.html" target="_blank">A new page documenting requirements for displaying slots, including explicit reference to delivery channel was added</a>
* <a href="" target="_blank">The conformance catalogue page was updated to remove unnecessary reference to GP Connect and change the format and content to reflect the current status of suppliers </a>

* Fixed broken menu item for GP Connect section

### 0.1.15 ALPHA

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.15  | ALPHA   | Alpha | Released | 24/07/2020   | Volatile

The 0.1.15 ALPHA release has the following highlights:

* First iteration of the deployment toolkit
  * <a href="dep_devptl.html" target="_blank">Path-to-Live guidance started (based on lessons learned so far)</a>
  * <a href="dep_devtopo.html" target="_blank">System Topologies page added</a>
  * <a href="dep_devtest.html" target="_blank">Testing resources for system suppliers added</a>
  * <a href="dep_provtest.html" target="_blank">Testing resources for providers added</a>
* <a href="definition.html" target="_blank">Made a slight wording change to the definition of appointment booking in the overview/definition page</a>
* <a href="usee_abus22.html" target="_blank">Updated user story: AUBS.22 wording to remove ambiguity over rebooking appointments</a>
* <a href="cr_workflow.html" target="_blank">Updated the cancellation workflow page to have increased clarity over the different possible workflows and the sequence of events.</a>
* <a href="fs_deliverychannel.html" target="_blank">Added a placeholder page for addition of support for "Delivery Channels" (due in the next release)</a>
* <a href="fs_authentication.html" target="_blank">Fixed some broken links on Authentication page and updated some elements with more detail</a>
* <a href="fs_sms.html" target="_blank">A new page providing (draft) guidence for Appointment Text Messages was added</a>
* <a href="assurance_overview.html" target="_blank">Updated the assurance process overview to reflect the current iteration of the process</a>

### 0.1.14 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.14   | PREVIEW | Alpha | Released | 05/05/2020 | Volatile

The 0.1.14 PREVIEW release has the following highlights:
* Updated the FHIR specification version to 1.0.6-alpha
* Added a new page in "Functional Specification" section providing guidance for referencing transfer of care documentation
* Tidied up some aspects of the reporting specification
* Updated the demonstrator pages to reflect recent updates and a change for a future update
* added Covid-19 Dx codes and fixed typos to the appointment mapping page

### 0.1.13 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.13   | PREVIEW | Alpha | Released | 07/02/2020 | Volatile

The 0.1.13 PREVIEW release has the following highlights:
* **Updated all functional specification pages where the ASID being included in the search parameters of FHIR queries is referenced. This has been changed to the more generic Healthcare Service ID and where appropriate direct reference to the DoS Service ID**
* Made some updates to the Functional Spec -> Workflow section
  * Created new requirements about how times and dates should be handled
  * Updated a few of the examples in the diagrams to reflect changes to the FHIR specification
  * Updated the references to authentication to reflect new approach
* Updated the Appointment mapping page to correct a typographical error and add clarification around local variance in GP Connect disposition mapping
* Updated slot mapping page to correct some typos
* Updated reporting specification page 
  * to fix some typos
  * to bring future requirements in to current requirements section (as they are now current requirements)
* Updated the Use Cases
  * Created a new Use Case for booking outside a disposition timeframe
  * Fixed some typos
* Updated the demonstrator pages to reflect a change for a future update

### 0.1.12 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.12   | PREVIEW | Alpha | Released | 19/11/2019 | Volatile

The 0.1.12 PREVIEW release has the following highlights:

* New section on error handling created
* Updated Authentication details with significant changes to reflect current approach
* Created "booking only" services section on DoS sub site
  * Added details for booking only attribute, including sample code (XML)
* Updated reporting requirements section 
   * Added future requirements section
   * Tidied up existing requirements  
   
### 0.1.11 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.11   | PREVIEW | Alpha | Released | 14/10/2019 | Volatile

The 0.1.11 PREVIEW release has the following highlights:

* Updated User Stories
  * Updated wording in all existing user stories
  * Added new user story for booking only services
  * Split cancellation user story into two
* Renamed "getting live" section to "Deployment"
  * Created supplier conformance catalogue
* Fixed a couple of issues in the main navigation
* Updated the reporting requirements
  * Split the requirements into consumer and provider sections
  * updated the layout
  * refreshed the requirements
* Fixed the broken link in the FHIR implementation page
* Fixed a few typos in several pages

### 0.1.10 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.10   | PREVIEW | Alpha | Released |26/07/2019   | Volatile

**The 0.1.10 PREVIEW release has the following highlights:**

* in the DoS workflow section: 
  * The GP Connect "Register a Patient" capability has been added as a requirement to be supported by consumers
  * specific reference to the "Register a Patient" capability has been made in the relevant workflow examples
  * Erroneous text removed from diagram
  * Additional information regarding the correct sequence to determine the SDS query for booking into GP Connect using the DoS 
* A new page displaying road map information was added
* Cancellation capability levels added to cancellation section
* Removed all reference to "HealthcareServiceID" as it was causing confusion and is no longer relevant
* Added guidance for the DoS service attribute
* Removed "not published" note from any pages that are complete

### 0.1.9 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.9   | PREVIEW | Alpha | Released | 14/06/2019   | Volatile

**The 0.1.9 PREVIEW release has the following highlights:**

* Introduction and Overview Sections
  * Wording tidied up in the introduction
  * Definition page wording tidied up
  * UEC Landscape page updated with more appropriate links and improved wording
  * Updated UEC Overview infographic
  * Tidied up and updated wording in scope section
* Scope and user stories section
   * Refreshed the scope overview page to align to current program milestones
   * Fixed typos in user story overview section
   *  Fixed typos and tidied up wording in various user stories
* Updated the non-functional requirements to reflect the current expectations
* Updated the workflow section in Functional Spec
* Various updates were made to the DoS section: 
  * Updated the DoS endpoints section
  * Updated the DoS requirements page
  * The workflow examples from the GP Connect section were moved into the DoS workflow section so the workflow examples for DoS interactions are in the same place.
  * Some typos were fixed in the workflow section
  * "Links between booking and CDA" page was elaborated
* Appointment Types page was removed (concept no longer relevant to FHIR spec - delivery channel used instead  - for GP Connect only)
* Cancel / Rebook section
  * Wording updated and typos removed from architecture page
  * Wording updated and typos removed from workflow page
* The Demonstrator overview section was updated
* Updated the FHIR profile page to link to GP Connect as well as Care Connect
* Updated the Glossary with some more detail and corrections

### 0.1.8 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.8   | PREVIEW | Alpha | Released | 17/05/2019   | Volatile

The 0.1.8 PREVIEW release has the following highlights:

* Update to the assurance section encompassing the following new content:
  * Update to the assurance overview section
    * Complete high level description of assurance and on-boarding process
    * Addition of an interactive assurance process info-graphic
  * A new section describing the SCAL document was created
  * "Supplier assurance process" page (and associated menu item) was renamed to "Supplier Assurance Prerequisites and Requirements"
* Additional information in the DoS workflow overview section describing the recommendation for how a booking only service should be profiled
* A broken link in the DoS workflow section was fixed
* Fixed an incorrect release state for previous releases in the release notes

### 0.1.7 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.7   | PREVIEW | Alpha | Released | 05/04/2019   | Volatile

The 0.1.7 PREVIEW release has the following highlights:

* A Detailed work through of a complex workflow was added to the GP Connect section
* A new section for appointment management (Cancel and Rebook) was created
  * This includes a section on technical architecture and workflow
* New content for the demonstrator guidance was added

### 0.1.6 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.6   | PREVIEW | Alpha | Released | 20/02/2019   | Volatile

The 0.1.6 PREVIEW release has the following highlights:

* A new section in functional spec was created for GP Connect specific content
  * A page otlining the key requirements for UEC Consuming systems was created
  * A new page comparing GP connect to proprietary booking was added
* New content for the "Monitoring, Analytics and Reporting" was created
  * Including a key metrics specification
* Added a FAQ page into IG section
* Added a page on Authentication in Functional Spec section
* Updated DoS workflow example from GP Fed to UTC

### 0.1.5 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.5   | PREVIEW | Alpha | Released | 04/01/2019   | Volatile

The 0.1.5 PREVIEW release has the following highlights:
* New DoS subsite in functional specification was created
  * New content for "DoS overview" page
  * New page "Key requirements" was added
  * New page "Workflow overview" was added
  * "DoS workflow example" page was tidied up
  * New "DoS endpoints" pages were created
    * A page describing the existing approach to endpoints was created
    * a page describing the new approach to endpoints was created
    * a page explaining the new booking changes was created
    * Added a page with guidance on transfer of care and ITK messaging
* One of the examples in the "Get Slots" section of the "Workflow and Interactions" page was updated to reflect an evolution of the messaging spec
* Resolved issue with the large codeblock on the "Workflow and Interactions" page
* Some content was added to the "Appointment Management" page
* The FHIR messaging spec link was updated to the latest version (1.0.3-alpha)
<br>
<br>

### 0.1.4 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.4   | PREVIEW | Alpha | Released | 07/12/2018   | Volatile

The 0.1.4 PREVIEW release has the following highlights:
* Small update to the glossary
* Changed references to the specific "StratAuth" to a more generic "NHS Authentication Service" in the functional specification
* Added generic statement regarding reporting requirements
* Added reference to the IUC service specification in the UEC Landscape overview page
* Added content to the user stories overview page
* made the link to the FHIR profile website much more prominent by adding a clickable "specification version" to the sidebar. On clicking it links to the FHIR profile website
<br>
<br>

### 0.1.3 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.3   | PREVIEW | Alpha | Released | 16/11/2018   | Volatile

The 0.1.3 PREVIEW release has the following highlights:
* Created content for "Differences from GP Connect" in the Functional Specification secion.
* Fixed the TOC and some formatting for the release notes page
<br>
<br>

### 0.1.2 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.2   | PREVIEW | Alpha | Released    | 06/11/2018   | Volatile

The 0.1.2 PREVIEW release has the following highlights:

* some of the user story text has been updated
* The wording in "Serviceability" section of Non-Functional Requirements has been updated
* Content in the "Interactions with the DoS" page in Functional Specification section has been created
<br>
<br>

### 0.1.1 PREVIEW

Version | Handle  | Phase | State           | Release Date | Stability
--------|---------|-------|-----------------|--------------|----------------
0.1.1   | PREVIEW | Alpha | Released | 18/10/2018   | Volatile

The 0.1.1 PREVIEW release is the first release version of the UEC appointment booking standards. This version has the following highlights:

* Initial site structure and base content
* Background and context setting content
* User stories and scoping information
* Workflow and filtering slots content in the functional specification section
* non-functional requirements
* a link to the FHIR API specification
