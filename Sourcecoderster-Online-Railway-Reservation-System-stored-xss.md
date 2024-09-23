# Stored XSS vulnerability was discovered in Sourcecodester's Online Railway Reservation System (contact_us.php)
---
## CVE-2024-XXXX

Vulnerability Analysis:
---

Affected product: [Railway Reservation System](https://www.sourcecodester.com/php/15121/online-railway-reservation-system-phpoop-project-free-source-code.html)

Affected Component: /admin/inquiries/index.php

The page `contact_us.php` has functionality to send inquiries of customers to the admin, but the insecure design of `/admin/inquiries/index.php` makes it vulnerable to send a malicious JavaScript code. Once the admin visits the inquiries page, the JavaScript code gets executed and can be used to steal the admin's cookies.

The index.php file is vulnerable to XSS attacks.
 XSS: The `<?= ucwords($row['fullname']) ?>, <?= ($row['email']) ?>, and <?= ($row['message']) ?>` code is vulnerable to XSS attacks because it directly outputs user-input data without proper sanitization or encoding.

Explopotation:
---

1. Make a Inquiry using `http://localhost/orrs/?page=contact_us`  with a XSS payload `<script>alert()</script>` in **full name** & **message** area

![image](https://github.com/gurudattch/CVEs/blob/main/assets/29.png)

2. Now Login With Admin Account and vist for Inquiries in Menu tab

![image](https://github.com/gurudattch/CVEs/blob/main/assets/30.png)

Successfully Got A alert message :)
