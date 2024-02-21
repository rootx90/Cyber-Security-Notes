#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : more about Password Cracking & Cryptography
> 1) wifi-phishing : in wifi-hacking
> 2) Theory : windowOS password cracking
> 3) Practical work : windowOS password cracking
> 4) Theory : Cryptography

---
### wifi-phishing : in wifi-hacking
- in wifi Phishing , 2 wifi-adapters required <br>- Note : it's not a part of our course , so check on YT
- reviews of wifi-hacking adapters : [Best WiFi Hacking Adapters in 2021 (Kali Linux / Parrot OS) - YouTube](https://www.youtube.com/watch?v=5MOsY3VNLK8&ab_channel=DavidBombal)
- via 2 wifi-adapters , we can get the victim's wifi-router password directly ✔<br>just like we did in social engineering
- Q : how 2 wifi-adapters work in wifi-phishing ✔<br>Ans : 1st wifi-adapter (consider it as a main wifi-adapter) - will get hidden <br>- then 2nd wifi-adapter (consider it as a fake wifi-adpater) - will be present in front of every normal wifi <br>- so if anyone enter the password in that fake wifi-adapter - then u can see that password

### Theory : windowOS password cracking
- Q : can u tell where window's OS password got saved , any location ? ✔
	- Ans : <br>Location : C:windows/system32/config/SAM <br>- SAM file : contain all the passwords of window's different profiles
	- this "SAM" file also encrypted 
	- Q : what we gonna do <br>Ans : apply "password cracking" <br>- but depends on a wordlist - cuz 1st we do I.G on targeted Victim - then we make a wordlist (based on I.G we got about victim)
	- `Note ✅` : until u don't do (I.G + making the wordlist properly) - then u can't crack the password of anyone <br>- which also a security <br>Q : means will be safe , if ur password cracked by someone easily <br>Ans : No - that's why security necessary <br>- our work : is to identify vulnerability from a device/app/software & make it secure
	- Conclusion : if u try to open the "SAM" file - then it'll not open - even if u're admin user of ur own device ✔ <br>- in this case , use a tool

### Practical work : windowOS password cracking
- STEP 1 : Download & Installation of a tool 
	- STEP 1.1 : Advice : before downloading it , off ur Windows Defender <br>1) go to "windows Security" <br>2) click "Manage settings" - Virus & threat protection settings <br>3) & turn off every toggles
	- STEP 1.2 : go [Password Cracking Tools.rar file](https://drive.google.com/file/d/1QvVAW_CakPwl37KIvok3bvBh_JLqfZDc/view)
	- STEP 1.3 : password = 123456
- STEP 2 : inside the folder 
	- "pwdump7" folder is useful for us
	- STEP 2.1 : go inside "pwdump7" folder -> copy the folder path
	- STEP 2.2 : open cmd "run as administration" -> paste the location
	- STEP 2.3 : in the location , remove "C:" -> then write `cd` <br>![[33_lecture-0-M3.jpg | 500]]
	- in kali , we do `ls` & in winOS - do `dir`
	- STEP 2.4 : run `dir` , output : "PwDump7.exe" will be shown
	- STEP 2.5 : copy "PwDump7.exe" -> paste it in cmd -> hit enter , output : <br>![[33_lecture-1-M3.jpg | 500]]
	- in output , we got the hash passwords of each user (i.e administrator , Gues , etc) of "SAM" file <br>- so these Hash password created via a algorithm i.e NTLM ✔<br>- NTLM - is the cryptographic format in which user passwords are stored on Windows systems ✔
	- now we need to store those hash passwords in a file <br>Q : earlier which symbol used to save in a file <br>Ans : `>`
	- STEP 2.6 : run `PwDump7.exe > passtest` <br>- Note : if ur Windows Firewall is off - but this command not working - then means windows-firewall deleted the main folder , <br>so extract the zip file again & restart the cmd again <br>- output : <br> ![[33_lecture-2-M3.jpg | 500]]
	- in output : those hash passwords not showed - cuz hash passwords are saved in a file
	- STEP 2.7 : right click on that saved file -> open it as -> notepad , output : all hash passwords are shown
		- output : <br>![[33_lecture-3-M3.jpg | 500]]
		- Note ✅ : <br>- if a user has id no. = 500 - aka Administrator user<br>- any different user 
	- Now we got the hash passwords file
	- STEP 2.8 : go in "ophcrack" folder -> click "x64" -> double click "ophcrack.exe"
		- Now need bring that file inside this software
		- STEP 2.8.1 : in ophcrack software , click "Load" -> select "PWDUMP file" -> select that saved file , output : <br>![[33_lecture-4-M3.jpg | 500]]
		- to crack each of them , give a wordlist file
		- STEP 2.8.2 : click "tables" tab -> select "Vista fre" -> click "install" -> open "ophcrack" folder -> select "tables_vista_free" <br>- output : now that "Vista free" becomes green - means it becomes enabled
		- STEP 2..8.3 : click ok
	- STEP 2.9 : click "crack" tab , output : it'll try to crack the password of those hashes - via "tables_vista_free" (which contain wordlists) <br>- if password doesn't contain in those wordlists - then not able to crack it <br>- then try by urself

### Theory : Cryptography
- Q : what's Cryptography
	- Ans : it contains 2 words i.e Crypto & graphy
	- Crypto = means hidden <br>graphy = written/writing <br>- both means = writing anything - by keep that writing stuff hidden
	- Eg : whenever a top person (like PM , CM , security agencies , etc) share any details  - they use cryptography technology
	- Cryptography has many concepts & it's itself a big topic with
- it has total 4 branches are : ✔<br>1) steganography <br>2) Hashing <br>3) Encoding <br>4) Encryption
- combining these branches together = are used around the world to send/receive the data in encrypted form
- Explanation of each branches of it ✔
	- steganography
		- is a process to send a secret/imp message - by keeping that secret/imp message hide behind of something/stuff
		- Types of steganography / Ways to implement steganography <br>1) Image/Video/Audio steganography<br>2) whitespace/Text/Document steganography <br>3) Natural writing steganography <br>4) Network steganography
		- Image/Video/Audio steganography : <br>- means Eg : u have a txt file & that file contain a message - & u want to send that file to 2nd person directly <br>or via a 3rd-person to 2nd person - but u don't want that txt file should be readable to 3rd-person <br>- so u can hide that txt file - behind a image/video/audio file , <br>now when u send that txt file (by hiding it behind a image/video/audio file) via any person to 2nd person <br>or directly to 2nd person (but other's can't understand) - then nobody can't understand <br>- so whatever others see that file as image/video/audio - but 2nd person see as secret message
		- whitespace/Text/Document steganography : <br>- means inside a document/text/whitespace , hiding a secret message<br>- Eg 1 : open MS Docs -> write a password -> then select that message -> give a white color on it , <br>output : message becomes hidden , Conclusion : same color used as that page's color<br>- Eg 2 : u have a 1 page document , inside of that page - many words are written , <br>but there's a corner where a extra whitespace given
		- Natural writing steganography : <br>- it's a the one which is used by mostly in security agencies <br>- means each word has a it's own code message <br>- Eg 1 : Assume , A = 1B , B = AZ , C = 9Z , H = 6E , I = 30, <br>now i want to send "HI" message - then i'll send 6E30 to that person - but others can't understand <br>& only that person can understand that code message as "HI" <br>- in it , natural words are used
	- Hashing
		- we have seen its eg : "Password Cracking" <br>- mostly hashing used to encrypt the password (& that password couldn't be of anything)
		- is a 1-way process <br>- Eg : "Dev" is a password - so once it's converted into a hash form <br>then that hash password can't be reversed back to actual password <br>- but when multiple times "Dev" password encrypted into a hash form - then that hash will be same as pervious hash ✔
		- even CEO/owner of Insta , FB , etc don't know about that ur Hash password <br>- CEO of different big companies (like Insta , etc) - they only know that they're using hashing technology to encrypt the password <br>- so when a user make a password on that app - then that password saved in hash form on that app's server <br>Q : then what does it mean - "Password got leaked" ✔ <br>Ans : when news comes that password of users go leaked from that social media <br>- then actual plain text password not leaked - but hash password got leaked
		- Conclusion : hashing mostly used in passwords encryption <br>![[33_lecture-5-M3.jpg | 300]]
	- Encoding
		- is used in URLs
		- Q : do u know how http works <br>Ans : earlier , we're sending sensitive data of users on URL (Eg : password , username , etc) <br>- due to this , hackers an easily read user's sensitive data <br>- but now we're sending those sensitive data inside body of a request/response - instead on Header <br>- so Https (contain SSL) - which protect the URL 
		- Eg : use any symbols (like @ , / , ?) ✔<br>in browser , search "wscube? password" , output : on URL , "?" & " " one space will get encrypted <br>![[33_lecture-6-M3.jpg | 500]]
		- in output , any symbols are used will be encrypted in URL <br>- so a normal person can't understand the URL easily & hacker can't easily hack
		- Encoding used for URL protection
	- Encryption
		- Eg : encryption used in zipping a file , etc
		- Working Process of Encryption ✔
			- assume u want to encrypt PDF & u have a tool <br>so 1st thing : u need to select the algorithm - let's say "AES" <br>2nd thing : which bit of AES u want - AES 128 & AES 256 <br>- so till yet , we selected algorithm i.e AES
			- 3rd thing : which technology u want to use - let's say "CBC" technology <br>4th thing : password it'll ask - & that password will be complete sentence : let's say "HiImDev"
			- & that technology (which we selected i.e CBC) could of different types - & AES algorithm is of 2 different types <br>- means if a hacker knows about that password - then the hacker might select wrong technology <br>even if the hacker selected correct technology  then the hacker select wrong bit of algorithm <br>- Conclusion : combining these 3 together i.e algorithm & it's bit + technology + password = <br>then only considered as encryption <br>- means if someone put all these 3 together in proper sequence - then only that person can decrypt otherwise not ,<br>means only that way can be used to decrypt as the way encryption applied to that stuff <br>- Conclusion : means whatever sequence order used to encrypt that stuff - on that sequence can be used to decrypt it ,<br>so anything wrong (like either a password mismatched OR a technology OR algorithm big) happens in the sequence , <br>then decrypt will get failed
			- Conclusion Pic : <br>![[33_lecture-7-M3.jpg | 300]]
		- used encrypt books , pdf , file , etc
- Q : what's algorithm ✔
	- Ans : is a step by step process to complete a particular task<br>- Eg : u want to call someone - then what u'll do <br>STEP 1 : on power button of ur phone <br>STEP 2 : lock open<br>STEP 3 : phone icon <br>STEP 4 : number select <br>STEP 5 (optional) : SIM select (if dual SIM inserted) <br>STEP 6 : call
	- Q : can u call that guy without follow these steps in sequence <br>Ans : No

---
### Homework
1. 

---
### End of the lecture (Doubts) :
- More on : Types of steganography
	- [What Is Steganography & How Does It Work?](https://www.kaspersky.com/resource-center/definitions/what-is-steganography)
	- [What is Steganography? A Complete Guide with Types & Examples](https://www.simplilearn.com/what-is-steganography-article)
	- [types of steganography Cryptography](https://www.perplexity.ai/search/types-of-steganography-Zu0VwHumR.6SsozYnFPRYg?s=u)
- More on : Types of Hashing in cryptography
	- [cryptography hash functions](https://www.tutorialspoint.com/cryptography/cryptography_hash_functions.htm)
	- [types of hashing in cryptography](https://www.perplexity.ai/search/types-of-hashing-xsC_T_5iTB6XZ2VgNOSnQw?s=u)
	- [Hash Functions and list/types of Hash functions](https://www.geeksforgeeks.org/hash-functions-and-list-types-of-hash-functions/)
- students doubts
	- Q : can we copy "SAME" file & paste it in other location <br>Ans : can't - cuz if u're not Administration user in that device - then u can't copy & paste it in other location <br>- if this possible - then we can copy & paste it in our device
	- Q : can we stop the process of "SAM" file via TaskManager <br>Ans : NO , cuz TaskManager didn't monitor this file 
- Q : single band vs dual band wifi adapter <br>Ans : [single band vs dual band wifi adapters](https://www.perplexity.ai/search/single-band-vs-jBxsHBEoRJ.6ZlcYbIQsdw?s=u)


