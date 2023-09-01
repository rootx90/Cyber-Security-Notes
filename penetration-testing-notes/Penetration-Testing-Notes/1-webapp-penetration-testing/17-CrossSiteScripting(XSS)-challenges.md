#WAPT #penetration-testing
### Overview
- most imp topic ⭐
- we'll over XSS - reflected type & 8 challenges of XSS
- XSS reflected - generally , u can exploit this vulnerability in bug bounty but if u're doing WAPT then u have to focus on XSS especially `XSS reflected` cuz this vulnerability comes in OWASP TOP 10 but this vulnerability is easy to exploit & still many applications have this vulnerability ✔
### what we'll learn
- how to exploit this vulnerability
- if some part is already sanitized or if they put encoding on their application to secure it , so how to break/crack it ✔
###  Others 
- in bug bounty , people earn good amount of money for doing this XSS & finding these sort of issues 
- websites where buy bounty done : [HackerOne](https://www.hackerone.com/) & [bugcrowd](https://www.bugcrowd.com/) ✔
- Bug Bounty are those people who don't want to work in offices but it's like freelancing

---
### Topics - Explanation

- link for XSS challenges : http://leettime.net/xsslab1/chalg1.php# (but it's not opening)

1) <u>XSS Challenge 1</u>
	- website looks like ![[WAPT-lecture-17-0.jpg]]
	- *usecase of XSS reflected / where we can use it* ✔
		- 1) it can be applied on a input field
		- 2) it can be applied on any parameter of a URL
	- STEP 1: this input field is for searching , so let's search anything to know search input field is working or not like `ironman` & click on search , u'll get this ![[WAPT-lecture-17-1.jpg]]
	- now u can see that the way we wrote the `ironman` , this webapp shows same thing
	- so first thing to remember that is input reflecting as a output or not ✔
	- STEP 2: to check more clearly , then do inspect , so right click & click "view source"
		- Note : we're testing in internet explorer cuz chrome , firefox , edge , etc browsers don't allow to run XSS ✔
		- check out the tag of that output like this ![[WAPT-lecture-17-2.jpg]]
		- so we're getting `ironman` word as it is the way we wrote in search input field
	- STEP 3: to exploit , in "search input field" write the payload `<script>alert(1)</script>`  & click on search , u'll get this ![[WAPT-lecture-17-3.jpg]]
	- so we got the `1` which means we did XSS & we'll get a alert message "Nice Try..... But use alert(document.URL) to pass this challenge!!" - so it's giving us a hint that we try well but when we do `document.URL` then we can pass the challenge ✔
	- so click ok
	- STEP 4: in search input field , write this payload `<script>alert(document.URL)</script>` & click on search , u'll get alert message box "Good Work!! You are welcome to next round" & click ok ✔
2) <u>XSS Challenge 2</u>
	- STEP 1: write again `ironman` inside the search input field & click search
		- Now check whether any encoding or sanitize ✔
		- so it's showing `cannot find your query` & now `ironman` word coming inside `value` attribute of text `input` field ![[WAPT-lecture-17-4.jpg]]
		- `ironman` word is getting close via `close angle bracket` 
		- STEP 1.1: now put that previous payload i.e `<script>alert(alert.(document.URL)</script>` just to check it's working or not & click on search
		- so it's not working cuz that complete payload stored inside `value` attribute `text input field` like this ![[WAPT-lecture-17-5.jpg]]
		- & we're getting extra `close angle bracket` at the end
	- `v imp Note ⭐` : in XSS , the rule is here `<script>alert(alert.(document.URL)</script>>` - we need to "balance" i.e whatever thing is ending with like here extra `close angle bracket` , put that thing at the starting also like this `><script>alert(alert.(document.URL)</script>>` but we're getting `close angle bracket`  at the end so remove it cuz it's automatically comes ✅
	- STEP 2: so payload will be `><script>alert(alert.(document.URL)</script>`
		- so paste it & click on search , u'll come to next round
3) <u>XSS Challenge 3</u>
	- STEP 1: write again `ironman` inside the search input field & click search
		- so it's showing `cannot find your query` & now `ironman` word coming inside double quotes (in `value` attribute of text `input` field) with closing angle bracket ![[WAPT-lecture-17-6.jpg]]
		- for checking purpose , put that same challenge 1 - payload to check which thing get sanitize & what's the input coming 
		- STEP 1.1: `<script>alert(alert.(document.URL)</script>` put it & click on search, so we'll get the payload as it is inside double quotes ![[WAPT-lecture-17-7.jpg]]
	- so we need to balance the thing 
	- STEP 2: so payload will be `"><script>alert(alert.(document.URL)</script>">` but at the end , we're getting 2 things extra i.e the ending double quotes & `close angle bracket` extra , so remove them cuz those will come automatically at the end, so ultimately `"><script>alert(alert.(document.URL)</script>` ✔
	- STEP 3: put this payload & click on search
4) <u>XSS Challenge 4</u>
	- STEP 1: write again `ironman` inside the search input field & click search
		- so it's showing `cannot find your query` & now `ironman` word coming inside single quotes (in `value` attribute of text `input` field) with closing angle bracket
		- STEP 1.1: so for testing purpose in order to know what's happening behind the scene, use that base line payload of Challenge 1 i.e `<script>alert(alert.(document.URL)</script>` & click on search ✔
		- we're getting output inside value attribute with single quotes & a close angle bracket
	- so to balance the payload , remove the 2 things from the end i.e single quote & close angle bracket
	- STEP 2: so payload will be `'><script>alert(alert.(document.URL)</script>`
5) <u>XSS Challenge 5</u>
	- STEP 1: write again `ironman` inside the search input field & click search
		- so it's showing `cannot find your query` & now `ironman` word coming inside double quotes of a variable i.e ![[WAPT-lecture-17-8.jpg]]
		- STEP 1.1: so in order to understand & testing purpose , we'll use that base line payload of Challenge 1 i.e `<script>alert(alert.(document.URL)</script>` & click on search ✔
		- we're getting the payload inside double quotes , semi colon & script tag
	- so to balance the payload , here at the end , 3 things extra we're getting i.e a double quote , semi colon & script tag ![[WAPT-lecture-17-9.jpg]]
	- STEP 2: so payload will be `";</script><script>alert(alert.(document.URL)</script>`
6) <u>XSS Challenge 6</u>
	- STEP 1: write again `ironman` inside the search input field & click search
		- so it's showing `cannot find your query` & now `ironman` word coming inside single quotes of a variable same as Challenge 5
		- STEP 1.1: in order to make sure , we'll check via our base line payload i.e `<script>alert(alert.(document.URL)</script>` , so put it inside the input field & click on search , we'll get same output as in Challenge 5 but in single quotes
	- STEP 2: so ultimately payload is `';</script><script>alert(document.URL)</script>` & remove these 3 things from the end i.e `';</script>`
	- STEP 3: paste the payload & click on search
7) <u>XSS Challenge 7</u>
	- STEP 1: write again `ironman` inside the search input field & click search
		- so it's showing `cannot find your query` & now `ironman` word coming inside single quotes value of `value` attribute of input field
		- STEP 1.1: in order to make sure , we'll check via our base line payload i.e `<script>alert(alert.(document.URL)</script>` , so put it inside the input field & click on search , we'll get the payload inside single quotes like this ![[WAPT-lecture-17-10.jpg]]
		- here to balance the payload , we're getting 2 things extra at the end i.e a single quote is coming before a closing angle bracket of the ending script tag & a close angle bracket of a starting `script` tag is missing✔
		- so here sanitized done like this ![[WAPT-lecture-17-11.jpg]]
		- STEP 1.2: for a 2nd test , let's put the double closing arrow bracket like this `<script>>alert(document.URL)</script>`  inside the input field cuz it might remove 1st one but 2nd one will remain as it is , cuz mostly happens & click on search , so we'll get this output ![[WAPT-lecture-17-12.jpg]]
		- so it remove 2 of them closing angle brackets
	- so in these cases , close angle bracket is sanitized (means escaping - means even if u give the parameter i.e close angle bracket , it's escaping - means it won't take it) aka character escaping ✔
	- STEP 2: so we can try payloads which doesn't require close-angle-bracket/greater-than-symbol i.e `onmouseover=alert(document.URL)` & click on search ✔
		- so output : `'onmouseover=alert(document.URL)'>`
		- remove those 2 extra things coming at the end i.e a single quote & close angle bracket ✔
	- STEP 3: so the payload is `'>onmouseover=alert(document.URL)` goes inside input field & click on search , output ![[WAPT-lecture-17-13.jpg]]
		- here before `onmouseover` , it took a string , the payload is not closed cuz we're getting in red & if we want to balance the payload then we need to put a single quote before `alert` word ✔
	- STEP 4: ultimately the payload is `'>onmouseover='alert(document.URL)` & click on search button , now hover on the search button & challenge is completed
	- `Tip💡` : that's why we're running base line payload to check what's happening ✔
8) <u>XSS Challenge 8</u>
	- STEP 1: write again `ironman` inside the search input field & click search
		- so it's showing `cannot find your query` & now `ironman` word coming inside single quotes value of `value` attribute of input field
		- STEP 1.1: in order to make sure , we'll check via our base line payload i.e `<script>alert(alert.(document.URL)</script>` , so put it inside the input field & click on search , output is ![[WAPT-lecture-17-14.jpg]]
		- so here greater-&-less-than-symbols is shown as HTML entities , so here encoding used , so in this cases where these kind of encoding happens then use `onmouseover` payload cuz this payload doesn't contain greater-&-less-than-symbols ✔
	- STEP 2: so `onmouseover=alert(document.URL)` & click on search , so output we'll get ![[WAPT-lecture-17-15.jpg]]
		- STEP 2.1: so to balance the payload , we need to use same trick i.e put the greater-than-symbol after the starting single quote & a single quote before the `alert` like this `'>onmouseover='alert(document.URL)` , & if you do mouse hover on `search` button then nothing happens . so output ![[WAPT-lecture-17-16.jpg]]
		- so the way we're doing XSS , that way is not possible
		- so we have 2nd way also to do XSS
	- STEP 3: 2nd way to do XSS
		- STEP 3.1: on URL address bar , u'll see `submit=search` & search button also has search text , so on address bar , remove `search` word & write `ironman` & press enter , u'll get `ironman` text on the search button also like this ![[WAPT-lecture-17-17.jpg]]
		- which means that's reflecting means , whatever you write on that address bar , it'll reflect on the `search` button also
		- STEP 3.2: `ironman` word of button is coming inside `value` attribute with double quotes i.e ![[WAPT-lecture-17-18.jpg]]
		- so payload will be `ironman"onmouseover="alert(document.URL)` , to balance the payload , we put a double quote before `alert` & we want `ironman` as a text on button , so behind the scene that payload will look like `<input type="submit" name="submit" value="ironman" onmouseover="alert(document.URL)">` ✔
	- STEP 4: so paste this payload on URL address bar after `submit=` i.e `ironman"onmouseover="alert(document.URL)` & hit enter & now we'll get a pop i.e "Internet Explorer has modified this page to help prevent XSS" cuz 
		- we're before this way , we're trying all the things inside input field , so at that time , the browser was not preventing ✔
		- but the moment , we run a query on `submit=` (aka submit parameter) URL address bar & it gets executed but the browser prevented that ✔
	- so challenge is completed but the browser is stopping
### summary / Payloads of challenges
- Challenge 1 : `<script>alert(alert.(document.URL)</script>`
- Challenge 2 : `><script>alert(alert.(document.URL)</script>`
- Challenge 3 : `"><script>alert(alert.(document.URL)</script>`
- Challenge 4 : `'><script>alert(alert.(document.URL)</script>`
- Challenge 5 : `";</script><script>alert(alert.(document.URL)</script>`
- Challenge 6 : `';</script><script>alert(document.URL)</script>`
- Challenge 7 : `'>onmouseover='alert(document.URL)`
- Challenge 8 : on browser URL address bar , apply the payload after "submit" parameter i.e `ironman"onmouseover="alert(document.URL)` 
