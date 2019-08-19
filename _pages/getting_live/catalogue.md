---
title: Supplier Conformance catalogue
sidebar: overview_sidebar
keywords: guidance
permalink: catalogue.html
toc: false
folder: getting_live
---

<link rel="stylesheet" href="https://unpkg.com/purecss@1.0.1/build/pure-min.css" integrity="sha384-oAOxQR6DkCoMliIh8yFnu25d7Eq/PHS21PClpwjOTeU2jRSq11vu66rf90/cZr47" crossorigin="anonymous">

<style>
    .wrap-collabsible {
    margin-bottom: 1.2rem 0;
  }

  input[type='checkbox'] {
    display: none;
  }

  .lbl-toggle {
    display: block;

    font-weight: bold;
    font-family: Verdana;
    font-size: 1.5rem;
    // text-transform: uppercase;
    text-align: left;

    padding: 5rem;
    padding-left: 2rem;

    color: #FFFFFF;
    background: #005EB8;

    cursor: pointer;

    border-radius: 7px;
    transition: all 0.25s ease-out;
  }

  .lbl-toggle:hover {
    color: #7C5A0B;
  }

  .lbl-toggle::before {
    content: ' ';
    display: inline-block;

    border-top: 5px solid transparent;
    border-bottom: 5px solid transparent;
    border-left: 5px solid currentColor;
    vertical-align: middle;
    margin-right: .7rem;
    transform: translateY(-2px);

    transition: transform .2s ease-out;
  }

  .toggle:checked + .lbl-toggle::before {
    transform: rotate(90deg) translateX(-3px);
  }

  .collapsible-content {
    max-height: 0px;
    overflow: hidden;
    transition: max-height .25s ease-in-out;
  }

  .toggle:checked + .lbl-toggle + .collapsible-content {
    max-height: 1600px;
  }

  .toggle:checked + .lbl-toggle {
    border-bottom-right-radius: 0;
    border-bottom-left-radius: 0;
  }

  .collapsible-content .content-inner {
    background: rgba(0, 0, 0, 0.01);
    border-bottom: 1px solid rgba(250, 224, 66, .45);
    border-bottom-left-radius: 7px;
    border-bottom-right-radius: 7px;
    padding: .5rem 1rem;
  }
</style>

<div class="wrap-collabsible">
  <input id="collapsible1" class="toggle" type="checkbox">
  <label for="collapsible1" class="lbl-toggle">IT supplier Booking Capabilities - GP Connect - Consumer</label>
  <div class="collapsible-content">
    <div class="content-inner">
      <p>        
      <table class="pure-table pure-table-bordered"> 
            <thead>
              <tr>
                <th data-field="ID" data-sortable="true">Item ID</th>
                <th data-field="Capability" data-sortable="true">Capability</th>
                <th data-field="Supplier" data-sortable="true">Supplier</th>
                <th data-field="Status" data-sortable="true">Status</th>
                <th data-field="Date" data-sortable="true">Date</th>
                <th data-field="Dependencies" data-sortable="true">Dependencies</th>
                <th data-field="Comments" data-sortable="true">Comments</th>
              </tr>
            </thead>
            <tbody>        
      <!------------------------------ROW----------------------------------->        
              <tr>
                <td rowspan="3">1</td>
                <td rowspan="3">Book an appointment - GP</td>
                <td>Advanced</td>
                <td>Complete</td>
                <td>July 2019</td>          
                <td rowspan="3">None</td>
                <td rowspan="3">Ability to search and book an appointment</td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Testing</td>
                <td>August 2019</td>         
              </tr>
              <tr>
                <td>Cleric</td>
                <td>Development</td>
                <td>October 2019</td>         
              </tr>
      <!------------------------------ROW----------------------------------->             
              <tr>
                <td rowspan="3">2</td>
                <td rowspan="3">Book an appointment - Hub</td>
                <td>Advanced</td>
                <td>Development</td>
                <td>September 2019</td>          
                <td rowspan="3">There is a dependency that all hubs work the same.  This work is not commissioned so would need to be followed through and scoped by BRAM</td>
                <td rowspan="3">Ability to search and book an appointment</td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Development</td>
                <td>September 2019</td>         
              </tr>
              <tr>
                <td>Cleric</td>
                <td>Development</td>
                <td>October 2019</td>         
              </tr>
      <!------------------------------ROW----------------------------------->             
              <tr>
                <td rowspan="3">3</td>
                <td rowspan="3">Cancel - During a consultation</td>
                <td>Advanced</td>
                <td>Complete</td>
                <td></td>          
                <td rowspan="3"></td>
                <td rowspan="3">Ability to cancel an appointment during a telephone call</td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Development</td>
                <td>September 2019</td>         
              </tr>
              <tr>
                <td>Cleric</td>
                <td>Development</td>
                <td>October 2019</td>         
              </tr>
      <!------------------------------ROW----------------------------------->             
              <tr>
                <td rowspan="3">4</td>
                <td rowspan="3">Cancel - After a consultation (Same 111 Provider)</td>
                <td>Advanced</td>
                <td>Development</td>
                <td>September 2019</td>          
                <td rowspan="3"></td>
                <td rowspan="3">Ability to cancel an appointment after the telephone call has been competed.  By the same 111 provider </td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Development</td>
                <td>September 2019</td>         
              </tr>
              <tr>
                <td>Cleric</td>
                <td>Development</td>
                <td>October 2019</td>         
              </tr>
      <!------------------------------ROW----------------------------------->             
              <tr>
                <td rowspan="3">5</td>
                <td rowspan="3">Temporary Register</td>
                <td>Advanced</td>
                <td>Development</td>
                <td>September 2019</td>          
                <td rowspan="3"></td>
                <td rowspan="3">When booking into a HUB/UTC and using a Primary Care IT System</td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Development</td>
                <td>September 2019</td>         
              </tr>
              <tr>
                <td>Cleric</td>
                <td>Development</td>
                <td>October 2019</td>         
              </tr>
      <!------------------------------ROW----------------------------------->             
              <tr>
                <td rowspan="3">6</td>
                <td rowspan="3">Appointment Warnings</td>
                <td>Advanced</td>
                <td>Not started</td>
                <td>TBC</td>          
                <td rowspan="3">This will be dependent on the NHS Pathways having a future version that provides this information</td>
                <td rowspan="3">Present a warning when booking outside a disposition timeframe</td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Not started</td>
                <td>N/A – Cleo only displays results within the disposition timeframe</td>         
              </tr>
              <tr>
                <td>Cleric</td>
                <td>Not started</td>
                <td>TBC</td>         
              </tr>
      <!------------------------------ROW----------------------------------->             
              <tr>
                <td rowspan="3">7</td>
                <td rowspan="3">Referral Suppression</td>
                <td>Advanced</td>
                <td>Development</td>
                <td>September 2019</td>          
                <td rowspan="3">This will be dependent on the DOS team completed the service attribute information and this being populated by the local DOS team </td>
                <td rowspan="3">When referring to a HUB</td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Development</td>
                <td>September 2019</td>         
              </tr>
              <tr>
                <td>Cleric</td>
                <td>Development</td>
                <td>October 2019</td>         
              </tr>
            </tbody>
      </table> 
      </p>
    </div>
  </div>
</div>

<div class="wrap-collabsible">
  <input id="collapsible2" class="toggle" type="checkbox">
  <label for="collapsible2" class="lbl-toggle">IT supplier Booking Capabilities - Care Connect - Consumer</label>
  <div class="collapsible-content">
    <div class="content-inner">
      <p>        
      <table class="pure-table pure-table-bordered"> 
            <thead>
              <tr>
                <th data-field="ID" data-sortable="true">Item ID</th>
                <th data-field="Capability" data-sortable="true">Capability</th>
                <th data-field="Supplier" data-sortable="true">Supplier</th>
                <th data-field="Status" data-sortable="true">Status</th>
                <th data-field="Date" data-sortable="true">Date</th>
                <th data-field="Dependencies" data-sortable="true">Dependencies</th>
                <th data-field="Comments" data-sortable="true">Comments</th>
              </tr>
            </thead>
            <tbody>        
      <!------------------------------ROW----------------------------------->        
              <tr>
                <td rowspan="3">1</td>
                <td rowspan="3">Book an appointment</td>
                <td>Advanced</td>
                <td>Development</td>
                <td>September 2019</td>          
                <td rowspan="3">None</td>
                <td rowspan="3">Ability to search and book an appointment</td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Not started</td>
                <td>November 2019</td>         
              </tr>
              <tr>
                <td>Cleric</td>
                <td>Development</td>
                <td>October 2019</td>         
              </tr>    
      <!------------------------------ROW----------------------------------->             
              <tr>
                <td rowspan="3">2</td>
                <td rowspan="3">Cancel - During a consultation</td>
                <td>Advanced</td>
                <td>Complete</td>
                <td></td>          
                <td rowspan="3"></td>
                <td rowspan="3">Ability to cancel an appointment during a telephone call</td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Not started</td>
                <td>November 2019</td>         
              </tr>
              <tr>
                <td>Cleric</td>
                <td>Development</td>
                <td>October 2019</td>         
              </tr>
      <!------------------------------ROW----------------------------------->             
              <tr>
                <td rowspan="3">3</td>
                <td rowspan="3">Cancel - After a consultation (Same 111 Provider)</td>
                <td>Advanced</td>
                <td>Development</td>
                <td>September 2019</td>          
                <td rowspan="3"></td>
                <td rowspan="3">Ability to cancel an appointment after the telephone call has been competed.  By the same 111 provider </td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Not started</td>
                <td>November 2019</td>         
              </tr>
              <tr>
                <td>Cleric</td>
                <td>Development</td>
                <td>October 2019</td>         
              </tr>     
      <!------------------------------ROW----------------------------------->             
              <tr>
                <td rowspan="3">4</td>
                <td rowspan="3">Appointment Warnings</td>
                <td>Advanced</td>
                <td>Not started</td>
                <td>TBC</td>          
                <td rowspan="3">This will be dependent on the NHS Pathways having a future version that provides this information</td>
                <td rowspan="3">Present a warning when booking outside a disposition timeframe</td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Not started</td>
                <td>TBD</td>         
              </tr>
              <tr>
                <td>Cleric</td>
                <td>Not started</td>
                <td>TBC</td>         
              </tr>
      <!------------------------------ROW----------------------------------->             
              <tr>
                <td rowspan="3">5</td>
                <td rowspan="3">Referral Suppression</td>
                <td>Advanced</td>
                <td>Development</td>
                <td>September 2019</td>          
                <td rowspan="3">This will be dependent on the DOS team completed the service attribute information and this being populated by the local DOS team </td>
                <td rowspan="3">When referring to a HUB</td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Development</td>
                <td>September 2019</td>         
              </tr>
              <tr>
                <td>Cleric</td>
                <td>Development</td>
                <td>October 2019</td>         
              </tr>
            </tbody>
      </table> 
      </p>
    </div>
  </div>
</div>

<div class="wrap-collabsible">
  <input id="collapsible3" class="toggle" type="checkbox">
  <label for="collapsible3" class="lbl-toggle">IT supplier Booking Capabilities - Care Connect - Provider</label>
  <div class="collapsible-content">
    <div class="content-inner">
      <p>        
      <table class="pure-table pure-table-bordered"> 
            <thead>
              <tr>
                <th data-field="ID" data-sortable="true">Item ID</th>
                <th data-field="Capability" data-sortable="true">Capability</th>
                <th data-field="Supplier" data-sortable="true">Supplier</th>
                <th data-field="Status" data-sortable="true">Status</th>
                <th data-field="Date" data-sortable="true">Date</th>
                <th data-field="Dependencies" data-sortable="true">Dependencies</th>
                <th data-field="Comments" data-sortable="true">Comments</th>
              </tr>
            </thead>
            <tbody>        
      <!------------------------------ROW----------------------------------->        
              <tr>
                <td rowspan="2">1</td>
                <td rowspan="2">Book an appointment</td>
                <td>EMIS</td>
                <td>TBC</td>
                <td>TBC</td>          
                <td rowspan="2"></td>
                <td rowspan="2">Ability to search and book an appointment</td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Not started</td>
                <td>November 2019</td>         
              </tr>                  
      <!------------------------------ROW----------------------------------->             
              <tr>
                <td rowspan="2">2</td>
                <td rowspan="2">Cancel an appointment</td>
                <td>EMIS</td>
                <td>TBC</td>
                <td>TBC</td>          
                <td rowspan="2"></td>
                <td rowspan="2">Ability to cancel an appointment</td>
              </tr>  
              <tr>
                <td>IC24</td>
                <td>Not started</td>
                <td>November 2019</td>         
              </tr>                   
            </tbody>
      </table> 
      </p>
    </div>
  </div>
</div>
