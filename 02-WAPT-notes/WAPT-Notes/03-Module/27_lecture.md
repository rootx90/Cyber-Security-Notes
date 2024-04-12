#WAPT-notes

---
### what we'll learn
> Lecture Name : [hindi] Do not miss this CRITICAL vulnerability!
> 1) Intro of the vulnerability
> 2) 

### Overview
- ATLASSIAN is a product-based company & it's some softwares are popular like Jira , Confluence <br>
    so a vulnerability found in "Confluence" software which is generated as Advisory i.e 4th October <br>
    due to this we got to know , it has "Broken Access Control" vulnerability via which any person can register as admin account <br>
    & that person can set the password
- we'll see about the vulnerability + how it's possible + in this big company , how this vulnerability founded <br>
    + we'll understand attacker's mindset 

### Reference
- https://tryhackme.com/r/room/confluence

---

### 1. Intro of the vulnerability
- On October 4th, 2023, Atlassian released a security advisory regarding CVE-2023-22515, <br>
    Q : for which vulnerability Atlassian released a security advisory ✔️ <br>
    Ans : i.e a broken access control vulnerability & it's CVSS score of 10 (which means max score - means most critical vulnerability)
- this vulnerability was introduced in version 8.0.0 of Confluence Server & Data Center editions
- it's present in versions <8.8.3, <8.4.3, <8.5.2 . According to Atlassian, the vulnerability has already been exploited in the wild.
- Advice : if a person who's using this software of around this versions <br>
    then check in ur organization + ur security teams must know about it

### 2. understanding the vulnerability
- when u run "Confluence" for the 1st time - then u need to do the initial setup (like configure some basic parameters & <br>
    create an administrative account)
    - once that initial setup done then u'll get this page <br><img src="../../notes-pics/03-Module/27_lecture/27_lecture-0-M3.jpg" alt="" width="500"/>
    - but we got the vulnerability due to which admin login page comes instead of that page (which is in pic 0) like this <br>
        <img src="../../notes-pics/03-Module/27_lecture/27_lecture-1-M3.jpg" alt="" width="500"/>
    - after just putting the URL i.e "10.10.57.42:8090" - then that vulnerability redirect u to that URL i.e login.action (which is in pic 1) <br>
        & in URL , os_destination is a parameter
- CVE-2023-22515
    - This vulnerability allows an attacker to reenable the initial setup process. <br>
        so, the attacker can go through the step of creating a new administrator all
    - this's all possible cuz Confluence is built using the Apache Struts framework (which depends on the XWork package)
    - means whenever u write "http://10.10.57.42:8090/" then it'll redirect to the "http://10.10.57.42:8090/login.action" <br>
        Q : why it doest that <br>
        Ans : cuz "action" method always gets invoked through its URL (which u wrote)
    - so this comes in working of "Apache Struts framework" - which call Getters/Setters methods
- Q : what's the problem here ✔️
    - http://10.10.57.42:8090/setup/setupadninistrator-start.action is a page - which is saying to setup the administrator's account
    - STEP 1 : in firefox -> paste the URL , output : <br><img src="../../notes-pics/03-Module/27_lecture/27_lecture-0-M3.jpg" alt="" width="500"/>
    - so generally , we need always the same output of STEP 1 , but the output is coming via using "Apache Struts framework" <br>
        so that's why , we can control Getters/Setters
    - Q : how we can control Getters/Setters ✔️<br>
        Ans : via id parameter
    - Q : as a hacker , what we'll do ✔️<br>
        Ans : we'll craft/create a URL
    - Q : how we'll craft a URL ✔️<br>
        Ans : like this http://10.10.57.42:8090/server-info.action?bootstrapStatusProvider.applicationConfig.setupComplete=false
        <br>- means 


### Practical Work 
- STEP 1 : in https://tryhackme.com/r/room/confluence -> in Task 1 intro -> click "start machine" -> copy the IP address i.e 10.10.57.42
- STEP 2 : in terminal -> run `openvpn EthicalSharmaji.ovpn`


