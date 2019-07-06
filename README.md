# Advanced-Wireshark-Network-Forensics
If you've ever picked up a book on Wireshark or network monitoring, they almost all cover about the same information. They'll show you, "Here's an ARP frame, here's an IP packet, here's a web request..." But what they don't go into is: when you open a Pcap file for the first time, where do you start? What are the things that you look for? And how do you find them?  So my goal here is to help you bridge that gap between having a basic understanding of network protocol analyzers, and using them to solve real world problems.



For scenario 1. 

The commands uses in wireshark 

ip.addr == 12.183.1.55 

Look for acknowledgement when a SYNC call was made. It should ideally return ACK. 
ip.addr == 12.183.1.55 && !(tcp.stream == 5) && http.host


Internal network scanned, called 
ip.src == 12.183.1.55 && ( ip.addr == 192.168.0.0/16 || ip.addr == 192.168.0.0/16 || ip.addr == 172.16.0.0/12 || ip.addr == 10.0.0.0/8  || ip.dst == 12.0.0.0/8)


