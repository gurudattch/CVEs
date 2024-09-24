# Stored XSS vulnerability was discovered in Sourcecodester's Online Railway Reservation System (contact_us.php)
---
## CVE-2024-XXXX

Vulnerability Analysis:
---

Affected product: [Railway Reservation System](https://www.sourcecodester.com/php/15121/online-railway-reservation-system-phpoop-project-free-source-code.html)

Affected Component: /admin/inquiries/index.php

The page `http://localhost/orrs/?page=reserve&sid=1` has functionality to make reservation of tickets, but the insecure design of `/orrs/admin/?page=reservations` makes it vulnerable to send a malicious JavaScript code. Once the admin visits the Reservation page, the JavaScript code gets executed and can be used to steal the admin's cookies.

Explopotation:
---

1. Make a Ticket Reservation using `http://localhost/orrs/?page=reserve&sid=1`  with a XSS payload `<script>alert()</script>` in **firstname** & **mid name** & **lastname** area

![image](https://github.com/gurudattch/CVEs/blob/main/assets/31.png)

2. Now Login With Admin Account and vist for Reservations in Menu tab

![image](https://github.com/gurudattch/CVEs/blob/main/assets/32.png)

Successfully Got A alert message :)
