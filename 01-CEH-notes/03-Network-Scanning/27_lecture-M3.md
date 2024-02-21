#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : DOS Attack practical
> 1) About : Function in programming - in terms of CEH
> 2) How DOS Attack implemented via a function in Bash 
> 3) Practical Work : DOS attack via fork() bomb
> 4) Concept : How DOS attack done on a website via BurpSuite
> 5) Download & Installation Steps - BurpSuite
> 6) Practical Work : DOS attack on a website via BurpSuite

---
### About : Function in programming - in terms of CEH
- Advice : programming is basically related to programmers - it's not our work <br>- so as a CEH , u must have knowledge about it - cuz by using function - a hacker do a DOS attack ✔
- About Function
	- [what is a function](https://www.perplexity.ai/search/what-is-a-I1GK5sp2QHebO3afTUIyTA)
	- A function in programming is a self-contained software routine that performs a specific task[1]. It is a block of organized, reusable code that is used to perform a single, related action[2]. Here are five points to explain the function concept to a 10-year-old kid:
		1. **Reusability**: Functions allow you to use the same code multiple times in a program, <br>making it more efficient and easier to maintain[1].
		2. **Modularity**: Functions help organize your code by breaking it into smaller, more manageable pieces[2].
		3. **Input and Output**: Functions usually take in data (input), process it, and return a result (output) [4].
		4. **Examples**: In everyday life, you can think of a function as a recipe that you follow to cook a meal. <br>The recipe is a set of instructions that you repeat every time you want to cook the meal, making it easier and faster to prepare.
		5. **Built-in Functions**: Most programming languages come with built-in functions that you can use in your programs, <br>like adding two numbers or calculating the square root of a number[3].
	- Example : <br>To illustrate this with an example, imagine you have a toy box with different toys. <br>You can create a function to count the number of toys in the box. When you want to count the toys again, <br>you can simply call the function, and it will return the number of toys without you having to write the same code twice. <br>This makes your toy box (program) more organized and efficient.
	- Citations:  <br>[1] https://www.pcmag.com/encyclopedia/term/function <br>[2] https://www.tutorialspoint.com/computer_programming/computer_programming_functions.htm <br>[3] https://en.wikipedia.org/wiki/Function_(computer_programming) <br>[4] https://users.cs.utah.edu/~germain/PPS/Topics/functions.html <br>[5] https://www.sololearn.com/en/Discuss/2057001/what-is-a-function-in-programming-i-cant-seem-to-grasp-the-definition-of-it

### How DOS Attack implemented via a function in Bash
- we'll do DOS attack via a function in Bash Programming , not in actual programming langs
- Understanding Example : DOS attack via a function in programming
	- let's say add() function `add() { add | add & } add()
	- in code , in bash programming , <br>> "`|`" : used for OR <br>> "`&`" : used to run processes in background , so this code will run in background ✔
	- More about "`|`" in Bash : [command line - What does the linux pipe symbol "|" do? - Super User](https://superuser.com/questions/756158/what-does-the-linux-pipe-symbol-do)
	- Q : what's happening in code ✔<br>Ans : we "add()" function "add | add &" : means we called the same function twice in block of code <br>- after the end of it , again called the function <br>- due to this , the function will call again & again itself recursively
	- so this function continuously call itself again & again - then at the end , it'll increase system's processing power - aka DOS attack ✔
	- in Bash programming , we use "`:`" instead of "add"
- in Bash Programming
	- the code `:(){ :|:& };:` aka "`fork() Bomb` ✔
	- "`:`" : means calling a function
### Practical Work : DOS attack via fork() bomb
- Q : what we did for changing MAC address of a system <br> Ans : made a file for changing MAC-address
- STEPS : implementation of it in Kali
	- STEP 0 : in kali , run `sudo su`
	- STEP 1 : run `gedit fork.sh`
	- STEP 2 : at 1st line - write `:(){ :|:& };:` , output : every time syntax error comes - doesn't matter how u write
		- Note ✅ : if a bash code file doesn't run - then put `#!/bin/bash` : means run inside terminal ✔
		- STEP 2.1 : write
		  ```
		  #!/bin/bash
		  :(){
			:|:&
		  };:
		  ```
	  - like this <br>![[27_lecture-0-M3.jpg | 300]]
	  - Q : what's the next STEP <br>Ans : giving executable permission to the file
	  - STEP 2.2 : run `./fork.sh` , output : open task manager of kali - then CPU + memory got freezed <br>& everything also gets freeze
	  - STEP 2.3 : shut down the kali immediately 
- STEP : implementation of it in windows
	- STEP 1 : in google , search `fork bomb for windows` , output : u'll see `%0|%0`
	  - STEP 2 : in windows , make a `dos.bat` file <br>- if ".bat" file not created - then turn off ur anti-virus - then create
		  - ".bat" file : means a script file that stores commands to be executed in a serial order .<br> It helps automate routine tasks without requiring user input or intervention ✔
		  - Note ✅ : don't run this program in windows - even accidentally
	  - STEP 3 : in file , write `%0|%0` - then save the file
	  - STEP 4 : share this file with that victim & once he/she runs on his/her system - then DOS attack happen
	  - STEP 5 : delete that file from ur windows OS - if u accidentally delete the file - then ur system gets corrupted
	  - Note : running in any OS - inside Vmware , then CPU usage will get increase - of that OS <br>- but that doesn't mean that ur actual system's resources - vmware not using <br>- vmware also consuming ur actual resources virtually - but still vmware using ur actual system's resources

### Concept : How DOS attack done on a website via BurpSuite
- understanding situation <br>- we're a attacker & in our system (i.e client) - a website is open - Eg : "wscubetech.com" <br>& that website is hoisted on a server - & this is obvious - that server has a size/storage (like 1TB or 10TB or etc) <br>- now in any website , there'll be a/are input boxes - Eg : in contact form , mail form , signup form , login form , etc
- STEP 1 : go in about-us of wscubetech [Contact Us: WsCube Tech](https://www.wscubetech.com/contact-us.html) & scroll down , output : Contact Form <br>![[27_lecture-1-M3.jpg | 300]]
- this is obvious - in this contact form , if u write anything & send via "send message" button <br>- then those details will go to the website's server ✔
- STEP 2 : inside contact form <br>- in Name input : if u write the name like this "`rthyuio[[mnbgtyuj`" , output : Please enter valid name <br>- in Mobile No. : if u write the mobile no. more than 10 digits , output : Please enter valid mobile no. <br>- in Email Add. : if u write the name & until u don't put  "`@gmail.com`" - that email consider as invalid , output : please enter valid email <br>- Purpose dropdown menu - is not a input field <br>- in Message input : if u write any random - then output : Please enter valid message
- understand that - inside "message" input - the message which we wrote - it has a size (like 1KB or 10KB) <br>- & that message will go inside the server <br>![[27_lecture-2-M3.jpg | 500]]
- so when that message sent at a time - then message size is 10KB (assume the size as 10KB) <br>- but when we were filling the contact form - details were showing invalid <br>- cuz some inputs has limitation - like in mobile no. : can't write more than 10 numbers & different condition in each input fields
- Q : in contact form , why these limitations/boundations are in each input field ✔<br>Ans : these limitations/boundations are made for security
	- Security : is a concept of penetration 
		- 2 types of security : client-side & server-side ✔ 
		- in client-side security , inside the website - the stuff which we're writing & the security of the website <br>is stopping us by showing invalid - so the security of the website is stopping us in client system <br>- so if we click on "send message" button - then the data packets will not go outside the client system <br>- Q : who is stopping the client system from sending the data packets ✔<br>Ans : client-side security of the website
		-  in server-side security , if those data packets goes from client-side system to server-side <br>- then data will be checked (whether details are valid or not) inside the server <br>- if details are invalid - then the server sent those data (with a message i.e invalid data) back to client-side system ✔
	- so in both security Types - has a security to check whether data is valid or not 
- in this situation , 
	- we got to know that - here is client-side security is applied , not server-side <br>- so what if we fill all the details correctly , then if those data packets come out from client-side <br>- cuz our main motive to bring those data packets out from client-side <br>- then data packets can be intercept/stop in the middle (from going to server-side) - then we can write all malicious stuff <br>- so earlier client-side sending 10KB data to the server - now it'll send 1TB/2TB
	- Q : now what we'll happen in server ✔<br>Ans : if we send the data more than the limit/size of the server - then server gets down
	- so that's the DOS attack done a website
	- Q : never a DOS attack can be happen via the IP of the website , why ✔<br>Ans : cuz firewalls of the website's server will stop <br>- earlier we saw NS1 & NS2 , so first these two name servers will stop the malicious stuff - then firewalls will stop <br>& due to this , DOS attack not implemented on client-side ✔<br>- & the server contains NS1 & NS2 + firewalls - then DOS attack can't be done in server-side also ✔ <br>- if the website showing/contain only one Name server - then it's a vulnerability in the website
- Q : how to intercept/stop that data packets in the middle - from going to the server-side ✔<br>Ans : using BurpSuite tool <br>- so once that data packets come out from client-side <br>- then we'll stop/intercept in the middle - then we'll do some malicious changes for DOS attack in those data packets <br>- then send to the server-side of that website
- Conclusion Pic : <br>![[27_lecture-3-M3.jpg | 500]]

### Download & Installation Steps - BurpSuite
- download & install BurpSuite : [Burp Suite Community Edition - PortSwigger](https://portswigger.net/burp/communitydownload) <br>- for BurpSuite pro crack : [Install Burp Suite Pro on Kali Linux | by Ravindra Dagale | Medium](https://medium.com/@sherlock297/install-burp-suite-pro-on-kali-linux-6abccc3860a8)
- Note : here sir using BurpSuite pro crack : [is virus come in my main PC if i am using any crack software inside vmware](https://www.perplexity.ai/search/is-virus-come-yLnsEYlyT7OgVLAcngHqtA?s=u)
- Note : if burpsuite doesn't work - then download Java v8 - cuz might be it'll run on Java v8
	- STEPS : to download java jdk v8 (optional STEPS)
	- STEP 1 : search "open java jdk" -> [OpenJDK](https://www.openlogic.com/openjdk-downloads)
	- STEP 2 : inside website , select those drop-down options for linux
	- STEP 3 : `cd Downloads` -> `ls`
	- STEP 4 : `dpkg -i openlogic-openjdk-8u392-b08-linux-x64-deb.deb`
- STEP 0 : `sudo su`
- STEP 1 : `cd Downloads` - then `ls` , output : BurpSuite.zip
	- if the file is in zip format - then 2 ways to extract it <br>1st way : go to file-manager -> right click on it -> extract it <br>2nd way : in terminal -> run `unzip BurpSuite.zip` ✔
	- STEP 1.1 : run `ls`
	- STEP 1.2 : `cd Burpsuite` - then `ls` , output : <br>> "burp.sh" : is used only to run <br>> "burpsuite_pro_v1.7.34.jar" : is a supported file <br>> "ESEdition.jar" : used to run - which we need ✔
	- Q : if a file made of ".py" - then via which thing u're gonna run <br>Ans : run via python <br>Q : but "ESEdition.jar" file made via java - then via which thing - to run this file <br>Ans : java
- STEP 2 : run `java -jar ESEdition.jar` & hit enter
	- output : <br>![[27_lecture-4-M3.jpg | 500]]
	- in output , in "License" : we need this in further steps
	- STEP 2.1 : click "run" btn , <br>output : it'll take time to run - cuz we just installed the java jdk v8 - we didn't set the java v8
	- STEP 2.2 : close it
	- STEP 2.3 : to change the java jdk version , run `update-alternatives --config java`<br>output : all the java jdk version installed will be shown
	- STEP 2.4 : select `2` - cuz java jdk v8 is on no. 2
	- STEP 2.5 : run `java -jar ESEdition.jar` -> click on "run" btn
		- output : <br> ![[27_lecture-5-M3.jpg | 500]]
		- in this output , it's showing u're also using old java jdk version - & by clicking on OK - means we don't have an issue
	- STEP 2.6 : click OK , output : now it's setup popup will come
	- STEP 2.7 : click "I Accept" with checkbox tick
	- Note : here Sir using old version of BurpSuite & in new version , old features removed
	- STEP 2.8 : copy & paste the license , output : <br>![[27_lecture-6-M3.jpg | 500]]
	- STEP 2.9 : click "Next" btn -> select "Manual activation" btn 
		- output : <br>![[27_lecture-7-M3.jpg | 500]]
		- STEP 2.9.1 : copy the request & paste in "Request" input , output : Response is generated<br>![[27_lecture-8-M3.jpg | 500]]
		- STEP 2.9.2 : copy the response & paste in there <br> ![[27_lecture-9-M3.jpg | 500]]
	- STEP 2.10 : click "Next" btn -> "Finish" btn , output : license is activated
	- output : pop of deleting temp files
	- STEP 2.11 : click on "Delete" btn -> "Next" btn -> "Start Burp" btn
	- STEP 2.12 : now BurpSuite On

### Practical Work : DOS attack on a website via BurpSuite
- STEPS - to open BurpSuite Tool
	- STEP 0 : `sudo su`
	- STEP 1 : `cd Downloads`
	- STEP 2 : `ls`
	- STEP 3 : `cd Burpsuite`
	- STEP 4 : `ls`
	- STEP 5 : `./burp.sh`
	- STEP 6 (optional) : if JRE popup comes -> then click "OK" btn -> then click "Next" btn -> then click "start burp" btn
- STEPS : DOS attack on a website via BurpSuite
	- in BurpSuite , Tabs which are useful for us
		1. Proxy
			- mostly "Proxy" tab used
			- inside of it
				- Intercept tab : <br>1) used to stop & capture data packets <br>2) we can turn it OFF or ON : means to stop or don't stop the data packets
				- Options tab : <br>1) in "Proxy Listeners" section : <br>- used to define the IP - in order to capture the data packets of that IP only , <br>not other IPs (which are added or unticked) <br>- Eg : "127.0.0.1:8080" - so anyone goes via this IP+portno. - then data packets will be intercept/stop in BurpSuite <br>- output : <br>![[27_lecture-10-M3.jpg | 500]]
	- STEP 1 : Q : how to link "127.0.0.1:8080" IP + Port No. in (Proxy -> Options -> "Proxy Listeners" Section) with the browser
		- STEP 1.1 : in firefox , on top-right corner -> click "hamburger menu" -> settings
		- STEP 1.2 : search "proxy" -> click "settings" btn
		- STEP 1.3 : select "Manual Proxy configuration" <br>> in HTTP Proxy : write "127.0.0.1" & Port no. "8080"
		- STEP 1.4 : checked "Also use this proxy for HTTPS" -> click "OK" <br>![[27_lecture-11-M3.jpg | 500]]
		- Now everything is setup - but firefox don't trust on our BurpSuite Tool ✔<br>- cuz Eg : u don't want any unknown person to come at ur home & exit from ur home - <br> so same with firefox don't trust on BurSuite - cuz BurpSuite is unknown <br>- so we need to show the identity/certificate of BurpSuite to Firefox <br>like if u show ur aadhar card - then u'll get new JIO SIM - then only u can use JIO services (here JIO is a home)
	- Note : if setting the IP & Port no. in a browser - then only go to STEP 2 , otherwise setup them properly ✔
	- STEP 2 : downloading certificate of BurpSuite , run `http://burp` , output : <br>![[27_lecture-12-M3.jpg | 500]]
	- STEP 3 : click on "CA Certificate" btn , output : cacert.der downloaded
	- now add that certificate of BurpSuite on the browser
	- STEP 4 : firefox settings -> search "cert" -> click "View Certificates" -> click "import" -> select the certificate -> <br>then tick both Checkbox (Turst this CA to identity : websites + email users) -> click OK
	- Now we gave the permission to firefox , now whatever search query did on firefox - then all data packets <br>related to that search query will go via BurpSuite
	- STEP 5 : go in Proxy -> Intercept tab -> turn ON intercept
		- STEP 5.1 : in firefox , search "wscube" , output : we got the request of a search query <br>![[27_lecture-13-M3.jpg | 500]]
		- in output , <br>1) in firefox , tab is reloading on & on <br>2) & data request has been stopped via BurpSuite - cuz that data request is not going to the server
		- in output , u can see <br>- "GET" method <br>- Host : tells what u're accessing Eg : currently we're accessing google - means google request we did<br>- User-Agent : taking details of browser + OS <br>- Accept : what server can accept like html , xml files
		- if u click on "Forward" OR "turn OFF Intercept" , in both cases - request will move forward
		- STEP 5.2 : click on "Forward" btn , output : first data request (of the search query) will go forward + <br>in browser - google is loaded (instead of wscubetech) cuz right now the data request reached to google - not wscubetech
		- STEP 5.3 : click on "Forward" btn again & again - in order to send all the data packets (of the search query) to server <br>OR directly click on "intercept OFF" btn - to send all the data requests in one go ✔
		- output : in firefox , that tab loaded successfully - cuz all data requests reached to the server
		- STEP 5.4 : open the [wscubetech](https://wscubetech.com) -> scroll down & reach at 2nd section -> click "Contact Us"
		- STEP 5.5 : fill the contact form with correct details <br>![[27_lecture-14-M3.jpg | 300]]
		- STEP 5.6 : in BurpSuite , now turn ON intercept
		- STEP 5.7 : again come on that contact form -> click "Send Message" btn , <br>- output : now BurpSuite stop the data packets from sending those details <br>- means those data packets came out from our browser ✔ <br>![[27_lecture-15-M3.jpg | 500]] 
		- in output , now u can write anything u want - cuz client-side security will not stop u <br>- & server also not stop those details - cuz no server-side security implemented like this <br>![[27_lecture-16-M3.jpg | 500]]
		- so these details will get uploaded directly on the server , <br>so we can inject malicious data or tons of data for DOS attack on the website
		- Advice : don't try this on those websites which u don't have authority ✔
- when u don't have work related to BurpSuite , then stop the proxy from the browser <br>otherwise u won't able to do searches on browser ✔
	- STEPS : to close the proxy from the browser : <br>in firefox , settings -> search "proxy" -> click "proxy settings" btn -> select "No Proxy"
	- so if u're not using BurpSuite - then select "No Proxy" - otherwise errors comes 
	- if u select "manual proxy configuration" - then data request will not go forward - cuz BurpSuite is close <br>- selecting "manual proxy configuration" : means send the data requests via BurpSuite
- Testing websites : [vulnweb](https://testphp.vulnweb.com)
	- in this website , search for a form (like signup , login) - in order to do DOS attack 
	- but if server-side security is implemented for that form - then not possible

---
### Homework
1. 

---
### End of the lecture (Doubts) :
- Advice : if find something crap or stuff in vid or lecture - then u can skip ✔
	1) Mistake u did while writing notes : above u wrote - download & installation steps for BurpSuite
	2) writing these kind of stuff is not necessary even it's not gonna help u in CEH or OSCP journey or in penetration job
	3) so think twice before doing anything whether it's important or not or u can skip that stuff
	- before writing anything - understand how much important it's + useful , if not then skip it
- Q : is BASH a actual programming language?
	- Ans : Yes there's language here. It's usually called "shell scripting". It's a scripting language. <br>u will often see these as `.sh` files. They can have loops, variables, conditions & <br>many other things u'd expect from a normal programming language but are executed directly <br>in the shell as opposed to being compiled by another program first.
	- reference : reddit


