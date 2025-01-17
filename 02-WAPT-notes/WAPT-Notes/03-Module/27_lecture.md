#WAPT-notes

---
### what we'll learn
> Lecture Name : [hindi] Do not miss this CRITICAL vulnerability!
> 1) Intro of the vulnerability
> 2) understanding the vulnerability
> 3) Practical Work : "Broken Access Control" vulnerability
> 4) Automating Exploitation
> 5) Detection & Patching

### Overview
- ATLASSIAN is a product-based company & it's some softwares are popular like Jira , Confluence <br>
    so a vulnerability found in "Confluence" software which is generated as Advisory i.e 4th October <br>
    due to this we got to know , it has "Broken Access Control" vulnerability via which any person can register as admin account <br>
    & that person can set the password
- we'll see about the vulnerability + how it's possible + in this big company , how this vulnerability founded <br>
    + we'll understand attacker's mindset 

### Reference
- https://tryhackme.com/r/room/confluence
    - Task 1 Intro
    - Task 2 Understanding the Vulnerability
    - Task 3 Automating Exploitation
    - Task 4 Detection and Patching
    - Task 5 Conclusion

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
        - means Q : what action we need ✔️<br>
            Ans : we need action from the server
        - bootstrapStatusProvider.applicationConfig.setupComplete : means the variable which set as true <br>
            due to which we're able to find whether that account already setup/created or not - we set it as false
        - means like "Apache Struts framework" redirect to login.action same way actions get called <br>
            Eg : the moment u called this page i.e http://10.10.57.42:8090/setup/setupadministrator-start.action <br>
            then it checks whether this account already setup or not , so this account already setup that's why <br>
            we got the page i.e "your Confluence instance is already completely setup"
        - Q : how it's able to check whether the account is already setup or not ✔️<br>
            Ans : cuz earlier it was set as true i.e server-info.action?bootstrapStatusProvider.applicationConfig.setupComplete=true
        - now understand the attacker's mindset
            <br>- attacker tries to understand the logic like "1stly the attacker understand how logic is running"
            <br>Q : how the attacker able to know whether the admin account is setup or not ✔️<br>
                Ans : so the attacker set it as false - then the attacker start watching "what's gonna happen"
        - so if u're able to understand the attacker's mindset then u can become the better

### 3. Practical Work : "Broken Access Control" vulnerability
- STEP 1 : in https://tryhackme.com/r/room/confluence -> in Task 1 intro -> click "start machine" -> copy the IP address i.e 10.10.57.42
- STEP 2 : in terminal -> run `openvpn EthicalSharmaji.ovpn`
- STEP 3 : in firefox -> in new tab -> paste the URL of admin account & set it as false i.e <br>
    http://10.10.57.42:8090/server-info.action?bootstrapStatusProvider.applicationConfig.setupComplete=false , <br>
    output : Success page - which means it's set as false
- STEP 4 : in firefox -> in new tab -> paste the URL of admin account i.e http://10.10.57.42:8090/setup/setupadministrator-start.action <br>
    output : got the Configure account of system administrator <br>
    Q : why we got page of Configure system admin account ✔️<br>
    Ans : cuz it was set as false that's why we (as a attacker) can create a "system admin account" again
    - i.e aka Broken Access Control
    - Q : why it's considered as Broken Access Control ✔️ <br>
        Ans : cuz they already setup the Access Control , How ✔️ <br>
        Ans : just setting as true i.e bootstrapStatusProvider.applicationConfig.setupComplete=true <br>
        but any user can set it as false - which means it's broken , so it's not working properly
- STEP 5 : fill the form completely -> click Next , output : <br><img src="../../notes-pics/03-Module/27_lecture/27_lecture-2-M3.jpg" alt="" width="500"/>
    - STEP 5.1 : click start , <br>
        output : got the URL as `http://10.10.57.42:8090/dashboard.action#all-updates` 
        <br>- so it's showing dashboard.action & admin acc. is created
        <br>- now we're a part of admin & we can also see posts <br>
        <br>- got the flag i.e THM(who_needs_keys_anyway)
- Ques
    - Q 1 : Log into Confluence with ur new credentials. What is the value of the flag posted by admin? <br>
        Ans : THM(who_needs_keys_anyway)

### 4. Automating Exploitation
- Q : can we automate those above steps of Practical Work
- there's a script to make the process automate i.e Chocapikk i.e https://github.com/Chocapikk/CVE-2023-22515
- STEP 0 : in terminal -> run `sudo su`
- STEP 1 : go to https://github.com/Chocapikk/CVE-2023-22515 -> open exploit.py , <br>
    output : after trigging this vulnerability , username & password are set
- STEP 2 : copy https://github.com/Chocapikk/CVE-2023-22515 -> in terminal , <br>
    run `git clone https://github.com/Chocapikk/CVE-2023-22515` -> hit enter
- STEP 3 : run `cd CVE-2023-22515`
- STEP 4 : in firefox -> go to https://github.com/Chocapikk/CVE-2023-22515 to check how to run this vulnerability
    - STEP 4.1 : copy `pip install -r requirements.txt` -> in terminal , paste it -> hit enter
    - STEP 4.2 : go to that github URL -> usage section -> in Normal Mode -> in terminal , write `python3 exploit.py normal` <br>
        Q : what's Normal mode ✔️<br>
        Ans : go to that URL github , u'll find i.e in normal mode , u can exploit the Confluence vulnerability <br>
        using a single target URL <br>
        Q : why we're using Normal Mode <br>
        Ans : so currently , we want to exploit only one target URL , not multiple that's why we're using Normal mode <br>
        Q : what's the target URL <br>
        Ans : go to https://tryhackme.com/r/room/confluence -> open Task 2 , output : u'll see "http://10.10.57.42:8090"
    - STEP 4.3 : copy the targeted URL -> paste in STEP 4.2 command i.e `python3 exploit.py normal http://10.10.57.42:8090/`
    - STEP 4.4 : go to that github URL -> usage section -> in Normal Mode -> check syntax i.e "--output-file=[OUTPUT_FILE]" <br>
        so in terminal -> write `python3 exploit.py normal http://10.10.57.42:8090/ --output-file=out.txt` , <br>
        output : got the Username & Password <br>
        <img src="../../notes-pics/03-Module/27_lecture/27_lecture-3-M3.jpg" alt="" width="500"/>
- STEP 5 : go to Confluence account -> click profileIcon -> click Logout -> , output : got the Login Page
    - STEP 5.1 : write username "pleasepatch" & password "Password2" -> click login , output : we're able to login as admin
    - conclusion : it automate the process 
- Ques 
    - Q 1 : Read Chocapikk's script. What is the name of the Confluence user it creates? <br>
        Ans : pleasepatch

### 5. Detection & Patching
- how to detect & patch it
- 1st way : Detection 
    - if u're using a vulnerable version of confluence , be sure - u can check these things 
        1) check Network access logs `/setup/*.action` : means is there any thing in `*.action` <br>
            (like whether a normal user able to access or not - cuz that login admin page must be only for a admin user)
        2) Network access logs `server-info.action?bootstrapStatusProvider.applicationConfig.setupComplete=false` <br>
            which this URL is reachable/accessible by normal user or not <br>
            if it's reachable - then make it unreachable
        3) review ur Confluence users & look for suspicious (accounts & members) in the `confluence-administrators` group <br>
- 2nd way : Patching
    - Q : how to patch it <br>
        Ans : update the software to that version which there's no vulnerability of it
- 3rd way : if u can't upgrade - then disallow/blocked (as a temporary measure) this directory `/setup/*`
    - means restrict the users from accessing `/setup/*`
    - means if no user able to go to that path - then he/she can't set it as false
    - STEP 1 : for the code , go to https://tryhackme.com/r/room/confluence -> go to "Task 3 Automation Exploitation"
- Ques 
    - Q 1 : Is Confluence Server version 8.2.0 vulnerable to CVE-2023-22515? (yea/nay) <br>
        Ans : yea
    - Q 2 : Does applying mitigation actions replace the need to upgrade Confluence? (yea/nay) <br>
        Ans : nay

### 6. Conclusion
- check Task 5 of https://tryhackme.com/r/room/confluence