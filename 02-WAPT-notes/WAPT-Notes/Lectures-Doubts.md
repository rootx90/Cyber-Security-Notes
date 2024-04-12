#WAPT-notes 

## Apart from Lectures
1. How do u remember/retain & process of thinking <br>
    what's ur mindset whenever u learn new things & u can't able to remember
2. sir do u listen to music while learning a new concept or implement a new concept <br>
    tell reason in both cases i.e Yes or No
3. why sir u used different kali OS like in CSRF attack , u used parrot OS 
4. in Tech news , people say data breach happened of this company - what does exactly mean "data breach"

### life lessons
1. if someone say bad things about u + this goes on & on in ur mind then
    Q : how do u handle it like emotionally someone damage u - cuz i am very sensitive person
2. someone poke u again & again 

## related to Course / Email Stuff
- Q : in WAPT playlist , Hacking playlist not working <br>
    https://www.youtube.com/watch?v=RSyMIy2-iUc&list=PLHOJoqBk02jQWQ7UMwRkAoznEzRtKI1zk&index=2&ab_channel=EthicalSharmaji

```
Q : couldn't able to open this room because this room is private
    Even i open the BurpSuite room in tryhackme , BurpSuite Room section is divided into individual rooms based on topics 
    & only starting first 2 rooms are free & rest are paid to do, This is the issue i am facing 

    in tryhackme , i found these room for web fundamentals
    1. https://tryhackme.com/room/howwebsiteswork
    2. https://tryhackme.com/room/httpindetail
    3. https://tryhackme.com/room/dnsindetail
    4. https://tryhackme.com/room/puttingitalltogether
    Note : the room for webfundamentals which u showed is not same as i found in tryhackme even after searching on search bar

    rooms for BurpSuite
    5. https://tryhackme.com/r/room/burpsuitebasics
    6. https://tryhackme.com/r/room/burpsuiterepeater
    Note : further rooms for BurpSuite are paid 

    Current Status About Me : i started ur WAPT playlist & i am thinking to do those stuff 
        what i can do until i don't get reply from me , so waiting for reply 

    So like should I spend money on these or not or should i go for alternatives
Ans : u can buy tryhackme subscription for 1 month and do these paid rooms.It will be worth it.
    
    Q : Ok sir but in tryhackme , there are 2 different rooms for web fundamentals
       1. https://tryhackme.com/path/outline/web (i think this is a complete course of WAPT according to ur WAPT lectures)
       2. https://tryhackme.com/r/room/webfundamentals (this is a individual module)

       Which one should I buy for 1month subscription? Let me know.
    Ans : monthly subscription of tryhackme will give u the access to all the paid rooms.So, u can access anyone.
```
```
Q : Sir currently i am at this lecture XSS Challenges that's 
    https://www.youtube.com/watch?v=SVVSSBEU4OI&list=PLHOJoqBk02jQWQ7UMwRkAoznEzRtKI1zk&index=20&ab_channel=EthicalSharmaji

    i actually go through the lecture but the website is not working that is 
    http://leettime.net/xsslab1/chalg1.php#

    so i need to your suggestions 
    Q 1) is there any alternative of it in order to practice the XSS
    Q 2) or should i skip the practice part (because that practice website not working) & just go through the lecture

    What should I do? let me know

Ans : 
```

## Lectures Doubts

- Lecture 1
```
1) Q : what's Penetration Testing
    Q : directory Traversal vulnerability happens due to misconfiguration of the website's web-server
        or due to misconfiguration of firewall ?

general doubts
    Q : why we need OWASP or what if i don't follow OWASP OR importance of it
```
- Lecture 3 : 
```
1) Finding the server
2) Loading some content
    Q : diff. b/w server vs web server 
    Ans : https://www.perplexity.ai/search/difference-between-server-vM7DAFvPRterYLukvuiCGw
        - Server: 
            Imagine a server like a big box that stores and shares information. 
            It's like a giant library that keeps books safe and lets people borrow them when needed.
        - Web Server:
            Now, think of a web server as a special type of server that focuses on websites.
            It's like a library that specifically holds books about different topics that people can read online.
        - Purpose:
            A server can store all kinds of information, like books, 
            while a web server is more like a library dedicated to online books (websites).
        - Access:
            Just like u need a library card to borrow books, computers need permission to access servers. 
            Web servers are like libraries with online memberships for websites.
    Q : why HTTP comes with GET request
    Q : diff b/w sniffing vs spoofing

### More HTTP - Verbs/methods & requests formats
    Q : why body section doesn't come in GET request 
        Ans : 
    Q : when body section comes with GET request - then why body section is skipped by the server
        Ans : 
    Q : in which case , body section will come with GEt request
        Ans : 

    Q : why body section will comes with POST request to the server
        Ans : cuz eg : we're loginIn instagram , so this request will be POST request 
            & whatever u filled inside the loginIn page - will be considered as sensitive data
            that's why that data comes inside body section
            request = POST request + data comes inside = body section => that's why body section comes with POST request
    
    Q : define Accept-Encoding in HTTP request
        Ans: https://www.perplexity.ai/search/whats-AcceptEncoding-in-vqQ.HNktRta4Wf0N6wrERQ
    Q : define Accept-language in HTTP request
        Ans: https://www.perplexity.ai/search/whats-Acceptlanguage-in-vqQ.HNktRta4Wf0N6wrERQ
```

- Lecture 4 : 
```
### 7. More on Cookies
    - Restrict access to cookies (how to protect cookies from unknown access)
        Q : repeat once again why "Secure" & "HttpOnly" attributes required 
```

- lecture 5 : 
```
### Intruder
    Q : what "field fuzzing" means or "fuzzing" means

### Sequencer
    definition
        Q : "how much 'randomness' of that session Cookie" - what does this statement means

### Decoder
    Q : what does encoding & decoding means
        is encoding = encryption & decoding = decryption , is this statement correct or not

### Comparer
    Q : what does parameter means 

### Scanner
    Q : what vulnerability assessment means

### Ques
    Q : in Q2) , what tool could we use to analyze randomness in different pieces of data such as password reset tokens ?
        so here what does Token means
```

- Lecture 8
```
mine general doubts
    Q : what's the importance of having proxy server
    Ans : 
    Q : is there are alternative of proxy server & VPN
    Ans : 

### role/working of proxy
    Q : what does forwarding & dropping means in terms of proxy

### Practical Work : working of proxy in BurpSuite
    Q : whenever sir say we'll start the machine of tryhackme & to set a VPN , then how to set a VPN before
```

- Lecture 9
```
mine general doubts
    ### Ques
        4) Which poisoning issue arises when an application behind a cache process input that is not included in the cache key
        Ans : Web Cache Poisoning
        Doubt : 
            "Web cache Poisoning vulnerabilities arise when an application behind a cache processes input 
            that is not included in the cache key"
            1st) explain what have u understand after reading this statement
            2nd) ask from sir i.e "whenever u read a sentence & after reading it 
                - then couldn't able to understand then what he do"
                give ur example here that u read the above sentence but u couldn't able to understand
        AI Ans : https://www.perplexity.ai/search/sentence-Web-cache-W.Ovt8LGT_S6OoA9N7uriA
```

- Lecture 10
```
### 1. Intruder
    - intruder has 4 different attack types
        Q : statement "multiple payload sets" , here what "sets" means
        Q : in sniper , we need to put one by one the same payload on different positions
            & that payload will run one by one 
            & in "Battering Ram" , same payload can run on every selected positions simultaneously at the same time
            & in Pitchfork , running different payloads for different positions simultaneously at a time 
                (like username column have a different payload & password column have a different payload)
            Ans : check Ques 

### 2. Sequencer
    - Ques
        7) In order to find the usable bits of entropy we often have to make some adjustments to have a normalized dataset.
		    What item is converted in this process?
        Ans : Token
        Doubt : couldn't able to understand why Token came & why Token considered as conversion in terms of what
```

- Lecture 14
```
### 2. Exploiting XXE to perform SSRF attacks 
    - Ques : 
        Q : what's EC2 metadata endpoint
        or how to generate that SSRF attack request (like we'll be the user here in this)

```

- Lecture 16
```
mine doubt 
    Q : what's BruteForce attack

    Q : what's the major diff happened 
        b/w fcrackzip using dictionary method vs fcrackzip using bruteForce method/mode
    Ans : mine thought : 
        in dictionary method : we used a wordlist based on password (cuz we did I.G on victim's password)
        in bruteForce method : we used bruteforce way
        - before cracking victim's device password , 
            u must do I.G (which is a 1st step) on it otherwise u can't crack the password
```

- Lecture 17
```
mine doubt : couldn't able to understand "balance" in terms of code

### 7. XSS challenge 7
    Q : why not like this '>onmouseover=alert'(document.URL) instead of '>onmouseover='alert(document.URL)
    Ans : '>onmouseover='alert(document.URL)
        we put a single quote after = (equals to) cuz we also want to execute the payload 
        otherwise making payload doesn't make sense
    Q : 1) but why not like this '>onmouseover=alert'(document.URL)
        2) why do we even putting a single quote after = (equals to sign)
            means for balancing , we already put the single quote & "greater than sign"
            for this output (which we got in inspect tool) i.e '>onmouseover=alert(document.URL)'>


### 8. XSS challenge 8
    Q : couldn't able to understand the solution from star to end , please explain it once again
    
    Q : when we're getting issue of escaped character in input field , then we use the URL to implement XSS
        but is there any other way to implement XSS except using input field , URL address bar of browser

    Q : <input type="submit" name="submit" value="ironman"onmouseover="alert(document.URL)">
        in this , why we put double quotes 2 times i.e after ironman & after = (equals to sign)
        can't we do this way value="ironman"onmouseover=alert"(document.URL)">
        Ans : cuz we're defining the onmouseover as a attribute of "input" tag
            so inside input tag it'll be this way onmouseover="alert(document.URL)"
            & we define a double quote before onmouseover - cuz ironman is a value of value attribute that's why
            so overall looks like <input type="submit" name="submit" value="ironman" onmouseover="alert(document.URL)">
```

- Lecture 21
```
### 1. how to get information from the application's database via SQL injection
    - STEP 2 : 
        Q : sir u said whenever we got the vulnerable parameter (on which we can perform SQL injection)
	        then try to find out the "how many columns have in the application"  
            Doubt 1 : what does parameter means
            Doubt 2 : how do u know that vulnerable parameter is on URL address bar
                what if there's a different vulnerable parameter which is not on URL address bar
            Doubt 3 : are there common corners of a webapp where most of the time vulnerabilities occurs 
                if that webapp is vulnerable
                - means eg : in home , there are common spots where issues comes generally 
                    so is that same thing happen with webapp
            Doubt 4 : when SQL injection occurs in an webapp 
                or how to know whether that webapp is vulnerable by SQL injection
            Doubt 5 : how to prevent SQL injection
    
    - STEP 5.2 : 
        Doubt : "http://testphp.vulnweb.com/artists.php?artist=-1 union select 1, table_name,3 from information_schema.tables where table_schema=database() limit 0,1"
            couldn't able to understand the command
```

- Lecture 22
```
mine general doubts : Stored XSS
    Q : real life example of it
    Q : How Stored XSS can be dangerous 
    Q : How to prevent it
```

- Lecture 23
```
mine general doubts 
    Q : whatever attacks we did on a vulnerable webapp like SQL injection , bruteForce , XSS , CSRF , etc
        are all those experiment based or are there any common ways that if let's say 
        a webapp has SQL injection vulnerability - then these are ways to prevent/sanitize the webapp from SQL injection

    Q : how to know which kindof vulnerabilities a vulnerable webapp/website has
        means do we use a particular tool to find the vulnerabilities or like what ?
```

- Lecture 24
```
mine general doubts
    Q : are there many different types of Brute Force attack like "Dictionary attack"
    Q : how to prevent BruteForce attack or what're the sanitization methods to protect 
        (like login page or signup page or contact page)
```

- Lecture 25
```
mine general questions
    Q : what does deface means 
    Ans : https://www.perplexity.ai/search/what-does-deface-OQF5NiYGRiCIYJKGi4bM2g

    Q : textContent vs innerText vs innerHTML in html

### 2. Types of it
    Q : diff b/w Stored Vs reflected XSS , give a real life example
        Note : after asking from sir - even if u don't understand - then use ai tool
    Q : DOM-based XSS
```

- Lecture 26
```
mine general doubts
    Q : define Severity 
    Ans : https://www.perplexity.ai/search/Severity-means-in-UQwa4Gn_SUaenJ2OxyrqMg

    Q : ways to find out the RCS vulnerability have in a webapp or not

    Q : after getting the Shell of a victim/server's system via RCS - then files & folders can be deleted

### 1. what's Insecure Deserialization
    Q : when Deserialization becomes Insecure
        Ans : when converting/going from one data form (like JSON) to object
            so if u're validating this process via insecure way aka insecure Deserialization
        Doubt : here validating - u mean "during the process of converting" - this u mean
            cuz Me couldn't able to understand "validating" here
```

- Lecture 27
```
### 1. understanding the vulnerability
    Q : what's security advisory

    Q : what's CVSS score


```
