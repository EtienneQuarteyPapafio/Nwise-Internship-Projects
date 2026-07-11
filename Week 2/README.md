# Nwise-Internship-Project Week 2
Hands-on CyberSecurity internship projects showing practical experience with Tooling, Triaging, and Digital Forensics through technical documentation.

# Objectives
For week 2 our objectives were to use Nmap to discover devices on our network and identify services they are running, and to use wireshark to capture and analyse network traffic. We also learnt how to recognise normal network behaviour, and identify signs of suspicious and malicious traffic patterns.

For this scenario we have joined a SOC team and have deployed a new Ubuntu server, we are tasked with confirming that it is reachable, identify services on the server, and can capture netwrok traffic generated when communicating with it.

For the beginner lab we had the task of using Kali and nmap to scan open ports on an ubuntu os, both machines are connected to a host only virtual network with the ip addresses:

Kali: 192.xxx.xxx.xx3

Ubuntu:192.xxx.xxx.xx4

First we have to ensure that Ubuntu is on the same network, a ping from Kali shows a 0% packet loss, verifying an active and reachable device.
Kali pinging Ubuntu: 
![alt text](https://github.com/EtienneQuarteyPapafio/Nwise-Internship-Projects/blob/main/Week%202/Screenshots/1%20Kali%20ping%20Ubuntu.png)

Next we had to confirm the status of a Secure Shell Service on the Ubuntu by using 'sudo systemctl status ssh'. The status showed an installed and configured secure shell that was inactive, this inactivity was reflected in an nmap scan of the Ubuntu VM.
![alt text](https://github.com/EtienneQuarteyPapafio/Nwise-Internship-Projects/blob/main/Week%202/Screenshots/2%20Nmap%20scan.png)

Using command 'sudo systemctl start ssh' activates the service to start listening for connections, a re-entry of '..status ssh' shows the activate state and the service listening on port 22.
![alt text](https://github.com/EtienneQuarteyPapafio/Nwise-Internship-Projects/blob/main/Week%202/Screenshots/3%20SSH%20Status.png)

A subsequent nmap scan now shows the open tcp port 22, and the mac address. 
![alt text](https://github.com/EtienneQuarteyPapafio/Nwise-Internship-Projects/blob/main/Week%202/Screenshots/4%20Nmap%20rescan.png)

An nmap re-scan using the command 'nmap -sV and the Ubuntu IP address' shows the Operating System Version, this knowledge could be exploited by malicious actors if they have unpatched exploits or zero day capability.  

![alt text](https://github.com/EtienneQuarteyPapafio/Nwise-Internship-Projects/blob/main/Week%202/Screenshots/5%20service%20version.png)

Next we were instructed to ping Ubtuntu from Kali and capture the network data using Wireshark.

![alt text](https://github.com/EtienneQuarteyPapafio/Nwise-Internship-Projects/blob/main/Week%202/Screenshots/6%20Wireshark%20ping.png)

The captured traffic shows multiple protocols at work however, the main protocol used by a ping is an ICMP echo request and reply.

![alt text](https://github.com/EtienneQuarteyPapafio/Nwise-Internship-Projects/blob/main/Week%202/Screenshots/7%20Wireshark%20Capture.png)

By filtering for ICMP we see the exact time stamps of the protocol.

![alt text](https://github.com/EtienneQuarteyPapafio/Nwise-Internship-Projects/blob/main/Week%202/Screenshots/8%20ICMP.png)

By filtering out the capture again we can see the ARP protocol, this protocol occurs before the ICMP pings as the router needs to link the mac address of ip addresses to the mac address of devices in order to send the correct packets.

![alt text](https://github.com/EtienneQuarteyPapafio/Nwise-Internship-Projects/blob/main/Week%202/Screenshots/9%20ARP.png)

![alt text]()



# Author

Etienne Quartey-Papafio
Junior SOC Analyst, Malware Analyst, and Reverse Engineer
GitHub: https://github.com/EtienneQuarteyPapafio
