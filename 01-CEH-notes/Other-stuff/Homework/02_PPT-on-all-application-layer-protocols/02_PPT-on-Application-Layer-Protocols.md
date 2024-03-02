#WsCubeTech-CEH-homework

---
### Resource Links
- [Application_Layer_Protocols](https://www.academia.edu/37781543/Application_Layer_Protocols)
- [Application layer protocols | PPT](https://www.slideshare.net/FabMinds/application-layer-protocols-248653733)
- [meseec.ce.rit.edu/eecc694-spring2000/694-5-2-2000.pdf](http://meseec.ce.rit.edu/eecc694-spring2000/694-5-2-2000.pdf)
- [Application Layer Protocols in Computer Network | Scaler Topics](https://www.scaler.com/topics/computer-network/application-layer-protocols/) ✔
- OSI Model for Cyber Security
	- [The OSI Model for Cyber Security: A Comprehensive Guide to Securing Network Communications | Karthikeyan Nagraj | by Karthikeyan Nagaraj | Medium](https://cyberw1ng.medium.com/the-osi-model-for-cyber-security-a-comprehensive-guide-to-securing-network-communications-b8b0170675dd)
- OSI vs TCP/IP model : 
	- [TCP/IP: What is TCP/IP and How Does it Work?](https://www.techtarget.com/searchnetworking/definition/TCP-IP)
	- [What is TCP/IP Model and its Different Layers? | Intellipaat](https://intellipaat.com/blog/what-is-tcp-ip-model/)
	- [Application Layer Protocols in Computer Network | Scaler Topics](https://www.scaler.com/topics/computer-network/application-layer-protocols/) ✔
- Application Layer protocols in TCP/IP model : [Application Layer Protocols in TCP/IP - GeeksforGeeks](https://www.geeksforgeeks.org/application-layer-protocols-in-tcp-ip/)
- TCP vs UDP :
	- in lecture 4
	- [Differences between TCP and UDP - GeeksforGeeks](https://www.geeksforgeeks.org/differences-between-tcp-and-udp/?ref=lbp)
- Vids on it
	- [Application Layer in Computer Network - YouTube](https://www.youtube.com/playlist?list=PLgwJf8NK-2e5utf4e5VJCEeNTDFtKHgsF)
	- [Lec-75: Application layer of OSI model in Hindi | Application layer protocols & Port no - YouTube](https://www.youtube.com/watch?v=8An0dRalJeM&ab_channel=GateSmashers) ✔

----
### PPT on Application Layer Protocols in Computer Network

#### List of Application Layer Protocols

1. echo
2. FTP 
3. Secure Shell (SSH)
4. TELNET
5. SMTP
6. DNS
7. DHCP
8. TFTP
9. HTTP
10. POP
11. NTP
12. HTTPS
13. RIP
14. NFS
15. LPD
16. X window
17. SMTP
18. SNMP
19. URL
- Note ✅: HTTP , FTP , SMTP , SSH , DNS , TELNET = These protocols are essential for understanding <br>& potentially exploiting network vulnerabilities

---

> About + Features + Port no. + which Transport Protocol used by them
#### Echo
- about
	- a client send the request to the server & then the server send a response to the client for that request <br>- so total time b/w a client & server for sending a request & a response - this total time aka round trip time <br>- so to find the how much this Total-time/round-trip-time - we use "echo" protocol
	- Diagram : Client ⇌ server
	- "echo" protocol - generally used by Network Administrator - in order to find out <br>whether we're connected with the network or not (means are we connected to the server or not) <br>- Eg : "Ping" is generally used with ICMP protocol - but purpose of ICMP protocol is same as <br>whether we're connected with the network or not <br>- if we're getting response from the server = means we're connected with the server <br> if not getting response from the server = means our connection is not established with the server
	- Pros of it <br>1) it tells whether the connection is established or not with the server <br>2) it tells how much time gonna take to respond to our client's request aka round-trip-time
- Port no. = 7
- Transport Protocol : it can use either TCP/UDP
	- means if u're connection is TCP then it'll send the request to TCP <br>if the connection is UDP then it'll send the request to UDP
#### FTP
- about
	- full form : File Transfer Protocol
	- if u want to transfer files - then the network will use FTP protocol
- Port no. = 20/21
	- Ques : why two port numbers <br>Ans : becuz generally the protocols are two different : inline & out-of-line protocols
	- out-of-line protocols : means <br>1) these protocols transfer data from different port number<br>2) & for the control statements/commands - they use different port number
	- so same FTP does <br>for data - FTP use 20 port no. <br>& for control commands - it use 21 port no.
	- & we have lot of FTP commands - for check on internet <br>- if we want to send all these FTP commands - TCP use port no. 21 of FTP ✔
	- both port no. is reserved for FTP
- Transport Protocol : it use TCP 
	- becuz it needs reliability , means that files must be transferred 100% <br>- there shouldn't be like that some files are done & some files didn't transferred <br>- if that file is transferred completely - only then it'll open
	- so anywhere u want reliability - there we use TCP ✔
#### Secure Shell (SSH)
- about
	- used in that place where we want security
	- so this protocol use cryptographic functions
	- if two people make connections - means if a client & the server are connected each other <br>then they are connected via secured key <br>- means they will exchange that key with each other & the connection will be stablished b/w a client & the server ✔ <br>- & they form a tunnel/tunneling
	- so when that tunnel formed (means secured connection b/w 2 system) - then a private connection created
	- so Internet is a unsecured - so in unsecured & public networks <br>- how we can do tunneling & make a secured & private connection - we use SSH ✔
- Port no. = 22
- Transport Protocol : it use TCP (& TCP is connection & reliability oriented)
#### TELNET
- about
	- used for remote login or getting remote access of a system
- Port no. : 23
- Transport Protocol : it use TCP connection
#### SMTP
- about
	- full form : Simple Mail Transfer Protocol
	- used for mailing
- Port no. = 25
- Transport Protocol : it use TCP connection
#### DNS
- about 
	- full form : Domain Name System
- Port no. = 53
- Transport Protocol : it use UDP (user datagram protocol)
	- Ques : When do we use UDP protocol <br>Ans : we use this protocol - when we want speed , means we don't want to make any connection <br>- we want to send request quickly & we want response quickly
	- means when we need consistently speed - in that situation , we use UDP Protocol
	- Ques : why do we use DNS <br>Ans : we have the domain name but we need IP address of that domain name <br>- so to find that IP address of the server - we send a request ✔ <br>- although , DNS can use TCP , but generally by-default UDP is used
	- Ques : why by-default UDP is used by DNS protocol <br>Ans : cuz we send a request to that server which have IP address of that domain name (which we have) ✔ <br>- so we need fast & consistent result to get IP address of that domain name <br>- that's why UDP protocol used
#### DHCP
- about 
	- full form : dynamic host control protocol
	- used when a Dynamic IP address required <br>- means generally , we use a static IP address 
	- Eg : in computer labs of colleges and universities <br>- in each PC's , a static IP is provided already <br>- so whenever u establish a connection - then already an static IP is given in that PC - so that case , DHCP is not required
	- but if ur administrator wants to assign dynamic IP addresses to ur computer - then u can use a local DHCP protocol <br>- means u'll give ur MAC address - means a request will be send from ur computer <br>& that request will contain ur computer's MAC address with a message like "I need a IP address" <br>- then dynamically , from a list of IP addresses - DHCP will provide an IP address to ur computer
	- in case of static , we don't use DHCP <br>in case of Dynamic , we use it
- Port no. = 67/68
	- it's also out-bound - means DHCP use two port numbers 
	- so for data transfer = 67 <br>& for control statement = 68
- Transport Protocol : UDP
	- Ques : why it use UDP transport protocol <br>Ans : in DHCP , becuz there's no need to establish connection <br>- we want speed in "that u gave the mac address & u want an IP address" <br>- so in this situation , we don't want to waste time & here no reliability required <br>- so using UDP in DHCP - is a better option
#### TFTP
- about 
	- Full form : Trivial File Transfer Protocol
	- used when we want <br>Eg : let's say a client wants to send some files to the server <br>& if clients wants to send files to the server without making any connection <br>- means TFTP doesn't make a connection with the server , TFTP directly send the files <br>then in this case , ur data may get lost <br>- but if ur application says that there's no issue if data get lost - then TFTP is used in this situation ✔
	- TFTP vs FTP ✔
		- FTP : 
			- firstly it'll make a connection via using "TCP 3 way hand-shaking" - then it'll transfer the data
			- so in this , time will get spent more becuz of reliability <br>- & if any packet get lost , then FTP will send that packet again
		- TFTP : 
			- is fast
			- same in "about" which we wrote
- Port no. = 69
- Transport Protocol : UDP
#### HTTP
- About 
	- full form : Hyper Text Transfer Protocol
	- is a protocol used to access the data on the WWW
	- all ur web pages , all ur browsers <br>- in all those browsers , u would have always seen i.e whenever u send a request to any application or server <br>- that request goes via HTTP protocol <br>- means all the webpages gets transferred via HTTP protocol
	- Extra stuff on it
		- can be used to transfer the data in the form of plain text , hypertext , audio , video & etc
		- is like the FTP as it also transfers the files from one host to another host. <br>But HTTP is simpler than FTP.
		- is like SMTP as the data is transferred between client and server.
		- SMTP messages are stored and forwarded <br>while HTTP messages are delivered immediately.
		- Features
			- is the standard protocol for requesting a URL defined web-page resource <br>& for sending a response to the web server
			- <u>Stateless</u> : <br>- The connection b/w client & server exist only during the current request & response time only <br>- is a stateless protocol as both the client & the server know each other only the current request <br>- Due to this nature of it , both the client & server don't retain the information b/w various requests <br>of the web pages
- port no. = 80
- Transport Protocol : it use TCP - means connection oriented based
#### POP
- about 
	- full form : post office protocol
	- generally , it's used to pop mails - means that mail already came in mail server <br>u just need to pop/bring that mail to ur system - for this we use POP
	- POP vs SMTP ✔
		- SMTP : used to push the mails , means to send the mails
		- POP : used to withdraw/bring the mails to our own system
	- It has different versions like POPv2<br>- but the latest version of it i.e POP3 (which we use today) & it's port no. 110
- Port no. 
	- POP3 = 110
	- POP2 = 109
- Transport Protocol : TCP
	- so SMTP also use TCP , so both POP & SMTP works parallelly <br>- SMTP to send the mails & POP used to fetch the mails
#### NTP
- about 
	- Full form : network time protocol
	- Eg : there are multiple clients connected to server <br>& if all those clients wants to synchronize their time , their clocks <br>- Obviously if u're connected to a server - then u want the time of server is synchronized <br>with the time of ur client's machine ✔
	- so to Synchronize the clock/time - we use NTP <br>- means to find the time - that's why aka Network time protocol
- Port no. = 123
- Transport Protocol : UDP
	- here also UDP used cuz no connection required & u're simply finding the time
#### HTTPS
- about
	- is a secured version of HTTP <br>- nowadays , u'll find most of the applications running on HTTPS
	- Eg : when u do search like amazon then u never type complete URL of amazon with https <br>- whatever u search on internet via their domain name <br>- then ur connection will be established on HTTPS - cuz it's secured <br>& it works on SSL (Secured Socket Layer)
	- & SSL works same as SSH <br>- like SSL use Cryptography functions - means ur connection will not go directly to the server <br>- firstly , that request will get converted into cipher text with authentication & then go to the server ✔<br>- here authentication - means username , password will be authenticated <br>then u'll get a session & u can work within that session <br>- so the request will be converted into cipher text & ur username , password is always checked ✔
	- all ur banking portals - automatically works on HTTPS 
- port no. = 443
- Transport Protocol : TCP
#### RIP
- about
	- full form : routing information protocol
	- for more : watch [Application layer protocols & Port no - YouTube](https://www.youtube.com/watch?v=8An0dRalJeM&ab_channel=GateSmashers)
- Port no. = 520
- Transport Protocol : UDP
#### NFS
- about 
	- full form : Network File System
	- it mounts a file system present in a network & enables interactions with the file system <br>as though that system is mounted locally. Users can use CLI commands to create, remove, read, write <br>& perform other functions on the remote files accessed using NFS. ✔
	- pros & cons
		- Pros <br>1) Multiple users can access the same file simultaneously. <br>2) Centralization of data reduces system admin overhead.
		- Cons : <br>1) They are vulnerable to internet threats unless used on a trusted network behind a firewall. <br>2) Parallel file access is not supported by a lot of clients to date.
- Port no. = 2049
- Transport Protocol : TCP
#### SNMP
- about 
- Port no. = 
- Transport Protocol : 

- Note ✅ : so whichever protocol using UDP (Transport protocol) - then doesn't mean that protocol can't use TCP
	- Eg : DNS - using UDP , but we can use TCP also in DNS
	- cuz where UDP is being used - then there TCP can also be used <br>cuz UDP says that "i make work fast" , but TCP says "i'll form a connection first & i want reliability + security" <br>- so in TCP , some delay of time happens
	- so where UDP is being used , there TCP can also be used <br>but where TCP is being used , there UDP might or might not be used

---
### Advice 
- u can't remember all Application Layer Protocols & their port no. , so just remember the important <br>which are vital acc. to Ethical Hacker
