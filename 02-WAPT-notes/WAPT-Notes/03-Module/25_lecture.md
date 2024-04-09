#WAPT-notes

---
### what we'll learn
> Lecture Name : [Hindi] Cross-Site Scripting(XSS) | Deface website | Owasp Top 10
> 1) what's XSS
> 2) Types of it
> 3) XSS Payloads
> 4) Practical Work : How to deface a website via XSS

### Overview

### reference
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
1. 
2. asd

### 4. Practical Work : How to deface a website via XSS
- STEP 1 : connect to openvpn , run `openvpn EthicalSharmaji.ovpn`
- STEP 2 : in tryhackme -> Task 20 -> click "Star machine"
- STEP 3 : 
- step 4 : 
