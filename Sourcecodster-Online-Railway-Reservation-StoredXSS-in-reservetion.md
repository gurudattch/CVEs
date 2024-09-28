# Stored XSS vulnerability was discovered in Sourcecodester's Online Railway Reservation System (Ticket Reservation)
---
## CVE-2024-2299

Vulnerability Analysis:
---

Affected product: [Railway Reservation System](https://www.sourcecodester.com/php/15121/online-railway-reservation-system-phpoop-project-free-source-code.html)

Affected Component: `http://localhost/orrs/admin/?page=reservations`


The page `http://localhost/orrs/?page=reserve&sid=1` has functionality to make a Ticket Reservation by customer, but the insecure design of `http://localhost/orrs/?page=reserve&sid=1` makes it vulnerable to send a malicious JavaScript code. Once the admin visits the Reservations page, the JavaScript code gets executed and can be used to steal the admin's cookies.


Explopotation:
---

1. Make a Ticket Booking using `http://localhost/orrs/?page=reserve&sid=1`  with a XSS payload `<script>alert()</script>` in **firstname** & **midname**  & **lastname** area

![image](https://github.com/gurudattch/CVEs/blob/main/assets/31.png)

2. Now Login With Admin Account and vist for Reservations in Menu tab

![image](https://github.com/gurudattch/CVEs/blob/main/assets/32.png)

Successfully Got A alert message :)
