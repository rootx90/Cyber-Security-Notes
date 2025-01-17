#WAPT-notes

--- 
### what we'll learn
> Lecture Name : What is a Brute Force Attack? Practical Demo
> 1) what's Brute Force 
> 2) Practical Work : Brute Force attack

### Overview
- we'll see Brute Force Attack & it's Practical work 
- Advice : try this attack on Demo Websites only , don't use it on official websites
---

### 1. What is Brute Force attack
- it's a `trial-and-error method` , used to get/obtain info such as user, password or personal identification number (PIN)
- in it, we don't put password manually , we use automated software (like Burp-Suite , etc.) <br>
	used to generate a large number of consecutive (one by one) guesses as to the value of the desired data ✔️
- it's aka brute force cracking or simple brute force
- `Brute Force` : means we're attacking with too much force - means we took a list of many usernames & passwords <br>
	i.e dictionary attack (type of brute force attack) , so within 1min , that automated software do trial-and-error <br>
	& then it shows which is passed & which are failed ✔️
- it's used by criminals to crack encrypted data or by security analysis (white hat) to test an organization's network security 

### 2. Practical Work : Brute Force attack
- STEP 1 : setting up in burpSuite
	- STEP 1.1 : in burpSuite -> proxy tab -> OFF the intercept
	- STEP 1.2 : now configure the proxy , in proxy tab -> options -> uncheck the localhost URL -> click "edit" btn -> <br>
		write 8085 port & loopback will remain `127.0.0.1` -> click ok -> now check the localhost URL for running mode
- STEP 2 : in chrome , do the same settings (so that it can intercept means packets will be captured in the middle ✔️)
	- STEP 2.1 : chrome settings -> search xy -> click on "Open Proxy settings" -> in "internet properties" popup , <br>
		click "LAN settings" -> tick the checkbox of "Proxy server" & Address -> `127.0.0.1` , Port `8085`
	- STEP 2.2 : uncheck "automatically detect settings" -> click ok -> ok
	- now BurpSuite can intercept
- STEP 3 : in BurpSuite -> proxy -> intercept , ON the intercept
- STEP 4 : now we'll do brute Force attack
	- STEP 4.1 : in chrome search , write `demo.testfire.net` , <br>
		output now u'll see that site will not get loaded cuz BurpSuite captured the packets ✔️
	- `intercept is ON` : means it becomes man-in-the-middle , so all those requests intercepted which are going to the server & <br>
		all those requests packets will be taken away in the middle by a attacker ✔️
	- STEP 4.2 : in burpSuite , proxy -> intercept -> click on `forward` btn again & again till "Raw" tab gets blanked -> <br>
		click OFF the intercept
	- STEP 4.3 : in burpSuite -> in proxy -> HTTP history , <br>
		output : burpSuite captured the packets of that website 
		<br><img src="../../notes-pics/03-Module/24_lecture/24_lecture-0-M3.jpg" alt="" width="300"/>
	- STEP 4.4 : in chrome -> in the website -> click "sign in" & we don't the username & password
	- STEP 4.5 : before doing anything , first see whether login page is captured or not, so burpSuite capture that also 
		<br><img src="../../notes-pics/03-Module/24_lecture/24_lecture-1-M3.jpg" alt="" width="300"/>
	- STEP 4.6 : in proxy tab -> intercept -> ON the intercept -> write anything in username & password input field -> click login , <br>
		output : now in BurpSuite , in proxy tab -> intercept tab -> in Raw tab -> burpSuite captured the username & password
	- STEP 4.7 : in Raw tab -> right click -> click on "send to intruder" , in intruder tab -> position tab -> click clear & <br>
		we'll keep `uid=admin` cuz to capture the admin's (username & password)
		- & we'll add payload symbol on password - so that whatever the password we'll use while login - those passwords <br>
			will be added in a list ✔️
	- STEEP 4.8 : let's create a list of password , in intruder -> payloads tab -> in payload options section -> <br>
		in `add` input field , write these words `admin` `administrator` `test123` `hack123` `admin123` , so add them one by one like this 
		<br><img src="../../notes-pics/03-Module/24_lecture/24_lecture-2-M3.jpg" alt="" width="300"/>
	- STEP 4.9 : in Positions tab -> select only password value -> click "add" btn for payload symbol like this 
		<br><img src="../../notes-pics/03-Module/24_lecture/24_lecture-3-M3.jpg" alt="" width="300"/>
	- STEP 4.10 : click "start attack" btn (& if any unknown popup comes then click on ok) ,<br>
		output : now mostly password payloads will get `200` status but `admin` has `302` i.e 
		<br><img src="../../notes-pics/03-Module/24_lecture/24_lecture-4-M3.jpg" alt="" width="300"/>
    	- here length of `admin` (which has 302 status) is 576 but others have same length
    	- `Note` : if that payload password has different length (than others payload password in a list) <br.
			then means we crack the password ✔️
    	- so password of the website , so admin account has `admin` password (i.e default password)
- STEP 5 : in burpSuite -> Proxy -> intercept tab -> click "drop" till all the packets will get dropped -> OFF the intercept
- STEP 6 : in chrome browser -> search `demo.testfire.net` -> click "sign off" -> click "sign in" -> <br>
	write username `admin` & password `admin` -> click login , output : now we logged-in & we got the info of admin account logins
    - so we successfully did via brute force attack & we compromised the website <br>
		& now we can manipulate users details which are under admin account

