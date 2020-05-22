---
title: Support for booking only services
sidebar: dos_sidebar
keywords: specification
permalink: dos_bookingonly.html
toc: false
folder: dos
---

## Support for "booking only" type services

Some services that are profiled on the Urgent Care Directory of Services are comissioned as "booking only" services. 
This means that these services will only accept a referral if a booking has also been made for that patient. 

If no appointment is available then a referral should not be made. 

To achieve this, a "service attribute" is configurable against services. This will allow the service to be flagged as "booking only". Therefore if this attribute is present on the servicem all consumer systems should withold referrals.

### Workflow

An example workflow showing how this might be implemented is illustrated below:

<div class="mxgraph" style="max-width:100%;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;nav&quot;:true,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;Electron\&quot; modified=\&quot;2019-10-31T11:00:36.664Z\&quot; agent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/12.1.7 Chrome/78.0.3905.1 Electron/7.0.0 Safari/537.36\&quot; etag=\&quot;mtzXSqoKcbRgunniNS3r\&quot; version=\&quot;12.1.7\&quot; type=\&quot;device\&quot; pages=\&quot;1\&quot;&gt;&lt;diagram id=\&quot;TTp8hsFlw5_qzt3Y8s8G\&quot; name=\&quot;Page-1\&quot;&gt;7Vpbc6M2GP01nmkfkuFisP3oW9LM3rLxbtvtS0cG2WgrEBUiNv31/QTiTmxvbceZNH4BfUhC0vnO4SDcM6f+9paj0PvAXEx7huZue+asZxj6qN+Hg4wkWcQwbDOLrDlxVa0ysCD/YBXUVDQmLo5qFQVjVJCwHnRYEGBH1GKIc7apV1sxWr9riNa4FVg4iLajvxFXeFl0aAzK+C+YrL38zro9yq74KK+sZhJ5yGWbSsic98wpZ0xkZ/52iqlcvXxdsnY3T1wtBsZxIA5pcDt8+OzM/xxO3aHx69j6/gfznCvVyyOisZrwPRJE9mhoM+yztYSVOJGagkjydYHZhPIU7o8oxVTW9HvmxBM+hbAOp5Hg7K9i1WC+kxBz4mOBebPhfXlhsvGIwIsQObL7DdwfYpzFgYtd1THijkoUXfYaZefatWFCaUUonTLKeDpOU18iHRvFaCpXNM2ej29kCxaISnyV/iCulgZzgbdPrrleIAkcwAwmwROoohpc6bZCX+X/QBU3ZS7pecyr5FHeDKn0XRddlwjDiQL5BwAftgBvQYtdYIAqMi48tmYBovMyWoFDg1JZ5z1jocLoOxYiUSihWLB6asDy8eR31T4tfEsRtPLibFu9OEuqpUqypMFsAnLUu1GCSbKYO3jH6lhKYRBfY7Gj3qgbdY4psOexPo4uCFXTe0ZSpqlsKUQvyTWwkQXZuFSrRiIUw/jvuWG1cuMLJ1IfmxlSp2MXYStYo2XEaCzwuGRtncP9Tq14UTw268BYHSzWOljcAvBkNLZfBI1PyLz82b6PedZZmHc1urb6o/JnWbuJmE2nRcRWv7rW7PiiBNeN15Y25xFi88JCPGrBNGMLCCwwfySwHrAwmILbBRBavqwlpFVHpkybv0193fWKso3jIS6uXRKFFCVPqPmL0uLCL+2wVF1ifDZLpbefmz3DpkItQw0f+++Y5ReuMuM6hgq6HW7Li3C2lsePeTcwrKynLH5Zx1aatG81j3YZx6abBz44dPs8UjGsZ2PhDZ5JKoxXJ+kZoicHyjIvq+l5olaAeph//nr3MJ98+vTu7uOtHIoQnCzBK/fMm5MpO3ZIRFhwmLSDShuO0yXtrr20LftEdrrxfDU7JLzf5af7Z9Pwl/FefEoa2YcK4+BIvh238O03mXEYShL62S7UJBYCsneH5fn/vY02pKywNvssUPPZdDIU8z3OV0SfwaH0OfYV5Dj6DPbRh0F+vnGmxRmzf2nO6O23vAe8wpwjmqpdCt9Pd1/ewQFWxNDmH8Z3739+g7IJZb/LPjyv/L267Tijf6SqdZvwgXVZE270W0DN1M4HpA/iAQnWUvQ9lGtnFvDjSAaWcuvFR648rFJOlqYETtXmzAV2ZJ7HtjdfofJd0n22fXQ23rUl9DQ7L1OPsUiijKjAPEACVwF+25TZpx6HmqfzbN82VQYetYfJzBgevkmlWmqkoqdvNNSsxo0an+CbH/iM5sBq9eEkG8FpNa9tEaeQtySIZVIv89crAvPU1hwnqZixWA47hmqy/7qlTGtKFbyG41dgRUUgQTHl+tXqp0LpFIwKmPAwr/JJg7xO/8GhBnV5g/M8etrM067PinrXNoj+44IKxfKvJllqlf/YMef/Ag==&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>

### Example xml returned:

When requesting DoS service details with "CheckCapacitySummary" DoS API call, there is a section in the returned message for the additional attributes:

```xml
<ns1:attributes>
  <attribute>
    <dataType>string</dataType>
    <name>requirebooking</name>
    <description>The service only accepts referrals with an accompanying booked appointment.</description>
    <value>true</value>
  </attribute>
</ns1:attributes>
```

This attribute will have three possible states:

* not present
* present and false
* present and true

For the first two cases, it can be assumed that referrals can be made without a booking. Only if the attribute is *present* **and** *true* should a referral be witheld if there has been no booking.
