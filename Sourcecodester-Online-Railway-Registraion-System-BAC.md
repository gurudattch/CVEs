# Broken Access Control (Improper Access Control) vulnerability was discovered in SourceCoderster Online Railway Reservation System 
---
## CVE-2024-XXXX

Vulnerability Analysis:
---

Affected product: [Railway Reservation System](https://www.sourcecodester.com/php/15121/online-railway-reservation-system-phpoop-project-free-source-code.html)

Affected Endpoint: `orrs/admin/inquiries/view_details.php?id=*`

Vulnerability Analysis:
---

A Broken Access Control (Improper Access Control) vulnerability was discovered in SourceCoderster Online Railway Reservation System  where a unauthorized user and directly access inquiries submitted by users to Administrator This can be Demonstrated with this steps:

Affected Product: [Online Railway Reservation System](https://www.sourcecodester.com/php/15121/online-railway-reservation-system-phpoop-project-free-source-code.html)
 

Exploitation:
---

1. Directly Pointing to the http://your_host/orrs/admin/inquiries/view_details.php?id=*  
2. By Changing the Id  parameter value a Unauthorized User can directly Access The Inquiry


OR USE this Python Script:

