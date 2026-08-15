SOC INCIDENT TIMELINE

Incident ID: INV-001
Target: 192.168.56.103
Source: 192.168.56.101

1. Network Baseline
Event:
Kali communicated with Metasploitable using ICMP.

Evidence:
ping + Wireshark

2. Reconnaissance
Event:
Kali performed network/service reconnaissance against the target.

Evidence:
Nmap output + Wireshark SYN traffic

3. FTP Investigation
Event:
Kali connected to the ProFTPD service on port 2121 and attempted anonymous authentication.

Result:
Login failed with 530 Login incorrect.

Evidence:
FTP terminal + Wireshark TCP stream

4. SMB Investigation
Event:
Ports 139 and 445 were reachable, but SMB protocol negotiation timed out.

Evidence:
nc + smbclient output

5. Telnet Investigation
Event:
TCP connection to Telnet port 23 was established.

Evidence:
Telnet terminal screenshot

6. NFS Investigation
Event:
The NFS server exported / to all hosts and the filesystem was successfully mounted from Kali.

Evidence:
showmount + mount + ls

7. HTTP Investigation
Event:
Port 80 was open, but the HTTP request did not return a response.

Evidence:
nc + curl output
