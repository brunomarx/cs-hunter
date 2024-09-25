# CS-Hunter Project

What is Cobalt Strike?
Cobalt Strike is a commercial penetration testing tool widely used for simulating advanced persistent threats (APTs). It provides attackers and red teams with a comprehensive platform for conducting sophisticated campaigns, including command-and-control (C2) operations, lateral movement, and stealthy command execution.

Cobalt Strike includes a beacon payload that can be deployed to compromised machines. These beacons communicate back to the C2 server (Command-and-Control), receiving instructions and executing tasks such as data exfiltration, lateral movement, and persistence.

In the context of adversary infrastructure hunting, Cobalt Strike is often abused by threat actors. Security teams use tools like Shodan to identify publicly accessible Cobalt Strike servers, thus mitigating potential risks posed by malicious infrastructure.

Explanation of the Lists
1. list_1.txt: IPs from Shodan Search
This file contains IPs identified through Shodan searches. The parameters used to find these IPs come from characteristics observed in Cobalt Strike beacons that communicate with known C2 servers. These IPs are potential Cobalt Strike servers that need further analysis and scanning.

Example entry:


1.14.206.72
2. list_2.txt: Scanned IPs Returning Cobalt Beacons
After running Nmap scans on the IPs listed in list_1.txt, this file contains IPs that confirmed the presence of Cobalt Strike Beacons. If the scan identifies a Cobalt Strike server on an IP, it is added here. These IPs host a Cobalt Strike Team Server.

Example entry:


1.14.206.72
3. list_3.txt: Cobalt Strike Beacon C2 Server Information
This file contains the C2 server configurations extracted from the beacon payloads. It includes details on how the Cobalt Strike beacon communicates with the C2 server, such as HTTP GET/POST methods, polling intervals, jitter, and server URLs.

Example entry:


C2 Server IP: 1.14.206.72
Communication Method: GET, POST
Polling Interval: 60000
HTTP Method Path: /submit.php
x64 C2 URL: 1.14.206.72/fwlink
x86 C2 URL: 1.14.206.72/__utm.gif
4. list_4.txt: C2 Host Header in the Beacon
This file contains the C2 host header information extracted from the beacon configuration. The Host Header is part of the HTTP requests that the beacon sends to communicate with the C2 server. This file helps to understand how the beacon disguises its communication (e.g., using custom host headers).

Example entry:

css
Code kopieren
Host Header: 
Example Beacon Breakdown
Using the example beacon JSON provided, the following information can be extracted:

The beacon was scanned on IP 1.14.206.72, which was identified through a Shodan search and scanned using Nmap.
The C2 server information includes:
x64 C2 Server: 1.14.206.72/fwlink
x86 C2 Server: 1.14.206.72/__utm.gif
The beacon uses HTTP GET and POST methods for both 32-bit and 64-bit systems.
The polling interval is set to 60,000 milliseconds (60 seconds).
The Host Header appears to be empty in this case.
Corresponding List Entries
list_1.txt
Contains the IP that was searched using Shodan and identified as a potential Cobalt Strike server:

Code kopieren
1.14.206.72
list_2.txt
After the Nmap scan confirmed the presence of a Cobalt Strike beacon, the IP is added here:

Code kopieren
1.14.206.72
list_3.txt
The details extracted from the beacon's configuration, including C2 server information and HTTP communication patterns:

mathematica
Code kopieren
C2 Server IP: 1.14.206.72
Communication Method: GET, POST
Polling Interval: 60000
HTTP Method Path: /submit.php
x64 C2 URL: 1.14.206.72/fwlink
x86 C2 URL: 1.14.206.72/__utm.gif
list_4.txt
The beacon's C2 host header (if any):

css
Code kopieren
Host Header: 
Summary
Cobalt Strike is a powerful tool for penetration testing but is often misused by threat actors.
list_1.txt contains potential IPs found via Shodan searches.
list_2.txt stores confirmed Cobalt Strike servers after scanning.
list_3.txt holds configuration details of how the beacon communicates with its C2 server.
list_4.txt stores the host header used by the beacon during communication.
