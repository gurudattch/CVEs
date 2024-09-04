# Unauthenticated Open Redirect Vulnerability was discovered in Sourcecodester's Clinic's Patient Management System - PHP 2.0 via congratulations.php 

Affected Project: Sourcecodester Clinic's Patient Management System - PHP 2.0

Official Website: [Sourcecodester Clinic's Patient Management System](https://www.sourcecodester.com/php-clinics-patient-management-system-source-code)

Version: 2.0



The issue lies in the fact that the $gotoPage variable is taken directly from the $_GET superglobal, which can be easily manipulated by an attacker. By crafting a malicious URL, an attacker can redirect users to any website, including ones that may be used for phishing or other malicious purposes.
affected code 
/congratulation.php
```
<?php 
        include './config/connection.php';

        $gotoPage = $_GET['goto_page'];
//the goto_page is redirecting everything
    $message = $_GET['message'];
        
        header("Location:$gotoPage?message=$message");

?>

```


![](https://github.com/gurudattch/CVEs/blob/main/assets/17.png)




POC
---

192.168.95.115/congratulation.php?goto_page=https://example.com

![](https://github.com/gurudattch/CVEs/blob/main/assets/18.png)
