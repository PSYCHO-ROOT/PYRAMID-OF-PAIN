# PYRAMID OF PAIN
 
## 1 - THE HASH VALUES (Trival)
The hash value is a numeric value of a fixed length that uniquely identifies data. A hash value is the result of a hashing algorithm such as : MD5, SHA-1, SHA-2 ...
A hash is not cryptographically secure if two files have the same hash value, sec professionals ussualy use the hash on specific malware as a way to uniquely indentify it .
As an attacker, it’s basic to modify a file by even a single bit, which would produce a different hash value. Wich make it really hard for threat hunters to keep the hash value as a primary indicator of a malware .
Let’s take a look at an example of how you can change the hash value of a file by simply appending a string to the end of a file using :
```bash
PS C:\Users\THM\Downloads> Get-FileHash .\OpenVPN_2.5.1_I601_amd64.msi -Algorithm MD5
Algorithm Hash                             Path                                                 
_________ ____                             ____                                                 
MD5       D1A008E3A606F24590A02B853E955CF7 C:\Users\THM\Downloads\OpenVPN_2.5.1_I601_amd64.msi
```
```bash
PS C:\Users\THM\Downloads> echo "AddedString" >> .\OpenVPN_2.5.1_I601_amd64.msi
PS C:\Users\THM\Downloads> Get-FileHash .\OpenVPN_2.5.1_I601_amd64.msi -Algorithm MD5
Algorithm Hash                             Path                                                 
_________ ____                             ____                                                 
MD5       9D52B46F5DE41B73418F8E0DACEC5E9F C:\Users\THM\Downloads\OpenVPN_2.5.1_I601_amd64.msi
```
## 2 - IP ADDRESS (Easy)
An IP address is used to identify any device connected to a network, and we relay on it to semd/receive any information over the net .
From a defense standpoint, knowledge of the IP addresses is much valuable to check if the IP address affiliated with malicious activities
An attacker can use ip blocking by using FAST FLUX. The purpose of using the Fast Flux network is to make the communication between malware and its command and control server challenging to be discovered by security professionals .
So, the primary concept of a Fast Flux network is having multiple IP addresses associated with a domain name, which is constantly changing .
## 3 - DOMAIN NAMES (Simple)
Domain Names can be a little more of a pain for the attacker to change as they would most likely need to purchase the domain, register it and modify DNS records.
Unfortunately for defenders, many DNS providers have loose standards and provide APIs to make it even easier for the attacker to change the domain.
As an example attackers can make a punycode attack. Punycode is a way of converting words that cannot be written in ASCII, into a Unicode ASCII encoding
As an example : 
```bash
adıdas.de
```
wich is the punycode of :
```bash
http://xn--addas-o4a.de/
```
Attackers usually hide the malicious domains under URL Shorteners. A URL Shortener is a tool that creates a short and unique URL that will redirect to the specific website specified during the initial step of setting up the URL Shortener link that can generate malicious links such as :
bit.ly / goo.gl / ow.ly / s.id / smarturl.it ....
U can see the restricted url bu adding + to the short url
for example :
```bash
https://someurl.com/bw7t8p4u
```
```bash
https://someurl.com/bw7t8p4u+
```
## 4 - HOST ARTIFACTS (Annoying)
Host artifacts are the traces or observables that attackers leave on the system, such as registry values, suspicious process execution, attack patterns or IOCs (Indicators of Compromise), files dropped by malicious applications, or anything exclusive to the current threat.
The attacker would need to circle back at this detection level and change his attack tools and methodologies.
## 5 - NETWORK ARTIFACTS (Annoying)
A network artifact can be a user-agent string, C2 information, or URI patterns followed by the HTTP POST requests. Network artifacts can be detected in Wireshark PCAPs or by an IDS
 If you can detect and respond to the threat, the attacker would need more time to go back and change his tactics or modify the tools, which gives you more time to respond and detect the upcoming threats or remediate the existing ones.
## 6 - TOOLS (Challenging)
If The attacker is detected at this stage he would most likely give up trying to break into your network or go back and try to create a new tool that serves the same purpose, or he would invest some money into building a new tool
## 7 - TTPs (Tough)
TTPs stands for Tactics, Techniques & Procedures, which means all the steps taken by an adversary to achieve his goal, starting from phishing attempts to persistence and data exfiltration. If you can detect and respond to the TTPs quickly, you leave the adversaries almost no chance to fight back.
 At this point, the attacker would have two options:
* Go back, do more research and training, reconfigure their custom tools
* Give up and find another target
