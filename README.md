# SOC Lab - Network Investigation and Security Analysis

## About

This is my personal cybersecurity lab project where I practiced basic **SOC investigation and network security analysis**.

I used Kali Linux as the investigation machine and Metasploitable as the vulnerable target in a VirtualBox lab.

The main purpose of this project was to learn how to find open services, check network traffic, investigate security issues, collect evidence and document the findings.

---

## Lab Environment

* **Kali Linux:** `192.168.56.101`
* **Metasploitable:** `192.168.56.103`
* **VirtualBox:** Used to run the virtual machines

The lab was performed on a private virtual network.

---

## Tools Used

* Kali Linux
* Metasploitable
* Nmap
* Wireshark
* Netcat
* FTP
* Telnet
* NFS
* Linux commands

---

## What I Did

During this project, I performed the following tasks:

1. Checked connectivity between Kali Linux and Metasploitable using ping.
2. Used Nmap to find open ports and services.
3. Investigated the services found during reconnaissance.
4. Checked the FTP service and tested anonymous login.
5. Investigated the failed FTP login.
6. Checked HTTP and SMB ports.
7. Tested a Telnet connection.
8. Checked NFS exports.
9. Mounted the NFS export from Kali.
10. Captured network traffic using Wireshark.
11. Investigated ICMP and FTP traffic.
12. Checked relevant service and system information.
13. Created basic SOC detection ideas.
14. Documented the investigation and security findings.

---

## Nmap Reconnaissance

I used Nmap against the Metasploitable machine:

```text
Target: 192.168.56.103
```

The scan showed several open services, including:

* FTP
* SSH
* Telnet
* SMTP
* DNS
* HTTP
* SMB
* NFS
* MySQL
* IRC

The results helped me understand the exposed attack surface of the target machine.

---

## FTP Investigation

I investigated the FTP service running on port `2121`.

I tried an anonymous login and received:

```text
530 Login incorrect.
```

I then used Wireshark to investigate the traffic related to the FTP connection.

This helped me understand how failed authentication activity can be identified and investigated.

---

## Telnet Investigation

Telnet was found open on port `23`.

I successfully connected to the service from Kali.

Because Telnet is an insecure remote-access protocol, an exposed Telnet service should normally be reviewed and disabled if it is not required.

---

## SMB Investigation

Nmap showed SMB-related ports:

```text
139/tcp
445/tcp
```

I checked the available SMB service from Kali.

The enumeration attempt timed out, but the open ports were recorded as part of the target's exposed services.

---

## NFS Investigation

The NFS service was one of the most important findings in this project.

I checked the NFS exports using:

```text
showmount -e 192.168.56.103
```

The result showed:

```text
Export list for 192.168.56.103:
/ *
```

This meant that the root filesystem `/` was exported to all hosts represented by `*`.

I was able to mount the export from Kali and view the filesystem.

### Risk

This is a serious configuration problem because unrestricted access to the root filesystem can expose sensitive system files and directories.

### Recommendation

NFS exports should be restricted to trusted hosts and sensitive directories such as the root filesystem should not be exported unless there is a specific requirement.

---

## Wireshark Investigation

I used Wireshark to capture and analyze network traffic between the two virtual machines.

The investigation included:

* ICMP ping traffic
* TCP connections
* FTP traffic
* Reconnaissance-related traffic

The PCAP files are stored in:

```text
04-Wireshark/
```

---

## Basic SOC Detections

I created some basic detection ideas based on the activity observed in the lab.

### 1. Port Scanning

If one source IP makes connection attempts to many different ports of the same target in a short period, it may indicate port scanning.

### 2. Failed FTP Login

Repeated failed FTP authentication attempts could indicate suspicious login activity.

### 3. Unnecessary Services

Services that are not required should be reviewed and disabled because they increase the attack surface.

### 4. NFS Misconfiguration

An NFS export that provides unrestricted access to the root filesystem should be treated as a serious security issue.

The detection notes are stored in:

```text
detections.txt
```

---

## Important Findings

The main findings from this lab were:

| Finding                   | Observation                     | Risk                                           |
| ------------------------- | ------------------------------- | ---------------------------------------------- |
| Multiple exposed services | Many network services were open | Increased attack surface                       |
| Failed FTP login          | Anonymous login was rejected    | Suspicious authentication activity if repeated |
| Telnet exposed            | Port 23 was accessible          | Insecure remote access                         |
| SMB exposed               | Ports 139 and 445 were open     | Increased attack surface                       |
| NFS root export           | `/` exported to `*`             | High                                           |

---

## Evidence

I collected screenshots and PCAP files during the investigation.

The evidence includes:

* Nmap scan results
* Ping results
* Wireshark ICMP analysis
* FTP connection
* Failed FTP login
* FTP packet analysis
* SMB port checks
* Telnet connection
* NFS export information
* NFS root filesystem access
* Reconnaissance traffic

Screenshots are stored in:

```text
07-Screenshots/
```

PCAP files are stored in:

```text
04-Wireshark/
```

Reports are stored in:

```text
08-Reports/
```

---

## Project Structure

```text
SOC-LAB-2026/
│
├── 01-Architecture/
├── 02-Recon/
├── 03-Attacks/
├── 04-Wireshark/
├── 05-Investigation/
├── 06-Incident-Reports/
├── 07-Screenshots/
├── 08-Reports/
├── evidence/
├── detections.txt
└── README.md
```

---

## What I Learned

This project helped me understand the basic workflow of a SOC investigation.

I learned how to:

* Perform basic network reconnaissance
* Identify open ports and services
* Capture network traffic
* Analyze packets using Wireshark
* Investigate failed authentication
* Check SMB, Telnet and NFS services
* Identify a security misconfiguration
* Create basic detection ideas
* Collect and organize investigation evidence
* Write an incident report

One important thing I learned is that **an open port does not automatically mean that the service is vulnerable**. It needs further investigation to understand the actual security risk.

---

## Conclusion

This project gave me practical experience with basic network investigation using Kali Linux, Metasploitable, Nmap and Wireshark.

The most important issue I found was the **NFS root filesystem being exported to `*`**, which allowed the export to be mounted from Kali.

This project helped me understand how reconnaissance, network traffic analysis, service investigation and evidence documentation fit together in a basic SOC investigation.

---

## Disclaimer

This project was performed only in my own isolated VirtualBox lab using Metasploitable for educational purposes.

No unauthorized systems or networks were tested.
