#WAPT-notes  

---
### what we'll learn
> Lecture Name : Web Fundamentals #1 How do we load websites? HTTP Verbs?
> 1) how do we load websites 
> 2) how a web requests goes
> 3) how a web requests works
> 4) structure of a web request
> 5) types of HTTP requests

### Platform used
- tryhackme.com

### Overview - web-fundamentals (of tryhackme.com)
1) what's HTTP request , HTTP responses
2) what's web server
3) Cookies
4) Capture the Flag (CTF)

---

### How do we load websites ?
- we'll see how website or a webapp loads inside the client machine
1) Finding the server
    - Eg : u (client) wrote the "tryhackme.com" URL , so "tryhackme.com" is a domain name <br>
	  	but the server can't understand by just writing "tryhackme.com" , cuz server understand the `IP address` language
    - but humans can't understand or remember `IP address` of any websites , <br>
		that's why `Domain Name Services (DNS)` came , so humans started using domain names for each websites 
	- Q : what's DNS ✔️<br>
        Ans : DNS means like yellow pages - means there's a directory which contains phone numbers of people - so same with DNS<br>
		DNS is like a giant phone book that takes a URL (like https://tryhackme.com/) & turns it into an IP address. <br>
        This means people don't have to remember IP addresses for their favorite websites
    - so whenever you write a URL as Domain Name of that website & hit Enter then 1stly a DNS request will go to the server <br>
		then server will check inside it's own directories whether this "tryhackme.com/" domain name have or not , <br>
		so inside the server's directory , if server have it then server will translate it from the Domain Name into its IP address
	- so first server will check inside it's own directory whether that have or not , <br>
		if server doesn't have it then u'll (client) get generic error , <br>
		if server have `IP address` of that Domain Name then that Domain Name will get it's own `IP Address`
	- Q : what is IP Address ✔️
		- Definition : on the internet , each devices (which are connected to the internet) have their own unique `IP address` , <br>
			means in the corner of the world , any device which is connected to the internet , <br>
			that device will have an unique `IP address`. Eg: web server also has it's own unique `IP address`
		- it's look like this `100.70.172.11` aka `octet` - means 8-bit number i.e this (`x.x.x.x`)
		- so an `IP Address` is formed/made of 4 groups of numbers. <br>
			Eg : `100` - is 1st group , `70` is 2nd group , `172` is 3rd group & `11` is 4th group
		- Range of each group of an `IP address` is `0 - 255` , will never see till 256 range , <br>
			like in programming , array index starts from 0 , so an IP address's range also starts from `0`
	- this is how the process happens to find the server of that Domain Name , <br>
		if the `IP address` of that Domain Name exists then we'll get the `IP address` of it
2) Loading some content
    - here we'll see : as earlier said , u searched "tryhackme.com" - then the server got the IP address (of this domain name) <br>
		but the content which will come in ur (client) browser <br>
		Q : how that content will come in ur browser ? - means content (HTML , CSS , JS, etc assets files..) <br>
		how all these file will get loaded on the client machine ✔️ <br>
		Ans : so content loaded via a `HTTP GET request`
    - Q : what is an HTTP GET request ✔️
		- `GET` request : it's a type of HTTP verb/method <br>
			Q : what's verb ? ✔️<br>
			Ans : means GET , POST = these are verbs <br>
			Q : why HTTP comes with GET request ✔️<br>
			Ans : cuz HTTP is a type of GET request - cuz we're talking about web <br>
			Q : what's GET ✔️<br>
			Ans : GET = means to get the content from the server to the client machine
    - Q : what is server & web server ✔️<br>
		Ans : server one who `serves` <br>
		Q : what things a server serves ✔️<br>
		Ans : it'll not serves a plate of foods - so here "server" is a web server , so the server will serves to the `web` <br>
			means it'll serves a web page
        - so when we say to the server that bring a `index.html` file of that Domain Name - then the server will send the`index.html` <br>
   			& it gets open inside the client machine , so this is a working of `web server`
		- Q : How this working of web Server is done OR how the server able to send the index.html file to the client machine ✔️<br>
			Ans : done when we (client) send a "GET request" to the server <br>
			so when we say to the server that "give that page" - only then the server will send content to us (client) <br>
			so the server automatically will not send anything to the client , so client have to do a GET request
    - so `HTTP GET requests` used to bring the resources/files/content <br>
   		from the server (whose has the `IP address` of that Domain Name) to the client machine
    - Eg of HTTP GET request : <br><img src="../../notes-pics/01-Module/03_lecture/03_lecture-0-M1.jpg" alt="Pic 1" width="600"/>
		- it's a output of "HTTP GET request" of neverssl.com - from client machine
		- wireshark - it's a free & open-source packet analyzer software.
    - Q : what is Protocol & why HTTPS came ✔️
		- most of the websites now use HTTPS
		- `HTTPS` : it's a secure (encrypted) version of HTTP & it works 99% same as HTTP but in secure way
		- `HTTPS` : use TLS 1.3 encryption , if a Domain Name has less than TLS 1.3 `HTTPS` <br>
			then it's a vulnerability in order to communicate without : 
			1) Other parties/hacker being able to send the data
			2) Other parties/hacker being able to modify the data
		- in old protocols , data can be read (cuz data goes in plain text & data wasn't encrypted) <br>
			eg : in HTTP protocol , data can be modified , so in old days , let's say a hacker using a packet sniffer tool (like Burp Suite) , <br>
			so via using this tool , hacker can intercept/catch/snatch the request & he/she can modify the request
		- Eg : let's say u're using banking website & u're transferring money in ur account <br>
			then a attacker can change the A/C no. to a different one via packet sniffer tool , <br>
			so that money goes to that different A/C no. , so HTTP was 0% secure - that's why HTTPS came
		- but HTTPS is not completely secure cuz if it is so , then our job will not be there in a company as a penetration tester , <br>
			so nothing is completely secure but HTTPS is secure than HTTP
    - Q : what is a web server ✔️
		- it's like a software which responds to the HTTP/HTTPS requests <br>
			means if u do a GET request via either HTTP or HTTPS - in order to bring that content <br>
			then a web server (which is a other party or a piece of a software) will responds to the HTTP/HTTPS requests
		- Eg of Popular web servers : Apache , Nginx , IIS , etc
		- bydefault `HTTP` runs on port 80 & `HTTPS` runs on port 443 <br>
			if u don't know about `port` - then see Networking Playlist : [Networking For Cyber Security - EthicalSharmaji YT](https://www.youtube.com/playlist?list=PLHOJoqBk02jR2iH1EO2KB4-8kwcagCR0i)
		- Generally , most of the CTFs (Capture the Flag) are based on websites , <br>
			which means if you get a open running web server on port 80 or port 443 , then u can attack & spread/exploit <br>
			reference to understand CTF : OSCP playlist of EthicalSharmaji YT
    - the actual content of the web page is normally a combination of (HTML , CSS & JS)
        1) HTML - for the structure of the page
   		1) CSS - make the page look fancy
   		2) JS - runs in the browser & allows u to make the pages dynamic & interactive
    - Q : 
        1) What request verb/method is used to retrieve page content ✔️ : `GET`
        2) What port do web servers normally listen/runs on ✔️ <br>
			Ans : generally , web servers runs on `port 80`

### More HTTP - Verbs/methods & requests formats
- there are 9 different HTTP "verbs" aka methods , Eg : are GET , POST & etc. <br>
	& each HTTP methods has different function <br>
	refer HTTP verbs : [HTTP request methods - HTTP | MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
- GET vs POST request
    - `GET` : used to retrieve/get the data from web server to the client machine
    - `POST` : used to send the data from the client machine to the web server <br>
    	Eg : adding a comment or contact form & etc. <br>
		Eg : in the "feedback form" , u fill/write & click on "submit" btn - then the form is action i.e POST <br>
    		so the request which goes i.e POST , not GET - cuz those input data goes inside server
	- conclusion : <br>
		POST request : means the data will be send as a "POST" to the web server <br>
		GET request : means the data will come as a "GET" from the web server
- a HTTP request is divided into 2 parts i.e <br>
	1st `verb` <br>
	2nd `path` for the server
	- Eg : `GET /index.html` - means get the index.html from the web server
    	- so atleast we need to tell the server that what - we want to bring to the client machine that's why `path` need to define
    	- "index.html" is inside the root path of the web server (not the linux root directory path) <br>
			means bring the "index.html" from the web-server's root path - we're saying this to the server
- `headers` of the request
	- used to give more information about ur request
	- information such as which type of the request it's , type of encoding, method, cookies & etc
- `body` of the request
	- in `POST` request , `body` is important cuz a `post` request is not considered valid without `body`
	- in `GET` request , `body` can be defined but generally the `server` skip/ignore the `body` , <br>
		means generally , `body` doesn't come in `GET` request but even if it comes in `GET` request then the `server` will skip it
- Eg : a GET request retrieving a simple js file <br><img src="../../notes-pics/01-Module/03_lecture/03_lecture-1-M1.jpg" alt="Pic 1" width="600"/>
    1) `GET /main.js HTTP/1.1` - means we're saying to the that get the main.js file via using `HTTP` protocol
    2) `HOST: 192.168.170.129:8081` - `192.168.170.129` -> it's a IP address & `8081` - is a port of the web server
    3) `Connection: keep-alive` - means keep the connection alive
    4) `user Agent` - tells about the browser (details + it's version) & sometimes it tells OS details (which is a loophole) of the client machine 
    5) `Accept: /` : means we can access from anywhere
    6) `Referer: http://192.168.170.129:8081` : means from it's originating
    7) `Accept-Encoding: gzip, deflate` - means types of encoding which can be accepted by the client machine
    8) `Accept-language` - means types of languages (which are define) only those can be accepted by the client machine
    - so from this `header` , u can know that the request is created from this (Chrome version 80, from window 10) ,<br>
		so this info is useful to use for forensics & analyzing packet captures
- [ ] Practical Task 
	- STEP 1 : open any website like `demo.testfire.net`
	- STEP 2 : press F12 key > network tab > select `all` tab
	- STEP 3 : reload the page again & you'll get all the content of that website , which means that what are the files which required to load that page completely
	- STEP 4 : click on a `demo.testfire.net` file > `Headers` , just look at the things
		- in General , u can see `Request URL` , `Request Method`, `status code`, `remote address`, `referrer policy`
		- in Request Headers , u can see `Accept` , `Accept-Encoding` , `Accept-language`, `Cache-Control`, `Cookie`, `Host`, `User-Agent`
- Responses
	- `Define` : means when we request from the web server then we get the response
	- it follows a basic structure of any HTTP request
    1) 1st line - `describes the status` : means the request is made by user <br>
		whether that request can be fulfilled by a web server or not, breakdown of status code , 404 : Not Found (general) `v imp ⭐`
        - `Note` : this status code breakdown is `v imp` till life time if u're doing debugging , webdev, security, 
        - `100 - 199` : used to give basic information
        - `200 - 299` : Successes response of GET request (200 OK is the "normal" response for a GET request)
        - if u get the success response of a GET request then status code will be `200` normally otherwise b/w `200 - 299` can be range
        - `300 - 399` : Redirects (the information you want is elsewhere)
        - Eg : let's u're opening/accessing a twitter page but u're not login then twitter will redirect u to it's login page
        - so in this case , generally status code is `302` 
        - `400 - 499` : contain always client side errors (browser based)
        - Eg : you did something wrong , like asking for something that doesn't exist on the server , requesting for wrong thing , so u'll get 404 status code
        - it is mostly useful for debugging
        - `500 - 599` : server errors
        - Eg : The server tried, but something went wrong on their side like `Bad Gateway - status code 502`
        - refer for more : [HTTP response status codes - HTTP | MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
	2) Response Headers `(v imp ⭐)`
		- STEP 1 : open any website like `demo.testfire.net`
		- STEP 2 : press F12 key %3E network tab > select `all` tab
		- STEP 3 : reload the page again & you'll get all the content of that website , which means that what are the files which required to load that page completely
		- STEP 4 : click on a `demo.testfire.net` file > `Headers` tab , in "Response Headers"
			- `HTTP/1.1` - means u requested for a page from the server & the server have that page , status code got `200 OK`
			- `Server` - Apache-Coyote/1.1 - it's also considered as `finding low vulnerability` cuz  it's showing this server & version of it 1.1
				- this website is vulnerable that's why we're `server` showing
				- otherwise strong website doesn't show 
				- u can check in `bug bounty` also due to which you can get the money like `50$` , `100$` for finding this issue only
			- `Content-Type: text/html;charset-150-8859-1` - means the data going to the server in the form of text & html form
			- `Transfer-Encoding`
			- `Date` : means showing the `client machine date & time` in real time who accessed the website
		- it's v imp cuz it tells mostly the web server & cookies of that website which you can use for testing such recession management , attacks , etc
		- it's also have a `body`
		- Eg : response to the GET request <br><img src="../../notes-pics/01-Module/03_lecture/03_lecture-2-M1.jpg" alt="Pic 1" width="600"/>
			- so for GET request , we'll get normal web content or information such as JSON
			- for POST request , information may be a status code or same as GET request

---

### Ques
1) Q : What verb would be used for a login ?<br>
	Ans : `POST`
2) Q : What verb would be used to see ur bank balance once u're logged in ? <br>
	Ans : `GET` cuz we'll get the page from the web server , so it's `GET` request 
3) Q : Does the body of a GET request matter ? yea/Nay
   - Ans : `Nay`
   - cuz in `POST` request , we need `body` cuz data goes to validate on the web server , so need `body`
4) What's the status code for "i'm a teapot ?" <br>
	Ans : `418`
5) What status code will you get if you need to authenticate to access some content & u're unauthenticated ?
   - Ans : `401`
   - means u're access the web page which needs login & signup but you didn't have account of that website but u want to signup/authenticate
   - then no response we'll get from the server right now , so this will be shown on client side
   - so client side means `400` series , so for unauthorized status code - `401`

---

### End of the lecture
- Advice : sir said do it side by side whatever he's teaching u
