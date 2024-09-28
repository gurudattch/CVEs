# A Insecure Direct Reference Object (IDOR) was Found in Sourcecodester's Online Railway Reservation System
---

The online railway Reservation System by Sourcecoderster is vulnerable with IDOR, where a Unauthorized person can view and dowlnoad tickets of any other user by just manuplating ticket ids.

## CVE-2024-9298

Affected Product: [Online Railway Reservation System](https://www.sourcecodester.com/php/15121/online-railway-reservation-system-phpoop-project-free-source-code.html)
Affected Version: 1.0 

Affected Endpoint:  `http://localhost/orrs/?page=tickets&ids=*`
by Just replacing the **ids** parameter value anyone can view and print other users tickets
