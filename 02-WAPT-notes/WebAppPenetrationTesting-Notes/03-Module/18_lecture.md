#WAPT-notes  
### Overview
- Cross-Site Request Forgery aka CSRF
### what we'll learn
- what's CSRF
- CSRF Practical Demo on DVWA application (vulnerable app)
- Prevention/Remediation of it

---
### Topics - Explanation

1) <u>What's CSRF attack</u>
	- u can understand any attack , just look at it's name
	- it comes under OWASP Top 10 attacks 
	- reference : [Cross Site Request Forgery (CSRF) | OWASP Foundation](https://owasp.org/www-community/attacks/csrf)
	- understanding CSRF
		- in CSRF , the `cross-site` word means the end user & he/she is using an application & the request is not coming from that application which he/she is using , means that request (is coming from an attacker) wants the user to make/follow unextend behavior/actions ✔
		- Eg : Let's say you're in xyz website (it's social media webapp) & u're already authenticated/logged-in , then attacker wants to make u to execute unwanted actions like changing password via forging that request (`forgery` : means fake request ) aka CSRF✔ 
	- Define : CSRF is an attack that forces an end user to execute unwanted actions on a web application in which they’re currently authenticated ✔
	- this attack is not used for data theft , it's for to change the data or change the state like a attacker take advantage of those users who are authenticated in a application such as u're transferring money from someone to yours banking application , then attacker can change the bank account number & he/she will transfer those amount in his/her own bank account ✔
	- it's severity/damage is very critical & high ✔
	- *To avoid/prevent it* ✅
		- we use Token , so that attacker not able to know cuz the token require special validate/update , in order to protect/save/defend from this attack
		- we can use POST method also to prevent it 
	- XSS & CRSF are both different attacks 
2) <u>CSRF Practical Demo on DVWA application</u>
	- osboxses - is a virtual machine
	- STEP 1: open Ubuntu OS & `ctrl + alt + T` to open terminal
	- STEP 2: command run `sudo -i` : means to come in root user directory
	- STEP 3: command run `docker ps --all` : in order to check is any container running or not
	- STEP 4: so no container running right now , so to run the container of DVWA , command run `docker run --rm -it -p 80:80 vulnerables/web-dvwa` 
		- & hit enter & we'll get output ![[WAPT-lecture-18-0.jpg]]
	- STEP 5: in firefox , write URL `localhost:80` & hit enter , u'll get DVWA login page & default both username & password is `admin`
	- STEP 6: after login , scroll down & click on `create/Reset database` button & then scroll down & click on `Login` button
	- STEP 7: now login credentials are : username is `admin`  & password is `password` , so we logged-in 
	- STEP 8: now let's do CSRF attack , 
		- so click on `CSRF` menu i.e ![[WAPT-lecture-18-1.jpg]]
		- STEP 8.1: it's a page where we can change the password , so for testing purpose , write `ethical` as a password & click on `change` button & click on `logout` button
		- STEP 8.2: now username as `admin` & password is `ethical` & click `login` button
		- so password is `ethical`
	- STEP 9: so click on `CSRF` menu tab & copy the URL i.e `localhost/vulnerabilities/csrf/`
		- STEP 9.1: open the terminal & run command `gedit`
		- STEP 9.2: paste the URL in notepad & save it on Home as `notes.txt`
		- STEP 9.3: now we need `form` code of this webpage `localhost/vulnerabilities/csrf/` , so right click on the webpage & click `view page source`
		- STEP 9.4: copy the `form` code as it is like this ![[WAPT-lecture-18-2.jpg]]
		- STEP 9.5: open terminal & run command `gedit` & paste the code & do some changes inside the `form` code like this
			```html
			<form action="http://localhost/vulnerabilities/csrf" method="GET">
				<p>Click here to change your password </p>
				<input type="hidden" AUTOCOMPLETE="off" name="password_new" 
					value="hacked">
				<input type="hidden" AUTOCOMPLETE="off" name="password_conf" 
					value="hacked">
				<input type="submit" value="Change" name="Change">
			</form>
			```
			- *understanding password update code*
				- `value="hacked"` : means value for "password" & "password confirmation" is `hacked` , in order to update or change the password ✔
				- URL value of `action` attribute : is to cross the request & send the user on this URL website which contain password update ✔
			- so this is our goal as a attacker to send the user on that URL
		- STEP 9.6: save the file in Home as `csrf_poc.html`
	- STEP 10: run command `ls` in terminal & run command to open firefox i.e firefox `csrf_poc.html`
		- & hit enter , output : ![[WAPT-lecture-18-3.jpg]]
	- now let's say there is a end user & he/she is using "dvwa" & he/she got the different link to change the password (like attacker send the link to that end user via social engineering attack OR via inserted image OR via Ads & u clicked on it) ✔
	- as a attacker can write "click the below button to get 1M euro or dollars" ✔
	- STEP 11: once u clicked on that `change` button , now password is changed now , 
		- so output ![[WAPT-lecture-18-4.jpg]]
	- means once that end user clicked on that `change` button then the attacker kept that password which he/she (attacker) wants & u as a end user don't know what's the password ✔
	- so click on `logout` tab & try to login this credentials i.e username `admin` & password `ethical` & login will failed
	- so password is `hacked` 
### Summary - CSRF Practical Demo
- so the end user intended action was not to change the password but to login on that website
- but the attacker take a advantage for that end user (when that end user was logged-in with his/her credentials on that website - means authenticated) & the attacker send the link (which could be Ads , image , etc)
- & once that end user clicked on that & the password has been changed into that password which was created/made by the attacker
- Eg : let's say this website as banking application & on that application CSRF attack might be possible & u're authenticated on it then the attacker can take the advantage of it & then the attacker might do fraud things like stealing , etc
