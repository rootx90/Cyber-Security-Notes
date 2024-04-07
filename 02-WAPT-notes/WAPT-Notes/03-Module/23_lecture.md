#WAPT-notes

---
### what we'll learn
> Lecture Name : Sql injection attack in hindi? Practical Demo
> 1) about SQLi
> 2) How authentication page i.e login page works for a new user & existing user
> 3) Practical Demo

---

### 1. About SQLi
- it refers to an injection attack wherein an attacker execute malicious SQL statements (aka malicious payload) <br>
  	that control a web app's database server (aka generally RDMS)
- & since an SQL injection vulnerability could possibly affect any website/webapp that use an SQL-based database , <br>
	this vulnerability/issue is one of the oldest & most dangerous of webapp vulnerabilities
- via an SQL injection vulnerability , an attacker can use it to bypass a web app's authentication & <br>
	authorization mechanisms (means if he/she doesn't have username & password of the user then still that attacker can login) <br>
	& retrieve the contents of an entire database. 
- SQL injection can also be used to add, modify & delete records in a database & affect data integrity

### 2. How auth page i.e login page works for a new user & existing user
- website : `demo.testfire.net`
1) authentication page if u're a new user
	- if u're a first time user then for "signup" , we have fields i.e username & password & once filling those details , <br>
		those details will get stored in database (that database could be SQL or NoSQL). ✔️
	- Diagram of explanation <br><img src="../../notes-pics/03-Module/23_lecture/23_lecture-0-M3.jpg" alt="" width="300"/>
2) login page if u already a user 
	- once u fill the "login page" then those details will check , are those details exists in the database or not using a SQL language ✔️ , <br>
		Diagram Explanation <br><img src="../../notes-pics/03-Module/23_lecture/23_lecture-1-M3.jpg" alt="" width="300"/> 
	- Define Query language : used to communicate to a database for different operations like add, delete records , etc ✔️
	- so if those details exists in the database then the user logged-in otherwise throw error ✔️
	- true - comes when details exists (of the user) in the database , so as a hacker , <br>
		if we do something like database always return true value like 1=1 (1 always equal to 1) , 2=2 & so on. <br>
		so if we use these in the SQL statement then we'll able to login ✔️

### 3. Practical Demo - SQL injection attack
- STEP 1: `demo.testfire.net` , click "sign in" menu tab , login page will open with 2 fields i.e username & password
- STEP 2: so now we'll choose/write a SQL statement (in "username" input field) that always to database & always return true ✔️
	- STEP 2.1: in "username" input field , so we'll choose username or sql statement which always go to database <br>
		& database always return true value. so in "username" input field write this  `1=1--` <br>
		& we put double hyphen after `1=1` which means we can put any random password , <br>
		so password value will not be checked in database cuz behind the scene , password value will get commented, <br>
		so ultimately write this ✔️ <br><img src="../../notes-pics/03-Module/23_lecture/23_lecture-2-M3.jpg" alt="" width="500"/>
	- output : we'll get error i.e `'username = '1=1'` <br><img src="../../notes-pics/03-Module/23_lecture/23_lecture-3-M3.jpg" alt="" width="500"/>
	- STEP 2.2: for testing purpose , let's write something else to check whether we're getting same error or <br>
		a different error, so in "username" input field as `ethical sharmaji--` (we again put double hyphen to comment the password) ✔️ <br>
		& in password input as any random & click login
	- output : so again same error coming
	- so we need to give that format as we're getting error
	- STEP 2.3: in username input field as `'username 1=1--` & password any random & click login , <br>
		output : we're getting in double initial single quote 
		<br><img src="../../notes-pics/03-Module/23_lecture/23_lecture-4-M3.jpg" alt="" width="500"/>
	- means we need to give something else instead of `username`
	- STEP 2.4: in username input field as `' or 1=1--` (means either a empty space or 1=1 , anyone of them is true then we'll get true) <br>
		& password as any random & click login , output : we'll logged-in 
		<br><img src="../../notes-pics/03-Module/23_lecture/23_lecture-5-M3.jpg" alt="" width="500"/>
	- so as a Admin user , we logged-in via SQL injection attack , think about banking website
