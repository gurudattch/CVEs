A SQL injection vulnerability was discovered in Sourcecodester's 101+ News Station (News Portal) Comment Section **name** parameter was vulnerable with blind time based SQL injection

Product: https://www.sourcecodester.com/php/16067/best-online-news-portal-project-php-free-download.html

Affected Code: /news-details.php
Line : 19
![](https://github.com/gurudattch/CVEs/blob/main/assets/25.png)

---

![](https://github.com/gurudattch/CVEs/blob/main/assets/26.png)

POC:

1. Download and setup the portal
2. visit any post and make a comment by following step
3. add SQLinjection payload  `' AND (SELECT 7178 FROM (SELECT(SLEEP(20)))MFQU) AND 'aOrZ'='aOrZ` in **name** field 
  
4. add any valid email and comment and hit submit 
5. Observe the SQLi
