---
title: Endpoint Structure - booking changes
sidebar: dos_sidebar
keywords: specification
permalink: dos_endpoints_booking.html
toc: false
folder: dos
---

## Changes to support Appointment Booking

For appointment booking there is a new transport type, format and interaction. There are also two new address types, ASID and ODS.

The new items are listed below:

* Transport: http
* Format: FHIR
* Interaction: Scheduling
* address: and ODS or ASID referencing the AS Object in SDS for the booking endpoint for this service (with the form "ODS:xxxx" or "ASID:xxxx")

An example of how this will look in XML is below:


```xml
<ns1:serviceEndPoints>
  <ns1:EndPoint>
     <ns1:endpointOrder>1</ns1:endpointOrder>
     <ns1:transport>email</ns1:transport>
     <ns1:format>HTML</ns1:format>
     <ns1:interaction>urn:nhs-itk:interaction:primaryEmergencyDepartmentRecipientNHS111CDADocument-v2-0</ns1:interaction>
     <ns1:businessScenario>Primary</ns1:businessScenario>
     <ns1:address>an address</ns1:address>
     <ns1:isCompressionEnabled>uncompressed</ns1:isCompressionEnabled>
     <ns1:comment>a comment</ns1:comment>
  </ns1:EndPoint>
  <ns1:EndPoint>
     <ns1:endpointOrder>2</ns1:endpointOrder>
     <ns1:transport>http</ns1:transport>
     <ns1:format>FHIR</ns1:format>
     <ns1:interaction>Scheduling</ns1:interaction>
     <ns1:address>ASID:918999198999|or|ODS:ABC123</ns1:address>
     <ns1:comment>a comment</ns1:comment>
  </ns1:EndPoint>
</ns1:serviceEndPoints>
```

### Booking only Services

<div class="mxgraph" style="max-width:100%;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;nav&quot;:true,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;Electron\&quot; modified=\&quot;2019-10-31T11:00:36.664Z\&quot; agent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/12.1.7 Chrome/78.0.3905.1 Electron/7.0.0 Safari/537.36\&quot; etag=\&quot;mtzXSqoKcbRgunniNS3r\&quot; version=\&quot;12.1.7\&quot; type=\&quot;device\&quot; pages=\&quot;1\&quot;&gt;&lt;diagram id=\&quot;TTp8hsFlw5_qzt3Y8s8G\&quot; name=\&quot;Page-1\&quot;&gt;7Vpbc6M2GP01nmkfkuFisP3oW9LM3rLxbtvtS0cG2WgrEBUiNv31/QTiTmxvbceZNH4BfUhC0vnO4SDcM6f+9paj0PvAXEx7huZue+asZxj6qN+Hg4wkWcQwbDOLrDlxVa0ysCD/YBXUVDQmLo5qFQVjVJCwHnRYEGBH1GKIc7apV1sxWr9riNa4FVg4iLajvxFXeFl0aAzK+C+YrL38zro9yq74KK+sZhJ5yGWbSsic98wpZ0xkZ/52iqlcvXxdsnY3T1wtBsZxIA5pcDt8+OzM/xxO3aHx69j6/gfznCvVyyOisZrwPRJE9mhoM+yztYSVOJGagkjydYHZhPIU7o8oxVTW9HvmxBM+hbAOp5Hg7K9i1WC+kxBz4mOBebPhfXlhsvGIwIsQObL7DdwfYpzFgYtd1THijkoUXfYaZefatWFCaUUonTLKeDpOU18iHRvFaCpXNM2ej29kCxaISnyV/iCulgZzgbdPrrleIAkcwAwmwROoohpc6bZCX+X/QBU3ZS7pecyr5FHeDKn0XRddlwjDiQL5BwAftgBvQYtdYIAqMi48tmYBovMyWoFDg1JZ5z1jocLoOxYiUSihWLB6asDy8eR31T4tfEsRtPLibFu9OEuqpUqypMFsAnLUu1GCSbKYO3jH6lhKYRBfY7Gj3qgbdY4psOexPo4uCFXTe0ZSpqlsKUQvyTWwkQXZuFSrRiIUw/jvuWG1cuMLJ1IfmxlSp2MXYStYo2XEaCzwuGRtncP9Tq14UTw268BYHSzWOljcAvBkNLZfBI1PyLz82b6PedZZmHc1urb6o/JnWbuJmE2nRcRWv7rW7PiiBNeN15Y25xFi88JCPGrBNGMLCCwwfySwHrAwmILbBRBavqwlpFVHpkybv0193fWKso3jIS6uXRKFFCVPqPmL0uLCL+2wVF1ifDZLpbefmz3DpkItQw0f+++Y5ReuMuM6hgq6HW7Li3C2lsePeTcwrKynLH5Zx1aatG81j3YZx6abBz44dPs8UjGsZ2PhDZ5JKoxXJ+kZoicHyjIvq+l5olaAeph//nr3MJ98+vTu7uOtHIoQnCzBK/fMm5MpO3ZIRFhwmLSDShuO0yXtrr20LftEdrrxfDU7JLzf5af7Z9Pwl/FefEoa2YcK4+BIvh238O03mXEYShL62S7UJBYCsneH5fn/vY02pKywNvssUPPZdDIU8z3OV0SfwaH0OfYV5Dj6DPbRh0F+vnGmxRmzf2nO6O23vAe8wpwjmqpdCt9Pd1/ewQFWxNDmH8Z3739+g7IJZb/LPjyv/L267Tijf6SqdZvwgXVZE270W0DN1M4HpA/iAQnWUvQ9lGtnFvDjSAaWcuvFR648rFJOlqYETtXmzAV2ZJ7HtjdfofJd0n22fXQ23rUl9DQ7L1OPsUiijKjAPEACVwF+25TZpx6HmqfzbN82VQYetYfJzBgevkmlWmqkoqdvNNSsxo0an+CbH/iM5sBq9eEkG8FpNa9tEaeQtySIZVIv89crAvPU1hwnqZixWA47hmqy/7qlTGtKFbyG41dgRUUgQTHl+tXqp0LpFIwKmPAwr/JJg7xO/8GhBnV5g/M8etrM067PinrXNoj+44IKxfKvJllqlf/YMef/Ag==&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>

