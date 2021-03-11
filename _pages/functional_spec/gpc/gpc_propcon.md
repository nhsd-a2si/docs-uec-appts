---
title: GP Connect - Comparison with proprietary booking
sidebar: overview_sidebar
keywords: specification
permalink: gpc_propcon.html
toc: false
folder: functional_spec
---

### Branch Surgeries

*	GP IT systems do not have the concept of ‘main’ and ‘branch’ surgeries.  
*	The SPINE does not have the concept of ‘branch’ surgeries and therefore ‘branch’ surgery ODS codes

### Booking into GP surgeries main/branch surgeries using GP Connect standards

* The user will search for a GP surgery using PDS
*	They will retrieve the surgery (i.e. main surgery) 
*	When searching the DOS they will retrieve the patient’s home (i.e. main surgery) based on the ODS code retrieved using PDS and the ODS code on DOS
*	When they search for appointments they will be displayed with a list of appointments by location
*	When using GP Connect you are also performing a patient check at the same time, with this the 111 system will receive information on the patient’s preferred surgery 
*	The preferred surgery can then be list as the top surgery to book into 

### Booking into GP surgeries main/branch surgeries using Proprietary standards

*	The user will search for a GP surgery using PDS
*	They will retrieve the surgery (i.e. main surgery) 
*	When searching the DOS they will retrieve the patient’s home (i.e. main surgery) based on the ODS code retrieved using PDS and the ODS code on DOS
*	When they search for appointments they will be displayed with a list of appointments by location
*	Booking into EMIS surgeries
  *	From Adastra, 
    *	you will receive a list of locations that you can book into
    *	the user will then need to book the patient into the correct / appropriate surgery 
  *	From Cleric
    * you will receive a list of locations that you can book into
  * the user will then need to book the patient into the correct / appropriate surgery
*	Booking into TPP surgeries
  * From Adastra, 
    * you will receive a list of locations that you can book into.  NOTE: the list of locations will only appear if you have v3.28 of Adastra
    *	the user will then need to book the patient into the correct / appropriate surgery 
   *	From Cleric
    *	you will receive a list of locations that you can book into
    *	the user will then need to book the patient into the correct / appropriate surgery
