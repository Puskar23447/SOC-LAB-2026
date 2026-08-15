# Nmap Reconnaissance

## Target
192.168.56.103

## Tool Used
Nmap

## Objective
To find the open ports and services running on the Metasploitable machine.

## Results

| Port | State | Service |
|---|---|---|
| 21/tcp | open | ftp |
| 22/tcp | open | ssh |
| 23/tcp | open | telnet |
| 25/tcp | open | smtp |
| 80/tcp | open | http |
| 111/tcp | open | rpcbind |
| 139/tcp | open | netbios-ssn |
| 445/tcp | open | microsoft-ds |
| 512/tcp | open | exec |
| 513/tcp | open | login |
| 514/tcp | open | shell |
| 1524/tcp | open | ingreslock |
| 2049/tcp | open | nfs |
| 2121/tcp | open | ccproxy-ftp |
| 6667/tcp | open | irc |

## Observation
The Nmap scan showed that many ports are open on the Metasploitable machine. Different services are running on these ports, including FTP, SSH, Telnet, HTTP, SMB and NFS.

## Conclusion
From this scan, I understood that the Metasploitable machine has many services running on it. I can now select some of these services and test them further in my lab.


