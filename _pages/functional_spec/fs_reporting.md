---
title: Monitoring, Analytics and Reporting
sidebar: overview_sidebar
keywords: specification
permalink: fs_reporting.html
toc: false
folder: functional_spec
---

It is expected that there should be a capability to report against expected national metrics for appointment booking and a clear mechanism to share these data with commissioners and other key stakeholders.

The below tables identify the key metrics required to meet the national commissioning reporting requirements as well the most common local operational reporting and performance metrics. This specification is still in draft and is developing and evolving.

{% include table-collapsible.html %} 
<p>

<!------------------------------------------------------------------------------------------------------->  
<!------------------------------------------------------------------------------------------------------->  
<!-----------------------------------------------TABLE-1------------------------------------------------->       
<!------------------------------------------------------------------------------------------------------->  
<!------------------------------------------------------------------------------------------------------->

<div class="wrap-collabsible">
  <input id="collapsible1" class="toggle" type="checkbox">
  <label for="collapsible1" class="lbl-toggle">UEC Booking Reporting Requirements - Consumer</label>
  <div class="collapsible-content">
    <div class="content-inner">
      <p>        
      <table class="pure-table pure-table-bordered"> 
            <thead>
              <tr>
                <th data-field="ID" data-sortable="true">Requirement ID</th>
                <th data-field="REQUIREMENT" data-sortable="true">Requirement</th>
                <th data-field="OUTPUT" data-sortable="true">Which will produce the following data....</th>                
              </tr>
            </thead>
        <tbody>   
       <!------------------------------ROW----------------------------------->   
              <tr>
                <td>rep-cons-01</td>
                <td>Number of appointments successfully booked vs number of successful referrals. Grouped by each service selected or patients registered practice, over a date range</td>
                <td>In December there were 2000 appointments booked in total, 50 for practice A, 32 for practice B etc..</td>      
              </tr>      
      <!------------------------------ROW----------------------------------->         
              <tr>
                <td>rep-cons-04</td>
                <td>Number of appointments not booked where there were no slots presented to the user and a successful referrals was made over a date range. Grouped by each service selected or patients registered practice</td>
                <td>In December there were 200 appointments not been able to be made as the appointment slots were not available, but a referral to the service was made.</td>      
              </tr>
      <!------------------------------ROW----------------------------------->   
              <tr>
                <td>rep-cons-05</td>
                <td>Number of appointments not booked where there were slots presented to the user and a successful referral was made over a date range. Grouped by each service selected or patients registered practice</td>
                <td>In December there were 100 appointments not been able to be made but some appointment slots were available, but a referral to the service was made</td>      
              </tr>     
      <!------------------------------ROW----------------------------------->   
              <tr>
                <td>rep-cons-07</td>
                <td>Number of appointments where an attempt to book into an offered slot failed because it was no longer available when the booking was made. Grouped by each service selected or patients registered practice</td>
                <td>In December there were 25 appointments not been able to be made successfully after the initial pre-allocation stage</td>      
              </tr>
      <!------------------------------ROW----------------------------------->   
              <tr>
                <td>rep-cons-08</td>
                <td>Number of times a user rejected the top DOS entry where the top DOS entry would allow the user to book an appointment over a date range</td>
                <td>In December there were 52 times where the user did not select the top service and the top service had an option to book appointment</td>      
              </tr>
      <!------------------------------ROW----------------------------------->   
              <tr>
                <td>rep-cons-09</td>
                <td>Number of times that a user tried to book an appointment and got an error message over a date range. Grouped by error message</td>
                <td>In December there were 2 times where the appointment booking button was clicked and an error occurred</td>      
              </tr>
      <!------------------------------ROW----------------------------------->   
              <tr>
                <td>rep-cons-10</td>
                <td>Number of times that a user books an appointment and the subsequently cancelled the appointment over a date range</td>
                <td>In December there were 7 times a user booked an appointment and then cancelled it whilst the patient was on the phone</td>      
              </tr>
      <!------------------------------ROW----------------------------------->   
              <tr>
                <td>rep-cons-11</td>
                <td>Number of times that a user books an appointment and the subsequently re-books the appointment over a date range</td>
                <td>In December there were 8 times a user booked an appointment and then re-books it whilst the patient was on the phone</td>      
              </tr>
      <!------------------------------ROW----------------------------------->   
              <tr>
                <td>rep-cons-12</td>
                <td>Number of times that a user books an appointment and the subsequently cancelled the appointment over a date range</td>
                <td>In December there were 8 times a user booked an appointment and then cancels it when the patient calls back</td>     
              </tr>
            </tbody>
      </table> 
      </p>
    </div>
  </div>
</div>

<p>
<!------------------------------------------------------------------------------------------------------->  
<!------------------------------------------------------------------------------------------------------->  
<!-----------------------------------------------TABLE-2------------------------------------------------->       
<!------------------------------------------------------------------------------------------------------->  
<!------------------------------------------------------------------------------------------------------->  
<div class="wrap-collabsible">
 <input id="collapsible2" class="toggle" type="checkbox">
 <label for="collapsible2" class="lbl-toggle">UEC Booking Reporting Requirements - Provider</label>
 <div class="collapsible-content">
    <div class="content-inner">
      <p>        
      <table class="pure-table pure-table-bordered"> 
            <thead>
              <tr>
                <th data-field="ID" data-sortable="true">Requirement ID</th>
                <th data-field="REQUIREMENT" data-sortable="true">Requirement</th>
                <th data-field="OUTPUT" data-sortable="true">Which will produce the following data....</th>                
              </tr>
            </thead>
            <tbody>
      <!------------------------------ROW----------------------------------->   
              <tr>
                <td>rep-prov-01</td>
                <td>Number of appointments successfully booked in over a date range</td>
                <td>In December there were 20 appointments booked</td>      
              </tr>
      <!------------------------------ROW----------------------------------->   
               <tr>
                <td>rep-prov-02</td>
                <td>Number of appointments successfully booked vs number of successful referrals over a date range</td>
                <td>In December there were 20 appointments booked and 25 referrals, showing that we have a 80% booking utilisation rate</td>      
              </tr>
      <!------------------------------ROW----------------------------------->   
              <tr>
                <td>rep-prov-03</td>
                <td>Number of appointments successfully booked and number of appointment slots made available over a date range</td>
                <td>In December there were 20 appointments booked and there were 30 appointment slots available</td>      
              </tr>      
      <!------------------------------ROW----------------------------------->   
              <tr>
                <td>rep-prov-06</td>
                <td>Number of appointments not booked vs number of successful referrals over a date range</td>
                <td>In December there were 20 appointments booked and 50 referrals, showing that we have a 20% non-booking utilisation rate for this service</td>      
              </tr> 
      <!------------------------------ROW----------------------------------->   
              <tr>
                <td>rep-prov-13</td>
                <td>Number of times that appointments were subsequently cancelled over a date range</td>
                <td>In December there were 7 times an appointment was cancelled</td>      
              </tr>
      <!------------------------------ROW-----------------------------------> 
        </tbody>
      </table> 
      </p>
    </div>
  </div>
 </div>
 

<p>  
<h2>Future Requirements</h2>
<p>
<br>
The items in the following table are expected to become requirements in the near future: 
<p>
<!------------------------------------------------------------------------------------------------------->  
<!------------------------------------------------------------------------------------------------------->  
<!-----------------------------------------------TABLE-3------------------------------------------------->       
<!------------------------------------------------------------------------------------------------------->  
<!------------------------------------------------------------------------------------------------------->  
<div class="wrap-collabsible">
 <input id="collapsible3" class="toggle" type="checkbox">
 <label for="collapsible3" class="lbl-toggle">UEC Booking Reporting Requirements - Provider</label>
 <div class="collapsible-content">
    <div class="content-inner">
      <p>        
      <table class="pure-table pure-table-bordered"> 
            <thead>
              <tr>
                <th data-field="ID" data-sortable="true">Requirement ID</th>
                <th data-field="REQUIREMENT" data-sortable="true">Requirement</th>
                <th data-field="OUTPUT" data-sortable="true">Which will produce the following data....</th>                
              </tr>
            </thead>
            <tbody>
      <!------------------------------ROW----------------------------------->   
            <tr>
             <td>rep-cons-15</td>
             <td>Number of appointments successfully booked and number of appointment slots available that would not cause a breach over a date range</td>
             <td>In December there were 200 “DX05” appointments booked and there were 400 appointment slots available that would not cause a breach.</td>      
            </tr>
  <!------------------------------ROW----------------------------------->   
            <tr>
             <td>rep-cons-16</td>
             <td>Number of appointments successfully booked and number of appointment slots available that would cause a breach over a date range</td>
             <td>In December there were 200 “DX05” appointments booked and there were 800 appointment slots available that would cause a breach.</td>      
            </tr>   
  <!------------------------------ROW----------------------------------->   
            <tr>
             <td>rep-cons-06</td>
             <td>Number of appointments not booked where there were slots presented to the user, but the slots would have caused a breach and a successful referrals was made over a date range</td>
             <td>In December there were 30 appointments not been able to made but the appointment slots that were available were outside of the disposition time frame</td>      
            </tr>
        </tbody>
       </table> 
      </p>
    </div>
  </div>
 </div>
 
<p>
  
<br>
  
<h2>Sharing Mechanism</h2>

<br>
<p> 
We are expecting that existing arrangements for sharing metrics are utilised. There may be a possibility that an API standard for data sharing will be published in the future.
