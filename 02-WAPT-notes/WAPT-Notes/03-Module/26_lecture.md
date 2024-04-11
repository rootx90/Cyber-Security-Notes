#WAPT-notes

---
### what we'll learn
> Lecture Name : [Hindi] Insecure Deserialization | Practical Demo | RCE | Owasp Top 10
> 1) what's Insecure Deserialization
> 2) reasons why this vulnerability comes 8 out of 10 in OWASP
> 3) what's Vulnerable
> 4) Ques
> 5) what's Objects
> 6) Ques
> 7) what's De(Serialization)
> 8) Ques
> 9) Cookies
> 10) Ques
> 11) Cookies Practical
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

### 5. What's Objects
- in Programming , in OOP , Objects are made of 2 things 
    <br>1) State
    <br>2) Behaviour
- Eg : a lamp is a object.
    <br>Lamps can have of different types of bulbs = their state
    <br>either their're ON/OFF = their behaviour

### 6. Ques
- Q 1 : if a dog was sleeping , would this be :
    <br>A) A state
    <br>B) A Behaviour
    <br>Ans : A Behaviour
    - Conclusion : 
        <br>- types of dogs = state
        <br>- actions = Behaviour

### 7. what's De(Serialization)
- Eg of Serialization vs De(Serialization) :
    - A Tourist approaches you & he's street asking for street directions cuz he got lost & he's looking for a local landmark & <br>
        he didn't understand English + nor u can't understand his language (let's say Spanish) <br>
        Q : what do u do ? <br>
        Ans : u'll draw a map of the route to the landmark (i.e he wants to go) cuz Pictures cross language barriers <br>
        then he'll be able to find the landmark <br>
    - Q : from this situation , what did u understood ? <br>
        Ans : when u serialized some info 
        - means u don't understand his language + he don't know ur language <br>
            so u converted the language from one form to another to make him understand <br>
            via gestures + pictures (cuz it's also another form of language)
        - then that tourist try to understand the drawing (i.e made by u) reach the landmark - means <br>
            he did De(Serialization) it to find the landmarks
- Serialization : is the process of converting objects into simpler & compatible formatting (like JSON , etc)
- Eg of Serialization vs De(Serialization) :
    - pic :<br><img src="../../notes-pics/03-Module/26_lecture/26_lecture-0-M3.jpg" alt="" width="500"/>
    - password is password123 (which going to be store in a database) <br>
        so travel across a network this string/output needs to be converted to binary notation
    - once the password reaches to the database <br>
        then the password is converted/deserialized back into "password123" - so it can be stored
- Q : how can we leverage this ? OR how we can take advantage of it ✔️
    - Ans : insecure deserialization happens when data comes/taken from an untrusted party (i.e a hacker) then we execute it
    - Eg : u have a data & u converted into base64 (cuz assume that data accept Base64 only) <br>
        then hacker got to know that (we're using Base64 & whatever data in Base64 will get execute) <br>
        Q : what hacker will do <br>
        Ans : the hacker will put a payload during the process & when the app do deserialize - then the hacker will get Shell
    - we'll see in Practical

### 8. Ques
- Q 1 : What is the name of the base-2 formatting that data is sent across a network as ? <br>
    Ans : binary <br>
    Q : base-2 means <br>
    Ans : here 2 means binary = 0 or 1

### 9. Cookies
- purpose of Cookies in browser : 
    - used to maintain the state of sessionID
    - Tiny pieces of data, these are created by a website and stored on the user's computer.
    - Eg : if u're login again & again in a webapp - then cookies maintain the login state until u don't logout
- Cookies additional attributes/Flags
    - Pic : <br><img src="../../notes-pics/03-Module/26_lecture/26_lecture-1-M3.jpg" alt="" width="500"/>
    - "Cookie Name" & "Cookie Value" is a imp attribute which is required in Cookie
    - Q : purpose of "Secure Only" attribute ✔️ <br>
        Ans : it'll set only for HTTPS connections - otherwise it'll not set for other protocols (like HTTP , etc)
    - Q : define "Expiry" attribute ✔️<br>
        Ans : it tells when (means time) the cookie will be removed from the browser
    - Q: purpose of "Path" attribute ✔️<br>
        Ans : the cookie will only be sent to the server - if when the specified URL is mentioned
- Cookies can be set via different website programming lang

### 10. Ques
- Q 1 : If a cookie had the path of webapp.com/login , what would the URL that the user has to visit be? <br>
    Ans : webapp.com/login
    - u have to set the same URL - only then cookie will be sent
- Q 2 : What is the acronym for the web technology that Secure cookies work over? <br>
    Ans : https

### 11. Cookies Practical
- STEP 1 : connect to openvpn , run `openvpn EthicalSharmaji.ovpn`
- STEP 2 : in tryhackme -> Task 21 module -> click "Star machine" -> copy the IP-address i.e 10.10.60.47
- STEP 3 : in tryhackme -> Task 25 module , output : we already connected to the VPN
- STEP 4 : in tryhackme -> in Task 25 module
    - Q 1) 1st Flag (cookie value) ✔️
        - means we need to find out 1st flag & to find it out - we need to do changes in "userType"
        - STEP 4.1 : in firefox -> open 10.10.60.47 -> click "Exchange today" , output : SignUp will get open
        - STEP 4.2 : write username & password as "test" -> click "don't save" , output : <br>
            <img src="../../notes-pics/03-Module/26_lecture/26_lecture-2-M3.jpg" alt="" width="500"/>
        - STEP 4.3 : in this webapp -> open inspect tool -> storage tab -> Cookies section -> select the URL

### 2. Practical Work : how to do remote code execution & take shell via Insecure Deserialization


---
### End of the Lecture (Doubts)
- Advice for learning : Learning is the best done through analogies ✔️

