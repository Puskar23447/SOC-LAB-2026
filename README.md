# SOC Lab - Network Investigation and Security Analysis

## About the Project

This is a personal SOC lab project that I created to practice basic
security monitoring and investigation.

I used Kali Linux as the testing and monitoring machine and
Metasploitable as the target machine.

The main goal was to understand how network traffic, open services,
authentication activity and system logs can be investigated.

## Lab Setup

Kali Linux:
192.168.56.101

Metasploitable:
192.168.56.103

## Tools Used

- Kali Linux
- Metasploitable
- Nmap
- Wireshark
- Netcat
- FTP
- Telnet
- NFS
- Linux commands

## What I Did

During the project I:

1. Tested network connectivity using ping.
2. Performed reconnaissance using Nmap.
3. Investigated open services.
4. Investigated the FTP service.
5. Tested anonymous FTP authentication.
6. Checked the HTTP service.
7. Investigated SMB ports.
8. Tested the Telnet service.
9. Investigated NFS exports.
10. Mounted and unmounted the NFS export.
11. Captured network traffic using Wireshark.
12. Checked available system and service logs.
13. Created basic SOC detection ideas.
14. Documented the findings and evidence.

## Important Findings

### NFS Misconfiguration

The NFS server was exporting the root directory `/` to `*`.
I was able to mount the export from Kali.

This was the most important security issue found during the lab.

### Telnet

Telnet was accessible on port 23.

### Multiple Services

Several services were available on the target, including FTP,
HTTP, SMB, Telnet and NFS.

### FTP Authentication

An anonymous FTP login attempt was rejected with:

530 Login incorrect.

### Reconnaissance

Nmap generated connection attempts to multiple ports. The traffic
was captured and studied in Wireshark.

## Evidence

The project contains screenshots and PCAP files showing the
different stages of the investigation.

Important evidence includes:

- ICMP packet capture
- Nmap results
- FTP investigation
- Wireshark captures
- SMB investigation
- Telnet connection
- NFS export and mount
- Log investigation
- Reconnaissance traffic

## Project Structure

SOC-LAB/

├── 01-Network/

├── 02-Nmap/

├── 03-Service-Investigation/

├── 04-Wireshark/

├── 05-Logs/

├── 06-Evidence/

├── 07-Reports/

├── detections.txt

├── evidence-index.txt

└── README.md

## What I Learned

This project helped me understand the basic process of a SOC
investigation.

I learned how to identify services, capture network traffic,
investigate authentication attempts, check system logs and
document security findings.

I also learned that having an open port does not automatically
mean that the service is vulnerable. Further investigation is
needed to understand the actual risk.

## Conclusion

This lab gave me practical experience with basic SOC investigation
using Kali Linux, Metasploitable and Wireshark.

The project is performed in an isolated virtual lab for learning
and security testing.
