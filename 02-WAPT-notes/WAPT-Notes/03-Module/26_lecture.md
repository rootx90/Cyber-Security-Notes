#WAPT-notes

---
### what we'll learn
> Lecture Name : [Hindi] Insecure Deserialization | Practical Demo | RCE | Owasp Top 10
> 1) what's Insecure Deserialization
> 2) reasons why this vulnerability comes 8 out of 10 in OWASP
> 3) what's Vulnerable
> 4) Ques
> 5) Objects
> 6) 
> Practical Work : how to do remote code execution & take shell via Insecure Deserialization

### Overview

### Reference
- https://tryhackme.com/r/room/owasptop10
    - Task 21 [Severity 8] Insecure Deserialization 
    - Task 22 [Severity 8] Insecure Deserialization - Objects
    - Task 23 [Severity 8] Insecure Deserialization - Deserialization
    - Task 24 [Severity 8] Insecure Deserialization - Cookies
    - Task 25 [Severity 8] Insecure Deserialization - Cookies Practical
    - Task 26 [Severity 8] Insecure Deserialization - Code Execution

---

### 1. what's Insecure Deserialization
- Serialization vs Deserialization
    - reference to understand Serialization vs Deserialization : <br>
        https://cheatsheetseries.owasp.org/cheatsheets/Deserialization_Cheat_Sheet.html
    - Advice : we need to understand "Serialization" in order to understand "Deserialization"
    - Serialization vs Deserialization ✔️
        <br>- is a process where converting any object into a data format , so that data can be restored later
        <br>- Eg : let's say a particular object & u're converting that object into XML format <br>
            & Deserialization means converting that XML data format into that same object form
    - Conclusion : Serialization vs Deserialization
        - Serialization : means a process where converting any object into a particular data format (like XML or JSON)
        - Deserialization : means a process where converting that data format into original object form
- Q : when Deserialization becomes Insecure ✔️
    - Ans : when converting/going from one data form (like JSON) to object <br>
        so if u're validating this process via insecure way aka insecure Deserialization
    - when we're doing Deserialization - so during the process of Deserialization , when the data process (of an app) happen <br>
        then if a attacker replace that data via malicious code - then the attacker can do any attacks (like DoS , RCE , gain a shell etc)

### 2. reasons why this vulnerability comes 8 out of 10 in OWASP
- Q : reasons why this vulnerability comes 8 out of 10 in OWASP
    <br>Ans : 
    <br>1) Low Exploitability : cuz for This vulnerability , there is no reliable tool/framework for it. <br>
        cuz of its nature, attackers need to have a good understanding of the inner-workings of the ToE.
    <br>2) The exploit is only as dangerous as the attacker's skill permits + it's impact of Severity is more

### 3. what's Vulnerable
- ultimately, any app that stores or fetches data where there are no validations/integrity-checks in place for the data queried or retained.
- A few examples of applications of this nature are:
    <br>1) E-Commerce Sites
    <br>2) Forums
    <br>3) API's
    <br>4) Application Runtimes (Tomcat, Jenkins, Jboss, etc)

### 4. Ques
- Q 1 : Who developed the Tomcat application? <br>
    Ans : The Apache Software Foundation
- Q 2 : What type of attack that crashes services can be performed with insecure deserialization? <br>
    Ans : Denial of Service <br>
    - "service crash" : means those services won't be available after they got crashes

### 5. Objects
- in Programming , in OOP , Objects are made of 2 things 
    <br>1) State
    <br>2) Behaviour
- Eg : a lamp is a object. 

### 2.Practical Work : how to do remote code execution & take shell via Insecure Deserialization


