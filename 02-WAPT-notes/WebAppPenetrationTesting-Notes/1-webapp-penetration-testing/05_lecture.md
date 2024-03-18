#WAPT-notes  

### Overview
- we'll do practical web mini CTF (capture the flag) of this complete webApp fundamentals

### what we'll learn
- how to do HTTP requests without any browser
- how to create cookies
- how to GET cookies
- how cookies details come when u get cookies

-----

### Topics - Explanation (Web Mini CTF)

1) <u>Making HTTP requests</u>
	- we can do/make HTTP requests without browsers i.e cURL (a programming lang) ✔
	- `cURL` is a small utility/CLI-browser & allows to automate repetitive tasks ✔
	- if you're doing OSCP then `cURL` is v imp & v useful
2) <u>Intro to cURL</u>
	- By default , cURL will perform GET requests on whatever URL you gave it. Eg : when u type url or anything on URL address bar of the browser means we're doing GET request , same as in cURL 
		```
		curl https://tryhackme.com
		```
		- this command means `curl` making GET request on that URL
	- `-X flag` - used to specify the request type are as follows :-
		- POST request via curl i.e `-X POST`
		- to specify data to POST i.e `--data` or `-d`
	- `Note⭐`: cookies are not shared b/w different browsers  ✔
		- when you hit/made the request for cookies via `curl` then cookies will not shown in the browser ✔
		- Eg : u're creating/getting a cookie on firefox then the same cookie will not shown/open in different browsers except firefox ✔

### Practical Tasks

> There's a web server running on http://10.10.40.131:8081 - connect to it & get the flags/issues/vulnerable-programs
> ![[WAPT-lecture-5-0.jpg]]
- do it after connecting with VPN

- `Ques 1)` : what's the GET flag ? 
	- above , to make a GET request , we need to go path -> /ctf/get
	- Ans : `curl http://10.10.40.131:8081/ctf/get`
	- Output : `hm{162520bec925bd7979e9ae65a725f99f}` - this GET flag u got
	- here `http://10.10.40.131:8081` - is a complete web server
- `Ques 2)` : What’s the POST flag?
	- Ans : `curl -X POST -d "flag_please" http://10.10.40.131:8081/ctf/get`
	- Output : `hm{3517c902e22def9c6e09b99a9040ba09}` - this is POST flag
	- why `-d` comes with a POST request - coz with a POST request , a body header also come & in `body` must have data , body shouldn't be empty ✔
- `Ques 3)` : What’s the “Get a cookie” flag?
	- we'll in 2 ways i.e browser way & via curl
	- via Browser way , 
		- 1) paste it `http://10.10.40.131:8081/ctf/getcookie` on URL address bar then u'll get "check your cookies" message 
		- 2) press F12 > storage > cookies > you'll get value , so that value is a flag i.e `thm{91b1ac2606f36b935f465558213d7ebd}` - we got a flag of `GET Cookie`
	- via curl , ![[WAPT-lecture-5-1.jpg]]
- `Ques 4)` : What’s the “Set a cookie” flag?
	- via browser way , 
		- 1) open firefox browser > run  `http://10.10.40.131:8081/ctf/getcookie`
		- 2) press F12 > storage > cookies 
		- 3) click on `+` button to add custom cookies
		- 4) write name as `flagpls` , value as `flagpls`
		- 5) then change the path of URL as `http://10.10.40.131:8081/ctf/sendcookie`
		- output : we'll get "set a cookie" flag as `thm{c10b5cb7546f359d19c747db2d0f47b3}`
	- via curl way , ![[WAPT-lecture-5-2.jpg]]

### Summary
- this is how we do GET & POST requests via `curl` CLI language
 