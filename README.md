# Advanced-Wireshark-Network-Forensics
If you've ever picked up a book on Wireshark or network monitoring, they almost all cover about the same information. They'll show you, "Here's an ARP frame, here's an IP packet, here's a web request..." But what they don't go into is: when you open a Pcap file for the first time, where do you start? What are the things that you look for? And how do you find them?  So my goal here is to help you bridge that gap between having a basic understanding of network protocol analyzers, and using them to solve real world problems.



## For scenario 1. 

1. Where did the user contracted the virus

2. any malware files captured? If there are, we can generate hash and submit to virustotal. 


3. kinda of calls made to external sources
It makes various call. Seems like the ones that responding via Pot 80

4. did try to propogate
No 

The commands uses in wireshark

To see traffic from 12.183.1.55 
ip.addr == 12.183.1.55 

Look for acknowledgement when a SYNC call was made. It should ideally return ACK. 

Use the following command on wireshark's filter 

> ip.addr == 12.183.1.55 && !(tcp.stream == 5) && http.host

Internal network scanned, called 
> ip.src == 12.183.1.55 && ( ip.addr == 192.168.0.0/16 || ip.addr == 192.168.0.0/16 || ip.addr == 172.16.0.0/12 || ip.addr == 10.0.0.0/8  || ip.dst == 12.0.0.0/8)


## Scenario 2 
Client network attack. 

Denial of service attack against FTP 192.168.56.1

FTP taken offline 

Attacking host 
192.168.56.101  

FTP Server 
192.168.56.1

Objective 

What causes the spike in FTP traffic? 

What type of attack? 

See alot or ARP - pretty sure it is port scan going on. Go to Statistic -> Converation 


Use the filter = arp.opcode == 2 on wirewhark and hit enter
- This is to 

What are the results of those attacks? What types of attack

## See network traffic activities

> !(arp)

ARP is Address Resolution protocol which tend to retrieve ips from a dns name.


And verify that, there are various different port number appearing. This is an obvious sign that attacker trying to do a port scan

## Acknowledgement that attacker received

> tcp.flags == 0x012

You should see SYN, ACK for the following ports :-

21 

445 

139

135

49154

49152

49155


## FTP Attack trace 

Use the following command :- 


> tcp.flags == 0x012 && (tcp.port == 21)


0x012 = SYNC / ACK 
For more info, please refere to link below :- 
http://rapid.web.unc.edu/resources/tcp-flag-key/

## Look only at FTP 

> tcp.port == 21

Right click and choose follow stream. We can see attacker trying to use brute force to login

What event took place prior to the FTP Servier being taken offline

Did they get in? Ftp login for success code for login successful is 230

We want to see if the attacker has login successfully. 

> ftp.response.code == 230  

And right click, and then choose 'Follow Stream'. Then click on the 'Srream' drop down button up. You can scroll through different types of network traffic capture data.









