# A Improper Privilege Management Vulnerability Discovered in Sourcecoderster Online Railway Reservation System where a low privilege user (staff user) can perform Administrative action without any Authentication / Authorization 
---
## CVE-2024-9297

---

Affected product: [Railway Reservation System](https://www.sourcecodester.com/php/15121/online-railway-reservation-system-phpoop-project-free-source-code.html)

Affected Version: 1.0
Vulnerability Analysis:
---

1. Login as Admin and Add a Staff User: Login to the system as an administrator and create a new user with staff privileges.
2. Logout and Login as Staff: Logout from the admin account and login back to the system using the staff user account.
3. Verify Staff Options: As a staff member, you should only have access to three options:
 - Dashboard
 - Inquiries
 - Reservations
   
7. Access Admin Privileges: To access administrative privileges, use the following endpoints directly, which do not require authentication:

   1. `http://localhost/orrs/admin/?page=trains`
   2.  `http://localhost/orrs/admin/?page=schedules`
   3.  `http://localhost/orrs/admin/?page=user/manage_user`
   4.  `http://localhost/orrs/admin/?page=system_info`
   
   

