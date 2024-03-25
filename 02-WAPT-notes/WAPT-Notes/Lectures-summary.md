#WAPT-notes

---

### Lectures Summary

- Lecture 1 : What is web application penetration testing?
    1. what's Penetration Testing
        - Situation Example
        - Example of webApp vulnerabilities
        - Definition
    2. what's webApp Penetration Testing (WAPT)
        - Definition
    3. techniques of WAPT
    4. tools to use for WAPT
- Lecture 2 : WAPT Learning Roadmap 2021 | Course Overview
    1. Topics must know as a WAPT
        1. Basics/fundamentals must be clea
        2. Web Fundamentals
        3. Burp Suite
        4. OWASP TOP 10
- Lecture 3 : Web Fundamentals #1 How do we load websites? HTTP Verbs?
    1. How do we load websites ?
        1. Finding the server
            - Eg :
            - Q : what's DNS
            - Q : what is IP Address
        2. Loading some content
            - Q : how that content will come in ur browser ? 
            - Q : how all these file will get loaded on the client machine
            - Q : what is an HTTP GET request <br>
                Q : what's verb ? <br>
                Q : why HTTP comes with GET request <br>
                Q : what's GET
            - Q : what is server & web server
            - Q : what things a server serves
            - Q : How this working of web Server is done OR how the server able to send the index.html file to the client machine
            - Q : what is Protocol & why HTTPS came
            - Q : what is a web server
            - Q :
                <br>1) What request verb/method is used to retrieve page content
                <br>2) What port do web servers normally listen/runs on
    2. More HTTP - Verbs/methods & requests formats
        - GET vs POST request
        - a HTTP request is divided into 2 parts i.e
        - "headers" of the request
        - "body" of the request
        - Eg : a GET request retrieving a simple js file
        - Practical Work : how to see the "Request Headers" of a website via inspect tool
        - Responses
            - Definition
            1. 1st line - describes the "status"
            2. 2nd line - Response Headers
    3. Ques (tryhackme - web-fundamentals)
        - Q : What verb would be used for a login ? <br>
            Reason : why POST request
        - Q : What verb would be used to see ur bank balance once u're logged in ? <br>
            Reason : why GET request
        - Q : Does the body of a GET request matter ? yea/Nay <br>
            Reason : why No
        - Q : What's the status code for "i'm a teapot ?"
        - Q : What status code will u get if u need to authenticate to access some content & u're unauthenticated ? <br>
            Reason : why 401 <br>
            Q : 1st we'll see where we made the mistake
- Lecture 4 : Web Fundamentals #2 What are cookies? Explained in detail | Practical Demo | HTTPOnly, Secure Flag
    1. What are Cookies
    2. Purpose/usage of Cookies
        - used for session management
        - used for advertising
    3. why cookies or importance of it
        - Q : why cookies / importance of it
        - parts of cookies
    4. for what purpose Using Cookies
        - Eg of importance of a Session Token
        - Q : what happen if someone steal ur session-token/cookies (which is maintained by ur browser)
    5. Manipulating Cookies - how u can manipulate cookies
    6. Alternatives - useful to know
    7. More on Cookies
        - Cookies are mainly used for 3 purposes
        - creating Cookies
        - Define the lifetime of a cookie
        - Restrict access to cookies (how to protect cookies from unknown access)
        - Q : where cookies are sent
    - Homework
    - Practical Work : how to see a cookie of a website via inspect tool
- Lecture 5 : Web Fundamentals #3 Mini CTF | Tryhackme
    1. Making HTTP requests
        - about cURL utility
    2. Intro to cURL
        - `-X flag`
    3. Practical Work
        - Q 1) : what's the GET flag ?
        - Q 2) : What’s the POST flag? <br>
            Q : why "-d" comes with a POST request
        - Q 3) : What’s the “Get a cookie” flag?
        - Q 4) : What’s the “Set a cookie” flag?
    4. Summary
- Lecture 6 : Burp Suite #1 Introduction | Installation | Configuration | Proxy


