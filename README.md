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
47.97.79.97


### **2. list_2.txt: Scanned IPs Returning Cobalt Beacons**
This file contains **IP addresses that have been scanned** and confirmed to be **Cobalt Strike Team Servers**. These servers are confirmed after scanning the IPs from `list_1.txt` using Nmap or another tool and detecting a **Cobalt Strike beacon**.

Example entry:
47.97.79.97


### **3. list_3.txt: Cobalt Strike Beacon C2 Server Information**
This file stores the **C2 server configuration** details extracted from the Cobalt Strike beacon. The information includes the **methods of communication (GET/POST), server URLs, polling intervals, beacon types**, and other relevant data about how the beacon contacts its C2 server.

Example entry based on the provided beacon:
C2 Server IPs:

61.170.80.230/jquery-3.3.1.min.js
180.213.179.141/jquery-3.3.1.min.js
120.195.185.112/jquery-3.3.1.min.js
118.182.226.161/jquery-3.3.1.min.js
61.170.81.233/jquery-3.3.1.min.js
27.37.200.237/jquery-3.3.1.min.js
101.226.26.147/jquery-3.3.1.min.js


### **4. list_4.txt: C2 Host Header in the Beacon**
This file contains the **C2 host header information** from the beacon. The **host header** is part of the HTTP requests that the beacon sends when communicating with the C2 server. This helps security teams understand how the beacon might be disguising its communication.

Example entry based on the provided beacon:

---

## **Example Beacon Breakdown**

Using the beacon JSON provided, the following information can be extracted:

- The beacon was scanned on IP **47.97.79.97**, which was identified through a Shodan search and scanned using Nmap.
- The **C2 server** information includes:
  - **x64 C2 Servers**: `61.170.80.230/jquery-3.3.1.min.js`, `180.213.179.141/jquery-3.3.1.min.js`, `120.195.185.112/jquery-3.3.1.min.js`, `118.182.226.161/jquery-3.3.1.min.js`, `61.170.81.233/jquery-3.3.1.min.js`, `27.37.200.237/jquery-3.3.1.min.js`, `101.226.26.147/jquery-3.3.1.min.js`
  - **x86 C2 Servers**: Same as x64
- The beacon uses **HTTP GET and POST methods** for both 32-bit and 64-bit systems.
- The **polling interval** is set to **5987 milliseconds**.
- The **Host Header** is: `Host: haifang310.com`.

### **Corresponding List Entries**

#### **list_1.txt**
Contains the IP that was searched using Shodan and identified as a potential Cobalt Strike server:

47.97.79.97

#### **list_2.txt**
After the Nmap scan confirmed the presence of a Cobalt Strike beacon, the IP is added here:
47.97.79.97


#### **list_3.txt**
The details extracted from the beacon's configuration, including C2 server information and HTTP communication patterns:

C2 Server IPs:

61.170.80.230
180.213.179.141
120.195.185.112
118.182.226.161
61.170.81.233
27.37.200.237
101.226.26.147


#### **list_4.txt**
The beacon's **C2 host header** (if any):
Host Header: Host: haifang310.com


#### Formatted Beacon Information in Json

{
  "timestamp": 1725167366.1659446,
  "nmap_cmd": "/usr/bin/nmap --script grab_beacon_config.nse -vv -d -n -F -T5 -oX - 47.97.79.97",
  "ip": "47.97.79.97",
  "port": "443",
  "protocol": "tcp",
  "service": "https",
  "hostnames": null,
  "x64_sha1": "3c2febf7d07a9e02a7997d85378024b23fb30f42",
  "x64_sha256": "dd9ac5fbbdf23bdd88e33e655d890a049ab62bbbd84795bb73127e875bea171d",
  "x64_md5": "0ee9cb77529c6eefe1bc8d6091b1e907",
  "x86_sha1": "666cee97054524e4f43763958adff22e4d1b32c6",
  "x86_sha256": "2421a42eb5fb1dd545839d4ef72add5f3c0846beb3c7e187f336ddb7c7ac28dd",
  "x86_md5": "5aa5514d8bd9d3ad9226d3b9611b22df",
  "x64_config_method_1": "GET",
  "x64_config_method_2": "POST",
  "x64_config_port": 443,
  "x64_config_spawn_to_x64": "%windir%\\sysnative\\svchost.exe",
  "x64_config_spawn_to_x86": "%windir%\\syswow64\\svchost.exe",
  "x64_config_jitter": 50,
  "watermark": 391144938,
  "c2_host_header": "Host: haifang310.com\r\n",
  "x64_config_polling": 5987,
  "x64_config_c2_server": [
    "61.170.80.230/jquery-3.3.1.min.js",
    "180.213.179.141/jquery-3.3.1.min.js",
    "120.195.185.112/jquery-3.3.1.min.js",
    "118.182.226.161/jquery-3.3.1.min.js",
    "61.170.81.233/jquery-3.3.1.min.js",
    "27.37.200.237/jquery-3.3.1.min.js",
    "101.226.26.147/jquery-3.3.1.min.js"
  ],
  "x64_config_beacon_type": "8 (HTTPS)",
  "x64_config_http_method_path_2": "/jquery-3.3.2.min.js",
  "x64_uri_queried": "/ILtT",
  "x86_config_method_1": "GET",
  "x86_config_method_2": "POST",
  "x86_config_port": 443,
  "x86_config_spawn_to_x64": "%windir%\\sysnative\\svchost.exe",
  "x86_config_spawn_to_x86": "%windir%\\syswow64\\svchost.exe",
  "x86_config_jitter": 50,
  "x86_config_polling": 5987,
  "x86_config_c2_server": [
    "61.170.80.230/jquery-3.3.1.min.js",
    "180.213.179.141/jquery-3.3.1.min.js",
    "120.195.185.112/jquery-3.3.1.min.js",
    "118.182.226.161/jquery-3.3.1.min.js",
    "61.170.81.233/jquery-3.3.1.min.js",
    "27.37.200.237/jquery-3.3.1.min.js",
    "101.226.26.147/jquery-3.3.1.min.js"
  ],
  "x86_config_beacon_type": "8 (HTTPS)",
  "x86_config_http_method_path_2": "/jquery-3.3.2.min.js"
}


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
