#WAPT #penetration-testing
### what we'll learn
- what's Brute Force attack
- practical Demo

---
### Topics - Explanation

1) <u>What is Brute Force attack</u>
	- it's a `trial-and-error method` , used to get/obtain info such as user, password or personal identification number (PIN) ✔
	- in it, we don't put password manually , we use automated software (like Burp-Suite , etc.) used to generate a large number of consecutive (one by one) guesses as to the value of the desired data ✔
	- it's used by criminals to crack encrypted data or by security analysis (white hat) to test an organization's network security 
	- it's aka brute force cracking or simple brute force
	- here `Force` word : means we took a list of many usernames & passwords i.e dictionary attack (type of brute force attack) , so within 1min , that automated software do trial-and-error & then it shows which is passed & which are failed ✔
2) <u>Practical Demo - Brute Force attack</u>
	- STEP 1: setting up in burp Suite 
		- STEP 1.1: in burp Suite > proxy tab > off the intercept
		- STEP 1.2: now configure the proxy , so proxy tab > options , uncheck the localhost URL then click on `edit` > write 8085 port & loopback will remain `127.0.0.1` & click ok & now check the localhost URL for running mode
	- STEP 2: same settings we'll do in chrome , so that it can intercept means packets will be captured in the middle ✔
		- STEP 2.1: chrome settings > search xy > click on "Open Proxy settings" > in "internet properties" popup , click "LAN settings" > tick the checkbox of "Proxy server" & Address -> `127.0.0.1` , Port `8085`
		- STEP 2.2: uncheck "automatically detect settings" & click ok & ok
		- now Burp Suite can intercept
	- STEP 3: in Burp Suite > proxy > intercept , on the intercept
	- STEP 4: now we'll do brute Force attack
		- STEP 4.1: in chrome search , `demo.testfire.net` , now u'll see that site will not get loaded cuz BurpSuite captured the packets ✔
		- `intercept is on` : means it becomes man-in-the-middle , so all those requests intercepted which are going to the server & all the requests/packets will be taken away in the middle by a attacker✔
		- STEP 4.2: in burp Suite , proxy > intercept > click on `forward` button again & again till `Raw` tab gets blanked & click off the intercept
		- STEP 4.3: in proxy > HTTP history , burp Suite captured the packets of that website ![[WAPT-lecture-24-0.jpg]]
		- STEP 4.4: in chrome , inside the website , click "sign in" & we don't the username & password
		- STEP 4.5: before doing anything , first see whether login page is captured or not, so burp Suite capture that also ![[WAPT-lecture-24-1.jpg]]
		- STEP 4.6: in proxy tab > intercept > on the intercept & write anything in username & password input field & click on login , now in Burp Suite , in proxy tab > intercept tab , in Raw tab , burp Suite captured the username & password
		- STEP 4.7: right click & click on `send to intruder` , in intruder tab > position tab , click on clear & we'll keep `uid=admin` cuz to capture the admin's username & password & we'll add payload symbol on password so that whatever the password we'll use while login
		- STEEP 4.8: let's create a list , in intruder > payloads tab, in payload options section, in `add` input field , write these words `admin`, `administrator`, `test123`, `hack123`, `admin123` , so add them one by one like this ![[WAPT-lecture-24-2.jpg]]
		- STEP 4.9: in Positions tab , select only password value & click on `add` btn for payload symbol like this ![[WAPT-lecture-24-3.jpg]]
		- STEP 4.10: click on `start attack` button & if any unknown popup comes then click on ok , now mostly password payloads will get `200` status but `admin` has `302` i.e ![[WAPT-lecture-24-4.jpg]]
		- here length of `admin` (which has 302 status) is 576 but others have same length
		- Note : if that payload password has different length (than others payload password in a list) then means we crack the password ✔
		- so password of the website , so admin account has `admin` password (i.e default password)
	- STEP 5: in burp Suite > Proxy > intercept tab , click on drop till the end so that all the packets will get dropped & off the intercept
	- STEP 6: check `demo.testfire.net` & click "sign off" & now "sign in" & write username `admin` & password `admin` & click login , now we logged-in & we got the info of admin account logins
	- so we successfully did via brute force attack & we compromised the website & now we can manipulate users details which are under admin account

