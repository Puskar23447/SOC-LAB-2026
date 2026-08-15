# SOC Lab - Day 1 Network Investigation

## Investigation ID
INV-001

## Objective
To check the connection between my Kali Linux and Metasploitable machines and observe the network traffic using Wireshark.

## Source
192.168.56.101 - Kali Linux

## Destination
192.168.56.103 - Metasploitable

## Protocol
ICMP

## Activity
I used the ping command from Kali Linux to check whether the Metasploitable machine was reachable.

## Observation
The ping was successful and Wireshark showed ICMP Echo Request and Echo Reply packets between both machines.

## Evidence
- Ping test screenshot
- Wireshark screenshot
- ping-investigation.pcapng

## Finding
Both machines are connected properly and can communicate with each other.

## SOC Relevance
I learned how normal ICMP traffic looks in Wireshark. This will help me compare it with the traffic generated during the security testing in the next steps.

## Conclusion
The connection between Kali Linux and Metasploitable is working properly. Wireshark is also capturing the network traffic successfully.
