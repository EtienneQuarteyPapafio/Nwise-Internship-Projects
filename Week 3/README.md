# Nwise-Internship-Project Week 3
Hands-on CyberSecurity internship projects showing practical experience with Tooling, Triaging, and Digital Forensics through technical documentation.

# Objectives
For week 3 our objectives were to gain foundational knowledge of using the Splunk SIEM. Our learning objectives are learning to: understand the purpose of splunk, navigate the interface, perform searches using the SPL, exploring and analysing events, creating reports and dashboards, and to understand the fundamentals of knowledge objects.

As the task for this week was to obtain an intro to splunk certification (of which I already own) I opted to build a splunk enterprise server on my homelab instead.

I have a spare mini pc that I use to send all my splunk universal forwarder logs to.

Firstly we will want to log in to our ubuntu server and update and upgrade all dependencies to start from a clean slate.

```
sudo apt update && sudo apt upgrade
```
Then we will need to download splunk from the download page, it will have the latest version to download using the wget command the code below is the version as of the posting of this repo, 
since i am using a debian based OS the link will be for a .deb package

```
wget -O splunk-10.4.1-5a009d941268-linux-amd64.deb "https://download.splunk.com/products/splunk/releases/10.4.1/linux/splunk-10.4.1-5a009d941268-linux-amd64.deb"
```

Then when the download is finished we install the package. It may tell you No such file or directory for find: '/opt/splunk/lib....' you can ignore this.

```
sudo dpkg -i splunk-10.4.1-5a009d941268-linux-amd64.deb
```
When it says complete, we now need to accept the license, As of 2026 Splunk no longer recommends running splunk as a root user and instead opts for it to be run as a non admin user.

```
sudo /opt/splunk/bin/splunk start --accept-license
```

We can create a new user account for running splunk, which may tell you a user named splunk already exists, in that case just set a password for the user.

```
sudo useradd splunk
```
Then set the users password
```
sudo passwd splunk
```
We then grant the user permission to access the files
```
chown -R splunk:splunk /opt/splunk/
```
We then enable boot start for the user

```
sudo /opt/splunk/bin/splunk enable boot-start -user splunk
```
Then we run splunk as the splunk user

```
sudo /opt/splunk/bin/splunk start -user splunk
```

If you are connected to your server via eth on a main computer or running it in a vm with a host-only connection you can connect to the web browser by switching your main computer to the same subnet. (you can check your ips by using ipconfig on windows or ip a on linux)

When on the same subnet connect to the webrowser with the url: (your splunk server ip:8000) in the search bar e.g 127.0.0.1:8000

# Author

Etienne Quartey-Papafio
Junior SOC Analyst, Malware Analyst, and Reverse Engineer
GitHub: https://github.com/EtienneQuarteyPapafio
