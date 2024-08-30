# Stored XSS vulnerability was discovered in Sourcecodester's Contact Manager with Export to VCF 1.0 (Contact Name)
---
CVE-2024-8337
---
Affected Project: Sourcecodester  Contact Manager with Export to VCF 1.0

Official Website: https://www.sourcecodester.com/php/17556/contact-manager-export-vcf-using-php-and-mysql-source-code.html
Version: 1.0

Releted Code: index.html
*Line Number: 105*
```
<thead>
<tr>
 <th scope="col">Contact ID</th>
 <th scope="col">Name</th>
 <th scope="col">Phone Number</th>
 <th scope="col">Email</th>
 <th scope="col">Action</th>
 </tr>
</thead>
```
---

Add the XSS payload in **Contact Name Field**

![image1](https://github.com/gurudattch/CVEs/blob/main/assets/11.png)

---

Add Contact

![image2](https://github.com/gurudattch/CVEs/blob/main/assets/12.png)
