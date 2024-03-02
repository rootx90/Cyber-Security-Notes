#WsCubeTech-CEH-notes 

---
### What we'll learn 
> Lecture Name : I.G (information gathering) using Search Engines & Google Dorks
> 1) What we do in Information Gathering ?
> 2) Types of Information Gathering (I.G) ? 
> - HomeWork

---

### What we do in Information Gathering ?
- Few Concepts + Practical Work related to Information Gathering are on [10_lecture-M2](10_lecture-M2.md)
- stuff done in information gathering :
	1. Personal Details
	2. Company Details
	3. System Information
	4. Gathering all Information about target/Victim <br>(Victim - means that person/system on which we're going to attack)
	5. Entities Belong to target <br>(Entities - means name , no. , etc)
	6. Technology <br>(means taking out information about technologies that Victim were/is using)

### Types of I.G ?
- 1st : Active & 2nd : Passive <br><img src="../notes-pics/02-Module/12_lecture/12_lecture-0-M2.jpg" alt="" width="500"/>
- in Active I.G , for Eg : 
	- u're asking from Kate about ally for information like where she live , her address , etc.
	- so here Kate also knowing or getting information that u're asking from her about ally
	- so either u're asking from Kate physically or via whatsapp message <br>- both will be consider as Active I.G
	- so when Victim knows that u're asking about Victim himself/herself , it'll be consider as Active I.G <br>cuz here u're doing Direct Interacting with someone about Victim ✔
- in Passive I.G , For Eg : 
	- gathering information without interacting - means Victim didn't know that u're collecting Information <br>about her/him - like going social media of Victim , etc websites - to know about the victim
- Q : u're getting information about that person from his/her Linkedin profile , so is it Active or Passive I.G<br>Ans : that's Active I.G , cuz when u view that person's Linkedin profile then Linkedin will <br>send the notification to that person about "This is a person who viewed ur profile" <br>- `imp Note ⭐` :  any information which make Victim aler/aware or Victim now knows about it <br>then it'll be Active I.G , not passive ✔
- Q : Information Gathering Practical did on WsCubeTech , is it Active or Passive I.G <br>Ans : that was Passive I.G 99% <br>- Mine thought - for 1% was Active cuz u visited on linkedin & linkedin will notify to Victim who visited
### use/pros of Information Gathering
> What're advantages when we do Information Gathering
> ➞ Importance of Information Gathering Example : [10_lecture-M2](10_lecture-M2.md)
1. Time Saving <br>- then we can do direct attack
2. Easy Processing
3. Accurate Attacking <br>- cuz we done the main thing i.e Information Gathering - due to which system got hacked

### Ways to do Information Gathering
- in [10_lecture-M2](10_lecture-M2.md) , we did information gathering about Victim (WsCubeTech) via 1st way/source i.e using Search Engines 
- here we'll see 2nd source i.e Google Dorks/operators (means Google Hacking Advance Techniques)
	- STEPS - to do Google Advance Search
		- STEP 1 : search "advance search" on google search engine
		- STEP 2 : click on "Advanced Search" link 
			- Pic<br><img src="../notes-pics/02-Module/12_lecture/12_lecture-1-M2.jpg" alt="" width="500"/>
			- `all these words` : means let's say we wrote -> Devendra hacking wscubetech forensic ,<br>so total 4 words in one sentence , `all these words` means all these 4 words should come<br>in search results
			- `this exact word or phrase` : means let's say we wrote -> Hacker ,<br>so `this exact word or phrase` means -> "Hacker" word should be there in search results
			- `any of these words` : means let's say we wrote -> ethical hacker wscubetech , <br>so if any word out of these 4 should come then show in search results
			- `none of these words` : means let's say we wrote -> youtube ,<br>so `none of these words` means we don't want "youtube" word on output <br>Eg : if u put "Hello world" in `none of these words` input field - then <br>output : `-hello -world` : so both words will get minus sign
			- `number ranging from` : means it's for when u're doing buying something , so input fields empty of this
			- `language` : don't select any language cuz if u select specific language like Hindi <br>then if that website is in English then output will not come 
			- `any region` : don't select any region cuz what if information which we need it's server on different country that's why ✔
			- `last update` : keep "anytime" , cuz we can get data which is vital & what if that data is old
			- `site or domain` : we'll not define domain or site name , cuz what if data is on different domain <br>Eg : if we write -> wscubetech , then search results will come only of wscubetech , not others
			- Advice : touching/modifying too much then output might come bad 🧠
			- `terms appearing` : means the output which will come , so where do u want that output to come <br>Eg : do u want that output on "in the title of the page" , etc . so "keep anywhere in the page"
			- `file type` : means in which form - u want that output <br>Eg : do u want that output in PDF , etc . so select it as "Adobe Acrobat PDF (.pdf)"
			- `usage rights` : do u want output in which filter form , so select "not filtered by licence"
		- STEP 3 : click on "Advanced search" button
		- Output : <br><img src="../notes-pics/02-Module/12_lecture/12_lecture-2-M2.jpg" alt="" width="500"/>
		- see how google did the search behind the scene , <br>- 1st : Devendra hacking wscubetech forensic -> comes as `all these words` <br>- 2nd : ethical OR hacker OR wscubetech -> comes as `any of these words` <br>- 3rd : "Hacker" -> comes as in double-quotes which means `Hacker` word must be shown in search result <br>- 4th : -youtube -> comes as firstly a hyphen sign added with "youtube" word <br>which means don't show youtube word in search result <br>- 5th : filetype:pdf -> means only pdf file must be shown in search result , not others file format
		- Eg : directly go in google search or google dorks , write `song song OR india "Arjit Singh" -youtube` <br>output : arjit singh related stuff will come but youtube stuff related to him will not come
	- in 2nd source - Advance techniques which is used for I.G i.e `Google Dorks/operators` are : 
		1. `cache:`
		2. `filetype:`
		3. `intext:` & `allintext:` 
		4. `inurl:` & `allinurl:`
		5. `intitle:` & `allintitle:`
		6. `inanchor:` - it's not useful for CEH
		7. `site:`
		8. `|` - we'll learn this in password cracking Topic
		9. `*`
		10. `-`
		11. `indexof:`
	- these are Google Dorks or google operators
	- in `cache:` operator : cache - means temporary files 
		- Eg 1 : whenever u open a application then a temp file will be created for that application ✔<br>Q : why temp file being created <br>Ans : so that application will get load fast <br>- like in Kali Linux , `~` sign temp file created for that PPT application <br>so either u can say that file as a temp file or cache file <br>- & if we don't save the changes which we made in the file then that temp file will not remove itself
		- Eg 2 : let's say we're on Phone & when we visit first time on a specific website ✔<br>then that website will open slowly cuz resources which are required for that website to load fast <br>those resources are not in ur System , so at first time visit - those resources (like settings , etc) will be loaded & saved <br>in ur device. So when u open 2nd time - then the website will get load fast due to those resources aka temp/cache files 
		- usecase/importance of `cache:` operator in Ethical Hacking ⭐ : <br>- if a developer made a website & he wants to do changes with time on his website again<br>then might be previous version is not saved properly or not deleted properly <br>- so cache file of that previous version of his website - can be used to know what's the changes being made <br>& if we found any vulnerabilities - then the issue can be used to catch the hacker or hack him ✔ <br>- that's why one of the usecase/importance of cache file is used
		- there is a difference b/w cookies & cache <br>- cookies takes all the system's information , system's configuration & details cuz <br>if u do any wrong activity then u'll be caught by cyber police <br>- in cookies , u'll see in upcoming lectures - session hyjacking
		- Eg 1 : in one tab - write `cache:wscubetech.com` & 2nd tab open wscubetech website
			- Pic <br><img src="../notes-pics/02-Module/12_lecture/12_lecture-3-M2.jpg" alt="" width="500"/>
			- now u can see above stuff written in cache wscubetech website
			- Practical Work : Finding the difference b/w actual website & cache website of wscubetech ✔ <br>> STEP 1 : open any text compare website like https://text-compare.com <br>> STEP 2 : view the source code of actual wscubetech website & copy the source code completely<br>& paste in on left side input field of "text-compare.com" website <br>> STEP 3 : view the source of of cache website & copy the source code completely & paste <br>on right side input field of "text-compare.com" website <br>> STEP 4 : click on "compare" button & whatever the things which are highlighted - that's the difference <br>but that  difference is not vital one <br>- & even in cache website of it - which u viewed - there's a time coming 14:56:30 GMT <br>that time is coming due to that difference
	- in `filetype:` , Eg : let's say we searched on search bar of google i.e `hacking book filetype:pdf` <br>output : we'll get only pdf file format related to hacking book , no other file format will come in search results
	- in `allintext:` & `intext:` : 
		- `intext:` : means in text form
			- it takes only single word ✔
			- Eg : search `intext:wscubetech` & anywhere in search results "wscubetech" written in text form <br>those results will be shown <br><img src="../notes-pics/02-Module/12_lecture/12_lecture-4-M2.jpg" alt="" width="500"/>
		- `allintext:` : means all in text form
			- it can take single or multiple words & if any one out of those multiple words found in search results <br>those results will be shown ✔ 
			- Eg : search `allintext:wscubetech devendra hacker` <br><img src="../notes-pics/02-Module/12_lecture/12_lecture-5-M2.jpg" alt="" width="500"/>
			- in output , hacking word also coming cuz hacker word used
	- in `allinurl:` & `inurl:`
		- `inurl:` : it takes only single word
			- Eg : `inurl:wscubetech` - so those search results will be shown whose have "wscubetech" <br>in their URL <br><img src="../notes-pics/02-Module/12_lecture/12_lecture-6-M2.jpg" alt="" width="500"/>
		- `allinurl:` : it can single or multiple words
			- Eg : `allinurl:wscubetech youtube facebook` , those results will be shown whose have <br>if any one or all these 3 words come in URL <br><img src="../notes-pics/02-Module/12_lecture/12_lecture-7-M2.jpg" alt="" width="500"/>
	-  in `intitle:` & `allintitle:`
		- `intitle:` : means showing a word in title (means the tab name (of the browser))
			- it takes only one word
			- Eg : `intitle:facebook` <br><img src="../notes-pics/02-Module/12_lecture/12_lecture-8-M2.jpg" alt="" width="500"/>
			- means we'll get only those results which contain "facebook" word as title ✔
		- `allintitle:` : means - same as `intitle:`
			- it takes one or multiple words 
			- Eg 1 : `allintitle:facebook wscubetech instagram` : means those results will be shown <br>whose have either any one or all these words inside the tab (of a browser) as title/s ✔
			- Eg 2 : `allintitle:facebook wscubetech youtube`
	- in `site:` : 
		- means Eg : `site:wscubetech.com` - only those results will be shown which are only related to wscubetech.com ,<br>no other websites links will come as outputs ✔<br><img src="../notes-pics/02-Module/12_lecture/12_lecture-9-M2.jpg" alt="" width="500"/>
	- `-` : means minus sign
		- used to remove/don't show a word/s which we don't want in search results
		- Eg 1 : `mindset books love -romance filetype:pdf` <br>Eg 2 : `mindset books -love -romance filetype:pdf`
	- `*` operator :
		- used to show all the results which are related that thing - which u defined ✔
		- Eg 1 : `wscubetech` - let's say we don't know whether wscubetech has `.com` or `.in` <br>so put `wscubetech*` - it'll show all the results which are only related to wscubetech ✔
		- usecase of it - let's say u know half word of that complete word - but u forgot half word of it <br>Eg 2 : `devendra` - but u don't know sir name of the name , so put star sign - `devendra*` <br><img src="../notes-pics/02-Module/12_lecture/12_lecture-10-M2.jpg" alt="" width="500"/>
	- `indexof:`
		- Story
			- Q : can we access files & folders from a computer of any client <br>Ans : No , any client can access their own computer not others
			- so a developer when make a website then that website contain files & folders <br>& they extract that website & kept files + folders on a server <br>Q : can we access/see files & folders of a website of a developer <br>Ans : no , cuz they are private
			- only in one case possible via which we can access/see those files & folders <br>if that server has a problem in itself & that might be `Directory/path Traversal` ✔
			- so if any server has issue of `Director Traversal` - then files & folders of that server <br>we can see clearly & sometime `Director Traversal` aka `indexof:` ✔
			- so we can't access/see files & folders of a server until we hack or has any vulnerabilities like `indexof:` ✔
			- so any website has vulnerabilities issue of `indexof:` - then we can access/see files & folders 
			- this issue is little dangerous & special way also
		- Examples 
			- Eg 1 : `indexof:facebook.com` <br>- so anything which is running via connectivity of facebook but their server has vulnerability of `Directory Traversal` ✔ <br><img src="../notes-pics/02-Module/12_lecture/12_lecture-11-M2.jpg" alt="" width="500"/> <br>- files & folders <br><img src="../notes-pics/02-Module/12_lecture/12_lecture-12-M2.jpg" alt="" width="500"/>
			- so due to `Directory Traversal` vulnerability in their server - that's why we can see files & folders
			- Eg 2 : `indexof:aiims` 
		- via this issue , we can find out more vulnerabilities in a website & can hack <br>cuz what if in those files & folders - there is imp files - then due to this a website become more vulnerable ✔

---
### Homework
1. see these Google Dorks Operators for I.G
2. so make a deep report on wscubetech for I.G 

---
### End of the Lectures (Doubts) : 
- More on : Google Dorks/Operators : <br>> https://www.youtube.com/watch?v=u_gOnwWEXiA&ab_channel=NullByte <br>> https://www.youtube.com/watch?v=lESeJ3EViCo&ab_channel=Hak5 <br>> https://www.youtube.com/watch?v=hrVa_dhD-iA&ab_channel=NetworkChuck <br>> https://www.youtube.com/watch?v=xpzvlC6WNPU&ab_channel=An0nAli <br>> https://www.youtube.com/watch?v=QLhUYxgalKI&ab_channel=CyberStudies <br>> https://www.youtube.com/watch?v=GlIG37uZSjQ&ab_channel=Afshan-AFSHackersAcademy
- Advice : clear ur doubts during lecture, cuz taking ur doubts at home is like baggage <br>if u're getting any doubt in ur mind during lecture then clear it right now <br>otherwise if u're not getting doubt during lecture then it's fine ✔
- Advice - Q : can i get the PPT via which Sir Explain <br>Ans : those PPT are not useful cuz only points are written in those PPT <br>so make ur own self-notes , so these PPT are useless & in future , u'll get many books to read