#WAPT-notes

---
### what we'll learn
> Lecture Name : [Hindi] Cross-Site Scripting(XSS) | Deface website | Owasp Top 10
> 1) what's XSS
> 2) Types of it
> 3) XSS Payloads
> 4) Practical Work : How to deface a website via XSS

### Overview

### Reference
- Task 20 [Severity 7] | https://tryhackme.com/r/room/owasptop10

---

### 1. what's XSS
- in Cross Site Scripting (XSS) , "Scripting" word is coming - means in a webapp , anywhere "input" field is coming <br>
    where a user can write/type (means a input can come from a user)
- Eg of Input Field : searchBox , CommentBox , etc 
    - so if any input field is not validated/sanitized properly (eg : in Covid , we sanitize our body to germs , viruses , etc)
    - so same way , when a malicious JS scripts (like in alertBox input field , let's say u're writing a script to print "hacked" <br>
        & got a output "hacked" popup - like we did in Lecture 17 XSS Challenge 1) <br>
    - so when we give a input i.e a JS script - inside any "input" box & if that JS script going as it is <br>
        & no sanitization happening (means left bracket ">" , right bracket "<" of script tag - so these symbols also going as it is) <br>
        & that JS script is executing - then this attack aka XSS
    - means that input field is not properly validated/sanitize/encoded/ & no (whitelisting & blacklisting) <br>
        means nothing done to protect the input field<br>
        Q : then in this situation , what will happen ✔️<br>
        Ans : in that input field , when a user giving a input - then as it is output is coming aka XSS

### 2. Types of it
- 3 types of it 
    <br>1) Stored XSS
    <br>2) Reflected XSS
    <br>3) DOM-Based XSS
- in Stored XSS : 
    - Eg : we have a Name input field & we gave input i.e `<script>alert(1)</script>` (instead of writing ur own name) <br>
        so that JS script/payload get stored in the server
    - Now in that webapp , after login - there's a page where it shows the name of the user <br>
        so earlier , we wrote the JS payload instead of writing the name + there's no validation/sanitization in that input field <br>
        so due to this , that JS payload will be stored inside the website's database
    - so whenever that page comes (which shows the name of the user) , <br>
        so that JS payload will come (instead of showing the name of the user) & executed
    - so once this JS payload executed - then this payload will execute again & again (whenever the user - login & comes on that page)
    - so this attack is vv dangerous
- in Reflected XSS : 
    - Eg : a searchBox input , so whenever u search something - then u'll get results related to that searched stuff
    - Now u're a attacker , so u'll put a JS payload on that search input field - let's say `<script>alert(1)</script>` <br>
        Q : Now in this is situation , what'll happen ✔️<br>
        Ans : if that "search input field" is not sanitize properly + no protection mechanism , due to this , that JS payload will be executed
- in DOM-Based XSS : 
    - Eg : at home , we have a water sink , so we open the tap-water & water goes directly inside sink <br>
        so tap-water is a source (means from where water is running) & sink is a sink (means where water is going) ✔️
    - these 2 stuff sometimes vulnerable (like eval() function in js , <br>
        document.location is not sanitize - due to this as it is any input can be given) - due to this , <br>
        that stuff becomes attacker controlled - means whenever we (as a attacker) send a payload to the sink - then it could be XSS
    - Q : why we say this attack as DOM-based ✔️<br>
        Ans : cuz it's Document Object Model - means it's a representation of HTML elements of HTML page <br>
        means HTML page is like tree-structure (eg : 1st root i.e html tag & so on..) <br>
        so a attacker manipulate that structure aka DOM-based XSS

### 3. XSS Payloads
- some common payloads based on types of XSS
1. Popup's (`<script>alert(“Hello World”)</script>`) - Creates a Hello World message popup on a users browser.
2. Writing HTML (`document.write`) - Override the website's HTML to add ur own (essentially defacing the entire page).
3. XSS Keylogger (http://www.xss-payloads.com/payloads/scripts/simplekeylogger.js.html)
   - u can log all keystrokes of a user, capturing their password & other sensitive information they type into the webpage.
   - Q : via XSS , u can make keylogger ✔️<br>
        Ans : if that input field is not sanitize properly & no protection mechanism - then we can use "simplekeylogger.js.html" payload <br>
        due to this payload , we can log all keystrokes of a user
    - log : means what are they keys clicked by a user
4. Port scanning (http://www.xss-payloads.com/payloads/scripts/portscanapi.js.html) 
    - A mini local port scanner (more information on this is covered in the TryHackMe XSS room).
    - on this link , we'll get port scanner
- Extra Resource : http://www.xss-payloads.com/ - is a best websites that has XSS related payloads ✔️

### 4. Practical Work : How to deface a website via XSS
- STEP 1 : connect to openvpn , run `openvpn EthicalSharmaji.ovpn`
- STEP 2 : in tryhackme -> Task 20 -> click "Star machine" -> copy the IP-address i.e 10.10.97.236
- STEP 3 : in firefox -> paste & open the IP-address , output : login page & Register page <br>
    <img src="../../notes-pics/03-Module/25_lecture/25_lecture-0-M3.jpg" alt="" width="500"/>
- STEP 4 : click "Reflected XSS" menu , we'll get 2 Ques
    - Ques 
        <br>1) Craft a reflected XSS payload that will cause a popup saying "Hello"
        <br>2) Craft a reflected XSS payload that will cause a popup with your machines IP address
    - STEP 4.0 : in search bar -> write xyz , output : we'll get `xyz` as it is
    - STEP 4.1 : in search bar -> write batman , output : u'll get `batman` as it is
    - so in search input bar , no validation implemented cuz we're getting results as same as we searched <br>
        so to test whether there's validation applied or not - we'll make a JS payload
    - STEP 4.2 : finding answer of 1st ques of Reflected XSS
        - STEP 4.2.0 : in search bar -> write `<script>alert("Hello")</script>` -> hit enter <br>
            output : alert popup shown with "Hello" message
        - STEP 4.2.1 : in popup -> click ok , output : ThereIsMoreToXssThanYouThink - answer of 1st ques of Reflected XSS
        - STEP 4.2.2 : in tryhackme -> paste `ThereIsMoreToXssThanYouThink` answer in 2nd ques
    - STEP 4.3 : finding answer of 2nd ques of Reflected XSS
        - 2nd ques of Reflected XSS - means show the name of the IP-Address in alert popup
        - STEP 4.3.0 : in search bar -> write `<script>alert(window.location.hostname)</script>` -> click "search" btn or hit enter <br>
            output : IP-address i.e 10.10.97.236 in alert popup
        - STEP 4.3.1 : in alert popup -> click ok , output : ReflectiveXss4TheWin - answer of 2nd ques of Reflected XSS
    - STEP 4.4 : click "Why does this work?" toggle <br>
        Ans : in reflected Xss ur payload - once u giving ur input as same we're getting output & no sanitization/encoding happening
        <br>- `<h6>You Searched for: [Your input will be input directly in here]</h6>` : means whatever u give input <br>
            that input will come as it is as a output
    - STEP 4.5 : click "Disable your browsers XSS protection" toggle <br>
        Ans : some browsers have in-built XSS protection
        <br>- if these XSS payloads are not working in ur browser , then u can disable the XSS protection from that browser
- STEP 5 : click "Stored XSS" menu , we'll get 3 Ques
    - Ques
        <br>1) Add a comment