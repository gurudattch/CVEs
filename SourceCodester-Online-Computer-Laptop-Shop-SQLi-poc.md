# SQL Injection vulnerability was discovered in Sourcecodester's Online Computer and Laptop Store. (user registration)
---
## CVE-2024-XXXX
---

Affected Project: Online Computer and Laptop Store

Official Website: [Online Computer and Laptop Store](https://www.sourcecodester.com/php/16397/online-computer-and-laptop-store-using-php-and-mysql-source-code-free-download.html)

Version: 1.0

Related Code file: `/php-ocls/classes/Master.php`

Injection parameter: `email`

Vulnerability Analysis
---
1. Use of Plain SQL Queries: The script likely uses plain SQL queries to interact with the database. Without prepared statements, this approach is highly vulnerable to SQL injection.
2. The email variable is directly inserted into the SQL query without any escaping or parameterization. An attacker could inject malicious SQL code by manipulating the email field. in (line number 390 of Master.php)
The email is directly inserted into the SQL query without escaping or validation:

![vuln-code]([https://github.com/gurudattch/](https://github.com/gurudattch/CVEs/blob/main/assets/7.png))


```
(Backend Log for SQL injection)
[Fri Aug 30 20:24:40 2024] 192.168.192.128:56326 [500]: POST /php-ocls/classes/Master.php?f=register - Uncaught mysqli_sql_exception:
You have an error in your SQL syntax; check the manual that corresponds to your
MariaDB server version for the right syntax to use near 'myname' , `lastname`='myLname' ,
`contact`='1234567890' , `gender`='Male' , `...' at line 1 in /home/kali/CVE-TEST/php-ocls/classes/Master.php:390                                                                                                                               
Stack trace:                                                                                                                            
#0 /home/kali/CVE-TEST/php-ocls/classes/Master.php(390): mysqli->query()                                                                
#1 /home/kali/CVE-TEST/php-ocls/classes/Master.php(651): Master->register()                                                             
#2 {main}                                                                                                                               
  thrown in /home/kali/CVE-TEST/php-ocls/classes/Master.php on line 390   
```

---

Expolitation
---

1. click of Login or follow this path (http://192.168.192.128/php-ocls/login) Click on **Login**  now click on **Create Account**

![image8](https://github.com/gurudattch/CVEs/blob/main/assets/7-.png)

---

3. Fill the form and intercept the POST request in burp and copy the request

![image9](https://github.com/gurudattch/CVEs/blob/main/assets/8.png)

---

5. Store this request in a .txt file eg: register_req.txt

![image10](https://github.com/gurudattch/CVEs/blob/main/assets/9.png)

---

7. Run sqlmap
   
`sqlmap -r register_req.txt -p email`

![image](https://github.com/gurudattch/CVEs/blob/main/assets/10.png)

