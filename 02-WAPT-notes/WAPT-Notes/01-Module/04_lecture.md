#WAPT-notes  

---
### what we'll learn
1) what are cookies
2) usecase of cookies
3) how to manipulate cookies with practical

### Platform used
- tryhackme.com

### Overview
- This Topic is vv imp for session management⭐
- whatever attacks are done without cookies are rare
- Cookies most important for session management ⭐

---

### Topics - Explanation

1) <u>What are Cookies</u>
	- Cookies are small bits of data which is stored in the browser
	- Different browsers store different cookies - cookies which are stored in all browsers are not same
2) <u>Purpose/usage of Cookies</u>
	- *used for session management* 
		- Eg of session management 
			1) let's say you're logged in on twitter & once you logout from twitter then that session will be removed from the browser
			2) but you're logged in already on twitter & you closed the browser & after some point of time , you came again & open the twitter in your same browser (which u were using earlier) then twitter will get open without asking login cuz in cookie , time mentioned that the user logged in this time & cookies are maintained ✔
	- *used for advertising* 
		- Eg : when you saw a product on amazon then advertising will shown related to that product 
		- so due to cookies you are tracked
		- or you'll get pop up from a website (which u're currently on) for accepting cookies
	- Cookies are information about users that a web server uses them to remember ✔
3) <u>why cookies ? or importance of it</u>
	- *importance of it*
		- cuz `HTTP` protocol is stateless (means we can't track `HTTP` protocol) but cookies are used to track or track user data or to track shopping data of your browser , we can use cookies to track them ✔
		- but `HTTP` protocol can't be track to know about your shopping data from your browser or app ✔
		- what you have done in that webapp or for how much time you stayed logged-in there , etc are managed by cookies ✔
	- *parts of cookies*
		- generally , cookies divided into 4 parts : 
			- 1st - the name of the cookie : used to identify the name of the cookie
			- 2nd - a value : tells where data is stored
			- 3rd - an expiry : tells when the browser will get rid of or remove the cookie automatically . 
				- Eg : let's say today is Thursday & time in defined that browser will destroy the cookie on Saturday , so till will be defined there
				- so we can define a expiry with date & time of a cookie
			- 4th - a path : tells what requests that the cookie will send with 
				- Eg : Generally , where the cookie is set/defined then the cookie with that thing will be send definitely
	- *Who set/define the cookie in the browser*
		- Generally , a web server define/set the cookies by a `Set-Cookie` header & `Set-Cookie` header comes inside `Reponse-Headers`
		- & we can define/set the cookies via JS inside your browser
4) <u>for what purpose Using Cookies</u>
	- when u login to a webApp , then u'll get `a Session Token`
	- This Session Token helps/allows the web server to identify that request is done by u
	- *Eg of importance of a Session Token* ⭐
		- let's say you're logged-in in amazon webapp & at this time , on the web server , multiple requests coming simultaneously & many customers also logged-in on amazon webapp
		- so then how a web server will identify that requests came from your side i.e via Cookies ✔
		- that's why cookies are extremely imp cuz only the cookies helps the web server to identify that the requests are send from u
	- *what happen if someone steal your session token*
		- Eg : let's say your if these cookies (which are maintained by the browser) steal by someone (via Man-In-the-middle-attack - burp suite , so we can intercept if you & someone are on the same internet connection)
		- so if someone steal all of your cookies via MITM (man in the middle attack) then the web server will think that request has been done by someone (who looks like u) but you didn't done any request
		- so this how u can impersonate (means actually u're not that person but you're showing yourself as him - means faking/pretending) to the web server ✔
5) <u>Manipulating Cookies - how u can manipulate cookies</u>
	- STEP 1 : open the browser dev tool > application tab > Storage section
	- we can also create our custom cookie
6) <u>Alternatives - useful to know</u>
	- we have LocalStorage & SessionStorage - both have a similar functionality but not sent with HTTP requests by-default
7) <u>More on Cookies</u>
	- reference : [Using HTTP cookies - HTTP | MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
	- *Define the lifetime of a cookie*
		- `Set-Cookie: id=a3fWa; Expires=Thu, 31 Oct 2021 07:28:00 GMT;`
		- this is define by a web server automatically 
		- but if you're deleting cookies manually then this date & time doesn't mean anything
	- *Restrict access to cookies (how to protect cookies from unknown access)*
		- majorly , a cookie has 2 attributes to secure the cookie i.e `Secure` & `HttpOnly` ✔
		- if in a cookie , `Secure` attribute flag is defined then means that cookie will not use `HTTP` protocol , only `HTTPS` going to be used by that cookie ✔
			- `Note ⭐` : sometimes we send the `HTTPS` protocol as `HTTP` protocol using burp suite or by doing any kindof manipulation in packets. ✔
			- so we can't able to send the request , that `cookie` is set/define as `Secure` attribute flag. so due to this , MITM , etc attacks can't possible in that cookie ✔
		- if in a cookie , `HttpOnly` attribute flag is define 
			- means attacks which are related to JS like `document.cookie()` - is a payload ✔
			- so JS & XSS (Cross site scripting) both have a payload that can be used ✔
			- means stealing cookies via XSS is not possible , if u set/define the cookie as `HttpOnly` attribute ✔
	- *where cookies are sent*
		- there are 2 attributes i.e `Domain` & `Path`
		- Eg of `Domain` : if u have an webapp as xyzz.com , so value of `Domain` attribute must be define/set as xyzz.com or u can set the subdomain also but if the website is xyzz.com but value of `Domain` attribute set as something else then its insecure configuration
		- Eg of `Path` : only define/set the path of your application like `/docs` or `/docs/web` , etc... but path is define as empty like this `/` then this also not good which shows insecure configuration
	- *`SameSite` attribute of cookies*
		- used to prevent CSRF (Cross-Site Request Forgery) attack
		- Eg : if you're logged-in in a webapp & you got the link from somewhere or someone send that & if u open that link in a tab inside the same browser (which u already logged-in in a webapp) , then that link/attacker might do changes on that webapp which u logged-in
		- so via CSRF attack , attacker can make u to perform unintended actions
		- so if there is `SameSite` attribute defined to the cookie then attacker can't do anything
	
### Tasks
- see more on `SameSite` attribute , http cookie

### Practical Tasks

- STEP 1 : open demo.testfire.net > press F12 > refresh the page again
- STEP  2 : `application` tab > inside storage - Cookies 
	- Eg of Cookie : u'll find the cookies of this website as this ![[WAPT-lecture-4-0.jpg]]
	- if u see the `Path` is empty which means this webapp is vulnerable , so `Path`  shouldn't be empty ✔
	- but this webapp set the `HttpOnly` & `Secure` attribute inside the cookie which is good✔
	- this webapp doesn't define `SameSite` attribute , so we can perform crsf attack

