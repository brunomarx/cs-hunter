# CS-Hunter Project

## **What is Cobalt Strike?**

Cobalt Strike is a **commercial penetration testing tool** often used to simulate **advanced persistent threats (APTs)**. It provides red teams and attackers with a platform for conducting complex operations, including **command-and-control (C2)** operations, lateral movement, and stealthy command execution.

Cobalt Strike uses a **beacon payload** that communicates with a **C2 server** (Command-and-Control), where attackers can issue commands, exfiltrate data, or perform lateral movement across a network.

In **adversary infrastructure hunting**, tools like **Shodan** help identify publicly accessible **Cobalt Strike Team Servers**, which are often abused by malicious actors. Security teams scan for and analyze these servers to mitigate potential threats.

---

## **Explanation of the Lists**

### **1. list_1.txt: IPs from Shodan Search**
This file contains **IP addresses identified via Shodan searches**. The searches are designed based on characteristics observed in **Cobalt Strike beacons** that communicate with known C2 servers. The IPs listed are potential **Cobalt Strike Team Servers** that require further scanning.

Example entry:
154.221.19.134


### **2. list_2.txt: Scanned IPs Returning Cobalt Beacons**
This file contains **IP addresses that have been scanned** and confirmed to be **Cobalt Strike Team Servers**. These servers are confirmed after scanning the IPs from `list_1.txt` using Nmap or another tool and detecting a **Cobalt Strike beacon**.

Example entry:
154.221.19.134


### **3. list_3.txt: Cobalt Strike Beacon C2 Server Information**
This file stores the **C2 server configuration** details extracted from the Cobalt Strike beacon. The information includes the **methods of communication (GET/POST), server URLs, polling intervals, beacon types**, and other relevant data about how the beacon contacts its C2 server.

Example entry based on the provided beacon:
C2 Server IP: shangde.co Communication Methods: GET, POST Polling Interval: 60000 ms Beacon Type: HTTPS x64 C2 Server URL: shangde.co/visit.js x86 C2 Server URL: shangde.co/updates.rss HTTP Method Path: /submit.php


### **4. list_4.txt: C2 Host Header in the Beacon**
This file contains the **C2 host header** information from the beacon. The **host header** is part of the HTTP requests that the beacon sends when communicating with the C2 server. This helps security teams understand how the beacon might be disguising its communication.

Example entry based on the provided beacon:
Host Header: Host: shangde.co


---

## **Example Beacon Breakdown**

Using a beacon as a sample, the following information can be extracted:

- The beacon was scanned on IP **154.221.19.134**, which was identified through a Shodan search and scanned using Nmap.
- The **C2 server** information includes:
  - **x64 C2 Server**: `shangde.co/visit.js`
  - **x86 C2 Server**: `shangde.co/updates.rss`
- The beacon uses **HTTP GET and POST methods** for both 32-bit and 64-bit systems.
- The **polling interval** is set to **60,000 milliseconds (60 seconds)**.
- The **Host Header** is: `Host: shangde.co`.

### **Corresponding List Entries**

#### **list_1.txt**
Contains the IP that was searched using Shodan and identified as a potential Cobalt Strike server:
154.221.19.134


#### **list_2.txt**
After the Nmap scan confirmed the presence of a Cobalt Strike beacon, the IP is added here:
154.221.19.134


#### **list_3.txt**
The details extracted from the beacon's configuration, including C2 server information and HTTP communication patterns:
C2 Server IP: shangde.co Communication Methods: GET, POST Polling Interval: 60000 ms Beacon Type: HTTPS x64 C2 Server URL: shangde.co/visit.js x86 C2 Server URL: shangde.co/updates.rss HTTP Method Path: /submit.php


#### **list_4.txt**
The beacon's **C2 host header** (if any):

Host Header: Host: shangde.co


---

## **Summary**

- **Cobalt Strike** is a powerful tool for penetration testing but is often misused by threat actors.
- **list_1.txt** contains potential IPs found via Shodan searches. 
- **list_2.txt** stores confirmed Cobalt Strike servers after scanning. It's a subset of list_1.txt
- **list_3.txt** holds configuration details of how the beacon communicates with its C2 server. It can also contain the ips of list_2.txt
- **list_4.txt** stores the host header used by the beacon during communication.



## Acknowledgment
Thank you!

- Shodan
- Censys
- https://github.com/drb-ra
- https://github.com/splunk/melting-cobalt
- https://github.com/whickey-r7
- @MichalKoczwara
