---
title: Principle of operation regarding times
sidebar: overview_sidebar
keywords: specification
permalink: fs_times.html
toc: false
folder: functional_spec
---

* All times included in the API messages MUST be in FHIR Instant format (```YYYY-MM-DDThh:mm:ss.sss+zz:zz```)
  * e.g. ```YearMonth-DayTHours:Minutes:Seconds+OffsetFromUTC``` 
  * e.g. ```201502-07T13:28:17.239+02:00```
* All times SHOULD be converted to UTC from local times (if not stored locally in UTC) before being included in any messages, this means the offset should be zero
* When receiving a time in a message a system MUST expect and handle a non UTC time (so an instant with a non-zero offset)
  * Therefore if a time is received that is not UTC, the receiver should convert the time back to UTC using the offset given (or their local time, if storing times locally in a local time)

{% include important.html content="This means both Consumer and Provider systems MUST be able to handle a time provided with an offset from UTC that differs from your local server time. As an illustration, if you store all times in UTC and someone uses a time specifying an offset, you will need to convert it to UTC when you store it." %}
