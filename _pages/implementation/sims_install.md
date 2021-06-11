---
title: TKW Simulators - Installing and Using
sidebar: overview_sidebar
keywords: install
permalink: sims_install.html
toc: false
Summary: "Install Simulators"
folder: implementation
---

The TKW (ToolKit Workbench) Simulators are tools to assist with developing and assuring a solution to meet the Booking Standard. 
There are two tools in the suite, to support the Provider and Consumer functionality, and they can utilised locally or in the dedicated environments – OpenTest, DEV or INT. 
When utlised within the dedicated environments they are supported by the other services – DoS, SDS and SSP – to replicate as near to like-live scenarios as possible.

## What are they?
Fundamentally, the TKW Simulators are (Docker) containers which neatly package all required resources, irrespective of the environment they are run on. 
There are two containers (Provider and Consumer) to replicate the different aspects of functionality and links to each of them can be found under the Resources section below. 

## Resources 
Resources required to understand and run the TKW Simulators 

### Docker 
Docker [download](https://www.docker.com/get-started)

### TKW Simulators Downloads
<div class="mxgraph" style="max-width:100%;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2021-01-25T18:06:48.120Z\&quot; agent=\&quot;5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36\&quot; etag=\&quot;CIH8QXnzlfbMLBZf-Mx0\&quot; version=\&quot;14.2.5\&quot; type=\&quot;browser\&quot;&gt;&lt;diagram id=\&quot;0rGeIxIf9BzHkJq4VMga\&quot; name=\&quot;Page-1\&quot;&gt;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&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>

# Deploying 
When starting to build a solution the TKW Simulators can be deployed locally, to validate the requests and responses made by either Providers or Consumers. This section will explain how to deploy and later sections will go on to explain how to use the tool.

## Windows
<details>
<summary>Click to see step-by-step setup guide</summary>
<div class="expanded-class" markdown="1">
 
### Prerequisites 
* Install Docker
   * [Windows 10 Pro](https://docs.docker.com/docker-for-windows/install/)
   * [Windows 10 home](https://docs.docker.com/docker-for-windows/install-windows-home/)

### Download Containers 
* Launch Powershell (local user)
* Run the following to download the Container(s)
   * Provider - *docker pull nhsdigitalmait/tkw_uec_provider_simulator*
   * Consumer - *docker pull nhsdigitalmait/tkw_uec_consumer_simulator*

### Run Containers 
*  Create Docker compose (.yml) files to instantiate the Containers

* **Provider**
   * Copy ‘**docker-compose_provider_simulator.yml**’ from [here](https://github.com/nhsdigitalmait/FHIR_111_UEC)
   * Update volume references to local resources – see Appendix1 
      * NB: The section after the colon (:) should not be altered because this is used by the Container
   * Save file 
   * Run the following from Powershell – *docker-compose -f docker-compose_provider_simulator.yml up*
   * The Provider Simulator will start and report ‘*ITK Testbench ready*’ when successfully running

* **Consumer**
   * Copy ‘**docker-compose_consumer_simulator.yml**’ from [here](https://github.com/nhsdigitalmait/FHIR_111_UEC)
   * Update volume references to local resources – see Appendix2
      * NB: The section after the colon (:) should not be altered because this is used by the Container
   * Save file 
   * Go to folder location ….Config/FHIR_111_UEC/autotest_config/endpoint_configs
   * Create an endpoint config file named '**200000000359.sh**', with 200000000359 being the ASID of the test service, and amend the required configuration (only to_ep for a local install), see Appendix6  
   * Save the **200000000359.sh** file 
   * Create batch file ‘**run_consumer_test.cmd**’ to instantiate the Container and run the various Consumer test routines – see Appendix3 for an example
   * Run Command
   * Call the batch file specifying the test routine required 
      * *run_consumer_test.cmd \<ASID\> \<Routine\>*
      * See further detail in the Using TKW section below 
   * Once execution is complete check the auto_tests folder and autotest logs folders for the test results and logs
</div>
</details>

## Mac
<details>
<summary>Click to see step-by-step setup guide</summary>
<div class="expanded-class" markdown="1">
 
### Prerequisites 
* [Install Docker](https://docs.docker.com/docker-for-mac/install/)
* [Test Installation](https://hub.docker.com/editions/community/docker-ce-desktop-mac/)

### Download Containers 
* Launch Terminal
* Download Container(s)
   * Provider - *docker pull nhsdigitalmait/tkw_uec_provider_simulator*
   * Consumer - *docker pull nhsdigitalmait/tkw_uec_consumer_simulator*

### Run Containers 
*  Create Docker compose (.yml) files to instantiate the Containers

* **Provider**
   * Copy ‘**docker-compose_provider_simulator.yml**’ and ‘**run_provider_simulator.sh**’ from [here](https://github.com/nhsdigitalmait/FHIR_111_UEC)
   *	Now edit **docker-compose_provider_simulator.yml**
   *	The section under 'volumes' requires amending such that the folder locations preceding the colon (:) refer to folders on the machine running the Docker Container, see Appendix4
      * NB: The section after the colon (:) should not be altered because this is used by the Container
   *	Save **docker-compose_provider_simulator.yml**
   *	Open a Terminal session
   *	Execute *run_provider_simulator.sh*
   *	The provider simulator container will now launch in Docker
   * The Provider Simulator will start and report ‘*ITK Testbench ready*’ when successfully running


* **Consumer**
   * Copy ‘**docker-compose_consumer_simulator.yml**’ and ‘**run_consumer_simulator.sh**’ from [here](https://github.com/nhsdigitalmait/FHIR_111_UEC)
   * Now edit **docker-compose_consumer_simulator.yml**
   * The section under 'volumes' requires amending such that the folder locations preceding the colon (:) refer to folders on the machine running the Docker Container, see Appendix5.
      * NB: The section after the colon (:) should not be altered because this is used by the Container
   * Go to …Config/FHIR_111_UEC/autotest_config/endpoint_configs
   * Create an endpoint config file named '**200000000359.sh**', with 200000000359 being the ASID of the test service, and amend the required configuration (only to_ep for a local install) see Appendix6
   * Save the **200000000359.sh**
   * Open a Terminal session
   * Execute *run_consumer_simulator.sh* file specifying the test routine required 
      * *run_consumer_test.sh \<ASID\> \<Routine\>*
      * See further detail in the Using TKW section below 
   * Once execution is complete check the auto_tests folder and autotest logs folders for the test results and logs
</div>
</details>

# Using TKW Simulators
The TKW Provider and Consumer Simulators will interact with each. It is advisable to set them up like that initially to ensure they’re working before proceeding to use them to test any other implementation. 
This section will explain how they’re intended to be used and their functionality.

## Consumer 
The TKW Consumer Simulator will test a Provider endpoint and is capable of running in three modes – 
* All test suites (see Test Suites section below)
   * e.g. *./run_consumer_simulator.sh \<toAsid\>*
* Single test suite (see Test Suites section below)
   * e.g. *./run_consumer_simulator.sh \<toAsid\> [A S B C]*
* Single test within a test suite (see Appendix7 for individual test names)
   * e.g. *./run_consumer_simulator.sh -s \<toAsid\> \<TestName\>*

The simulator is instantiated by running either a batch (Windows) or shell (Mac) file, the mode being defined by the parameters assigned. It will perform the requested tests and output a validation report for review under '..\auto_tests\\<ASID\>\'.

There are logs of activity of the Consumer Simulator under ‘..\autotest_logs’.

**NB: To point the TKW Consumer Simulator at the Provider solution to be tested edit the \<ASID\>.sh file in the ..\endpoint_configs folder, editing the ‘to_ep=\<provider solution endpoint\>’ value.**

### Test Suites
To run a single test suite, use the Initial value when invoking the Consumer Simulator.

|Initial|Test Suite|
|-------|----------|     
|A|cApability|
|S|Search for free slots|
|B|Book appointment|
|C|Cancel appointment|

## Provider
The TKW Provider Simulator is capable of testing a Consumer solution. As with any Provider system solution, it is passive and waits to accept requests. 

Once the container is up and running, reporting ‘*ITK Testbench ready*’, requests can be sent to it. The supplier's Consumer solution can be directed to the Provider Simulator, based on the address it was configured to listen via the Docker compose file - **docker-compose_provider_simulator.yml**.

The Provider Simulator can also be tested using an API Test Tool such as [Postman](https://www.postman.com/downloads/). A [collection](https://github.com/nhsdigitalmait/FHIR_111_UEC/blob/master/Postman_collection/FHIR_111-UEC.postman_collection.json) of all the requests which can be made to the Provider Simulator have been documented and can be imported into the Postman tool to assist seeing what the requests contain and envisage the eventual workflows.

A validation report of activity sent to the Provider Simulator resides under '..\all_evidence\\<ASID\>' and logs of activity is recorded in ‘..\logs’.

# Assuring with TKW
Another key feature of the TKW Simulator Tools is to assist with the self assurance process and provide the required evidence for the SCAL submission. Once the solution is complete, depending on whether it is fulfilling Provider or Consumer functionality, it can be configured to make or receive requests from the corresponding Simulator Tool. The Tool will record and collate the necessary evidence to be attached as part of the assurance process, as detailed in *Using TKW Simulators* section above. 

# Appendices 
<details>
<summary>Click to see step-by-step guide</summary>
<div class="expanded-class" markdown="1">

**Appendix1 – Docker Compose file for Provider Simulator (Windows)**
---
    version: '2.0'
    services:
    tkw_uec_provider_simulator:
        ports:
            - '4434:4434'
        volumes:
            - 'C:/Users/xxx/AppData/Local/Temp/assurance/scratch/data:/home/service/data'
            - 'C:/Users/xxx/AppData/Local/Temp/assurance/scratch:/home/service/fhir'
        image: 'nhsdigitalmait/tkw_uec_provider_simulator:0.5'

**Appendix2 – Docker Compose file for Consumer Simulator (Windows)**
---
    #
    #  docker-compose file supporting a docker stack comprised of a 
    #  111_uec consumer simulator suite instance 
    #
    version: "3"
    services:
    tkw_uec_consumer_simulator:
    image: nhsdigitalmait/tkw_uec_consumer_simulator:0.5

    environment:
      - TZ=Europe/London

    network_mode : "host"

    volumes:
        # <host path to mount> : <mount point within docker>
        # auto_tests folder
        - 'C:/Users/xxx/AppData/Local/Temp/config/FHIR_111_UEC/autotest_config/auto_tests:/home/service/TKW/config/FHIR_111_UEC/autotest_config/auto_tests'
        # endpoint_configs folder
        - 'C:/Users/xxx/AppData/Local/Temp/config/FHIR_111_UEC/autotest_config/endpoint_configs:/home/service/TKW/config/FHIR_111_UEC/autotest_config/endpoint_configs'
        # autotest logs folder
        - 'C:/Users/xxx/AppData/Local/Temp/config/FHIR_111_UEC/autotest_config/autotest_logs:/home/service/TKW/config/FHIR_111_UEC/autotest_config/autotest_logs'



**Appendix3 – Batch file to instantiate the Consumer Simulator**
---
    REM 
    REM invokes execution of tkw_uec_consumer_simulator in autotest mode to test Emeregncy Booking providers 
    REM 
    docker-compose -f docker-compose_consumer.yml run --rm tkw_uec_consumer_simulator %* 


**Appendix4 – Docker Compose file for Provider Simulator (Mac)**
---
    version: '2.0'
    services:
    tkw_uec_provider_simulator:
        ports:
            	- '4434:4434'
        volumes:
		- '/Users/xxx/Work/NHS-D/UEC/Testing/Data:/home/service/data'
		- '/Users/xxx/Work/NHS-D/UEC/Testing/Data:/home/service/fhir'
        image: 'nhsdigitalmait/tkw_uec_provider_simulator:0.5'


**Appendix5 – Docker Compose file for Consumer Simulator (Mac)**
---
    #
    #  docker-compose file supporting a docker stack comprised of a 
    #  111_uec consumer simulator (provider test suite) instance 
    #
    version: "3"
    services:
      tkw_uec_consumer_simulator:
      image: nhsdigitalmait/tkw_uec_consumer_simulator:0.5

    environment:
      - TZ=Europe/London

    network_mode : "host"

    volumes:
    # <host path to mount> : <mount point within docker>
    # auto_tests folder
    - /Users/xxx/Work/NHS-D/UEC/Testing/Config/FHIR_111_UEC/autotest_config/auto_tests:/home/service/TKW/config/FHIR_111_UEC/autotest_config/auto_tests
    # endpoint_configs folder
    - /Users/xxx/Work/NHS-D/UEC/Testing/Config/FHIR_111_UEC/autotest_config/endpoint_configs:/home/service/TKW/config/FHIR_111_UEC/autotest_config/endpoint_configs
    # autotest logs folder
    - /Users/xxx/Work/NHS-D/UEC/Testing/Config/FHIR_111_UEC/autotest_config/autotest_logs:/home/service/TKW/config/FHIR_111_UEC/autotest_config/autotest_logs

**Appendix6 - Endpoint configuration file example (default)**
---
    # Autotest endpoint config file
    #
    # to local clear
    to_ep=http://localhost:4434/STU3
    #to_ep=http://localhost/STU3
    
    # to local secure
    #to_ep=https://localhost:4431/STU3
    # to local via reverse proxy
    #to_ep=http://192.168.1.112/STU3 
    
    # defaults
    #toasid=200000000359
    #fromasid=200000000359
    #sendtls=No
    #truststore=/TKW_ROOT/config/FHIR_111_UEC/autotest_config/endpoint_configs/certs/opentest.jks
    #keystore=/TKW_ROOT/config/FHIR_111_UEC/autotest_config/endpoint_configs/certs/vpn-client-1003.opentest.hscic.gov.uk.jks

**Appendix7 - Endpoint configuration file example (default)**
---

|Test Name|Test Group|Short Description|
|---------|----------|-----------------|
|Capability_xml_accept|Capability|Request capability statement with a fhir+xml accept http header|
|Capability_json_accept|Capability|Request capability statement with a fhir+json accept http header|
|Capability_xml_parameter|Capability|Request capability statement with a xml \_format parameter|
|Capability_json_parameter|Capability|Request capability statement with a json \_format parameter|
|Capability_xml_parameter_json_accept|Capability|Request capability statement with  xml \_format parameter and a fhir+json accept http header|
|Capability_json_parameter_xml_accept|Capability|Request capability statement with  json \_format parameter and a fhir+xml accept http header|
|SFFSWithValidParameters_parameter_json|Search For Free Slots|Search for free slots with a json \_format parameter|
|SFFSWithValidParameters_header_json|Search For Free Slots|Search for free slots with a fhir+json http accept header|
|SFFSWithValidParameters_parameter_xml|Search For Free Slots|Search for free slots with a xml \_format parameter|
|SFFSWithValidParameters_header_xml|Search For Free Slots|Search for free slots with a fhir+xml http accept header|
|SFFSWithValidParameters_JWT_NoPractitioner|Search For Free Slots|Search for free slots with a JWT that does not contain a practitioner claim element|
|SFFSWithValidParameters_3_days	|Search For Free Slots|Search for free slots with a three day window from tomorrow to tomorrow+2|
|SFFSWithValidParameters_includes|Search For Free Slots|Search for free slots with added \_include parameters|
|SFFSNoSlots_HappyPath|Search For Free Slots|Search for free slots returning no slots|
|SFFSInvalid|Search For Free Slots|Search for free slots using an invalid request|
|SFFSForbidden|Search For Free Slots|Search for free slots forbidden repsonse|
|SFFSWrongMethod|Search For Free Slots|Search for free slots wrong method response|
|SFFSWithBusySlots|Search For Free Slots|Search for busy slots|
|BookAppointment_HappyPath|Book Appointment|Happy Path Appointment booking|
|BookAppointment_NoNHSNumber|Book Appointment|Happy Path Appointment booking where no patient nhs number is supplied|
|BookAppointment_SlotAlreadyBooked|Book Appointment|Attempt to book an already booked appointment|
|BookAppointment_FailedValidation|Book Appointment|Book an apppintment with an invalid request|
|BookAppointment_Invalid|Book Appointment|Book an apppintment with an invalid request|
|BookAppointment_Forbidden|Book Appointment|Book appointment forbidden response|
|BookAppointment_ServerError|Book Appointment|Book appointment server error response|
|BookAppointment_UnsupportedMediaType|Book Appointment|Book appointment requesting an unsupported media type|
|BookAppointment_BadGateway|Book Appointment|Book appointment bad gateway response|
|ReadNonExistentAppointment|Cancel Appointment|Read an appointment that does not exist|
|CancelAppointment_HappyPath|Cancel Appointment|Successfully cancel an appointment|
|CancelAppointment_DifferencesDetected|Cancel Appointment|Attempt to cancel an appointment supplying different appointment details|
|CancelAppointment_VersionConflict|Cancel Appointment|Attempt to cancel an appointment supplying incorrect version|
|CancelAppointment_If-MatchHeaderMissing|Cancel Appointment|Attempt to cancel an appointment without supplying an if match http header|
|CancelAppointment_ServerError|Cancel Appointment|Cancel appointment server error response|
|CancelAppointment_Forbidden|Cancel Appointment|Cancel appointment forbidden response|
|CancelAppointment_BadGateway|Cancel Appointment|Cancel appointment bad gateway response|
|CancelAppointment_GatewayTimeout|Cancel Appointment|Cancel appointment gateway timeout response|

	
**Appendix8 - Using TKW on the INT environment**
---
Navigate to - http://itw-work.itblab.nic.cfh.nhs.uk/Account/Register.aspx

Login with the following credentials - 
	Username = admin
	Password = uecbooking 
	
A
	
</div>
</details>
