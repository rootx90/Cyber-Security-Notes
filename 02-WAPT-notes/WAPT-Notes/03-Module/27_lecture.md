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
- Advice : if a person who's using this software of around this versions - then check in ur organization + ur security teams must know about it

### 2. understanding the vulnerability
- when u run "Confluence" for the 1st time - then u'll go through the initial setup


### Practical Work 
- STEP 1 : in https://tryhackme.com/r/room/confluence -> in Task 1 intro -> click "start machine" -> copy the IP address i.e 10.10.57.42
- STEP 2 : in terminal -> run `openvpn EthicalSharmaji.ovpn`


