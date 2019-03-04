---
title: Monitoring, Analytics and Reporting
sidebar: overview_sidebar
keywords: specification
permalink: fs_reporting.html
toc: false
folder: functional_spec
---

{% include note-notpublished.html %}

It is expected that there should be a capability to report against expected national metrics for appointment booking and a clear mechanism to share these data with commissioners and other key stakeholders.

The below table identifies the key metrics required to meet the national commissioning reporting requirements as well the most common local operational reporting and performance metrics. This specification is still in draft and is developing and evolving.

| *Requirement*                                                                                                                                                                   | *Which will provide the following information...*                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| Number of appointments successfully booked over a date range                                                                                                                   | In December there were 2000 appointments booked                                                                                                   |
| Number of appointments successfully booked vs number of successful referrals over a date range                                                                                 | In December there were 2000 appointments booked and 2500 referrals, showing that we have a 80% booking utilisation rate                           |
| Number of appointments successfully booked and number of appointment slots available over a date range                                                                         | In December there were 2000 appointments booked and there were 10,000 appointment slots available                                                 |
| Number of appointments successfully booked and number of appointment slots available that would not cause a breach over a date range                                           | In December there were 200 "DX05" appointments booked and there were 400 appointment slots available that would not cause a breach.               |
| Number of appointments successfully booked and number of appointment slots available that would cause a breach over a date range                                               | In December there were 200 "DX05" appointments booked and there were 800 appointment slots available that would cause a breach.                   |
| Number of appointments not booked vs number of successful referrals over a date range                                                                                          | In December there were 2000 appointments booked and 500 referrals, showing that we have a 20% non-booking utilisation rate                        |
| Number of appointments not booked where there were no slots presented to the user and a successful referrals was made over a date range                                        | In December there were 200 appointments not been able to made as the appointment slots were available                                             |
| Number of appointments not booked where there were slots presented to the user and a successful referrals was made over a date range                                           | In December there were 100 appointments not been able to made but some appointment slots were available                                           |
| Number of appointments not booked where there were slots presented to the user, but the slots would have caused a breach and a successful referrals was made over a date range | In December there were 30 appointments not been able to made but the appointment slots were available were outside of the disposition time frame  |
| Number of appointments where an attempt to book into an offered slot failed because it was no longer available when the booking was made                                       | In December there were 25 appointments not been able to be made successfully after the initial pre-allocation stage                               |
| Number of times a user rejected the top DOS entry where the top DOS entry would allow the user to book an appointment over a date range                                        | In December there were 52 times where the user did not select the top service and the top service had an option to book appointment               |
| Number of times that a user tried to book an appointment and got an error message over a date range                                                                            | In December there were 2 times where the appointment booking button was clicked and an error occurred                                             |
| Number of times that a user books an appointment and the subsequently cancelled the appointment over a date range                                                              | In December there were 7 times a user booked an appointment and then cancelled it whilst the patient was on the phone                             |
| Number of times that a user books an appointment and the subsequently re-books the appointment over a date range                                                               | In December there were 8 times a user booked an appointment and then re-books it whilst the patient was on the phone                              |


Regarding what the mechanism for sharing is, we are expecting that existing arrangements for sharing these metrics are utilised. There may be a possiblity that an API standard for data sharing will be published in the future.
