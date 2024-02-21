#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : Wi-Fi Hacking & Password Cracking
> 1) Practical work : Wi-Fi Hacking
> 2) Practical Work : Password Cracking
> 3) Ways to find patterns in a password

---
### Practical work : Wi-Fi Hacking
- for STEPS : go to lecture 31

### Practical work : Password Cracking
- let's say u saved the info of handshake file as Kapil
- STEP 1 : `sudo su` -> `cd /home/kali`
	- output : u'll see many name as kapil <br>![[32_lecture-0-M3.jpg | 500]]
	- so actual handshake file will be `.cap` extension i.e kapil-01.cap
- earlier commands used "airmon-ng" , "aireplay-ng" , "airodump-ng" : which are used for wifi-scanning <br>now for password cracking - use "aircrack-ng" ✔
- STEP 2 : there are 2 ways to crack the password - based on different types of encryption ✔
	- right now , there are mainly 2 types encryption used for wifi-password - i.e WPA & WPA2 ✔ <br>- there are less change where only WPA - it's only when a person use old wifi
	- 1st way) : if the password is WPA - then run `aircrack-ng kapil-01.cap` <br>- without giving a wordlist of password
	- 2nd way) : if the password is WPA2 - then run `aircrack-ng kapil-01.cap -w wordlist.txt`
	- but this wifi-password is based on WPA2 (which means that password has high level security) <br>- u can check the encryption security of each wifi-router ✔<br>![[32_lecture-1-M3.jpg | 500]]
	- so to crack the passwords , we need to a wordlist of many passwords - which already available in our Kali OS <br>- we use this wordlist only sometimes - cuz this wordlist contains common passwords only <br>- for strong password - required something else
	- STEP 2.1 : in kali OS , unziping the wordlist file i.e rockyou.txt.gz <br>- run `cd /usr/share/wordlists` <br>STEP 2.2 : `thunar` -> right click on that file & click Extract-here <br>- Note : can't be done via "unzip" command - cuz it has different format
	- STEP 2.3 : run `aircrack-ng kapil-01.cap -w /usr/share/wordlists/rockyou.txt` <br>- in this command , "-w" means define the wordlist of passwords <br>- output : "aircrack-ng" starts cracking that password via using each password of the wordlist
	- Explanation : wordlist file ✔
		- it's a txt file
		- Q : in form our password is kept <br>Ans : the ".cap" file - which is captured by us , the password is kept in encrypted form <br>Q : how the password is kept in encrypted form <br>Ans : u can say encrypted or hashes form <br>Q : what's hash <br>Ans : assume,  password - kapil , once the password is converted into Hash - then password looks like H216393219... <br>- so algorithms , tools - are used to convert the password into hash form <br>- Hash password : is not in binary
		- Q : About Hash password ✔
			- Advantage Hash password : <br>- once the password converted into the hash form <br>- then that hash can't be converted to that password again
			- but when u write that same password - then always same hash will be generated <br>- but u can't reverse/convert that same Hash into the same password 
		- Q : but how the system got to know - we wrote the wrong password - when we try to sign with wrong password in our device ✔ <br>Ans : when u write the wrong password - then that wrong password gets converted into the hash form <br>- then the device take that hash password (of wrong password) & match with the previous hash (of correct password) <br>- Assume if both - that new hash password gets matched with the previous hash (of correct password) <br>then we can use our device <br>- but if that new hash password didn't matched with the previous hash (of correct password) <br>then the device will show wrong password <br>- Conclusion : this is how the device identify whether the password correct or wrong
		- u can hack the hash password - but u can't understand that hash password <br>- cuz hash passwords are encrypted
		- a wordlist contain passwords & their hashes for password cracking
		- Q : how a wordlist made <br>Ans : we do I.G on the targeted Victim about : petname , everything related to the Victim , his likes/dislikes , etc<br>- then we write a wordlist - then there's a chance to hack his/her device's password <br>- cuz Victim will make password based on his/her surroundings
		- Conclusion Pic : <br>![[32_lecture-2-M3.jpg | 500]]
	- STEP 2.4 : if the wordlist not able to crack the password , press `CTRL + C`
	- in "/home/kali/usr/share/wordlists" : there are many wordlists like john.lst , etc <br>- but if need a long wordlist - go to google
	- STEP 2.5 : search "Seclists master github" -> https://github.com/danielmiessler/SecLists <br>- output : seclists wordlist contain leaked passwords <br>- Eg : in this website , go to "Passwords" folder -> "WiFi-WPA" folder -> wifi leaked passwords will be shown
	- Now might be there's a chance in these wordlists - doesn't have our wordlist <br>- in this situation , we make our wordlist ✔ <br>- to make our own wordlist - use "crunch"
	- STEP 2.5 : making our own wordlist , run `crunch -h` , output : syntax of it "`crunch <min> <max> [options]`" <br>- min : means how much minimum words password required need to create <br>- max : means how much maximum words password required need to create <br>- `[options]` : contains combination (like of symbols , sign , numbers , alphabet , etc) of passwords
	- STEP 2.6 : run `crunch 8 15 1234567890abcdefghijklmnopqrstuvwxyz@!$%^./` -> then press "CTRL + C"
		- output : cuz this tool will take storage in PB (Peta Byte) - as a normal user , we don't have storage for it <br>![[32_lecture-3-M3.jpg | 500]]
		- To solve this issue , we have `|` pipe sign (when we were learning I.G) ✔
			- Q : how this `|` pip sign works to crack the password ✔<br>Ans : here whatever password combinations we used - these combinations will be used as a password <br>but without saving each password - via the help of `|` pipe sign
			- means "crunch" tool make each password (based on that combinations) <br>- & each password (without saving) will sent to aircrack-ng <br>so both (password creation & password cracking) will be done simultaneously in the process
			- Conclusion : so once a password generated (by "crunch" tool) - will go to aircrack-ng via `|` pipe sign <br>& same process will happen with each password (without saving each password in a txt file)
			- so `|` pipe sign making those each password as a input for aircrack-ng <br>- Conclusion Pic : <br>![[32_lecture-4-M3.jpg | 300]]
	- STEP 2.7 :  run <br>`crunch 8 15 1234567890abcdefghijklmnopqrstuvwxyz@!$%^./ | aircrack-ng --bssid 8C:A3:99:A8:CD:9A -w - kapil-01.cap wlan0` <br>- in command , `-` : extra hyphen means to show the background process of password cracking ✔ <br>- output : each password will be generated by "crunch" tool (without saving each password) & <br> via `|` pipe sign - step by step each password will go (as a input) to "aircrack-ng" tool (to crack the password) <br>Q : is wifi will be used in this "password cracking" process✔<br>Ans : no - cuz we're testing on that ".cap" file <br>Q : do know how much time it'll take to crack the password ✔<br>Ans : it might take a month <br>that's why , we don't do password cracking directly , 1st thing we do IG on the targeted victim 
	- STEP 2.8 : now stop the process , press "Ctrl + C"

### Ways to find patterns in a password
- 1) Q : what best thing we can do to do password cracking ✔<br>Ans : do a I.G on a targeted victim <br>- Eg : if u have a access of the victim's system - then inside cmd (of his/her system) - then we can understand the password pattern , <br>cuz everyone makes a password based on patterns (like kapil@123 , kapil@DateOfBirth , kapil@name-of-his-fav-thing) <br>- so once understanding the pattern + doing I.G - then easy to crack the password of targeted victim's device ✔ <br>- but that password doesn't work to crack - but u can understand patterns of that password ✔
- 2) Q : what to do - in order to find out pattern in the password - if u got a device/lapi of a criminal/targeted-victim/hacker ✔
	- STEP 1 : open winOS powershell , run `netsh wlan show profile` , output : <br>![[32_lecture-5-M3.jpg | 500]]
	- this command - will show all the wifi connected (from starting till yet) in this system/device ✔
	- now let's say , i want to know the password of "Bad Hacker" wifi-profile ✔
	- STEP 2 : run `netsh wlan show profile "Bad Hacker" key=clear` <br>- in this command , in double quotes - that's the profile name (of wifi-router device) <br>Q : why that profile name in double quotes ✔<br>Ans : cuz in that profile name , there's a space b/w - that's why
	- output : <br>![[32_lecture-6-M3.jpg | 500]]
	- in output , inside "key Content" - that's the password ✔<br>- so that's the way to find out the pattern of the password <br>- means in this password , we got to know that victim/person use the phone no. to make a password
	- Q : let's say there're 3 wifi-profile name of wscubetech wifi-router - then can i able to know the pattern of passwords of wscubetech <br>Ans : yes
- 3) Q : if u got the access of criminal/victim's system ✔
	- STEP 1 : go to his/her browser
	- STEP 2 : go settings -> search "password" -> then "google password manager" , output : u can see saved passwords
	- STEP 3 : if he/she put the system's pin/password - in order to see any of the password <br>- then if know the system's pin/password - then u can see password of his/her login websites/webapps
- 4) Q : if u got the access of criminal/victim's system ✔
	- STEP 1 : go to his/her browser -> search "google dashboard" -> open google dashboard
	- output : <br>1) u can see mail (if u got the access of his/her mail's account - then u can do much more like reset the pass) <br>2) u can see his/her playstore - due to this , u can understand pattern what apps he/she likes <br>eg : u can make the same application & bind the payload - send it to him/her aka rubberducky <br>3) if u got his/her location timeline - due to this , u can find out where he/she go , his/her dislikes & likes <br>eg : a person show love to play games - then he/she might go to netcafe - then u can do attacks related to games


---
### Homework
1. 

---
### End of the lecture (Doubts) :
- Student Doubt 
	- Q : what's packet injection ✔<br>Q : is packet injection was the same as we were sending de-authentication packet ✔
		- Ans : Packet injection = means selecting a targeted device - then injecting a packet inside that device's wifi <br>- & Packet injection will only happen if that device has vulnerability of Packet Injection
		- in wifi-hacking , De-authentication packets (which we were sending) aren't not injecting <br>those packets are just to de-authenticate the device from the router
- Q : in 2024 , which encryption used for wifi password <br>Ans : [in 2024 , which encryption used for wifi password](https://www.perplexity.ai/search/in-2024-which-7h1.6MRHT9mOesBkZAd4Dw?s=u)
- Extra stuff
	- [How to Install KALI LINUX on Your Android Phone in 5 Minutes (Without Root) - YouTube](https://www.youtube.com/watch?v=HuRuO3PdZHs&ab_channel=WsCubeTech) <br>[Kali Linux NetHunter install in 8 minutes (rootless) and includes Android 14 - YouTube](https://www.youtube.com/watch?v=GmfM8VCAu-I&ab_channel=DavidBombal) <br>[Install KALI LINUX on Android Phone - Complete Setup - YouTube](https://www.youtube.com/watch?v=H240HOZpCB0&ab_channel=WsCubeTech)
	- [kali nethunter Non-root Install on Any Phone 2023 |Full Installation | hindi - YouTube](https://www.youtube.com/watch?v=PEpSg92ASiA&ab_channel=himanshuyadav-hackind)
	- [Linux for Hackers Python pip, Git, Apt NEW Tools Install with OTW! (Episode 4) - YouTube](https://www.youtube.com/watch?v=EeGjmTx2diM&ab_channel=DavidBombal)

