#WAPT-notes

---
### What we'll learn
> 1) what's penetration testing
> 2) what is webapp penetration testing (WAPT)
> 3) techniques
> 4) tools to use how to do

---
### Aim of this course - Anuj Sir
- after doing this course , u can say that u know WAPT even thou you're beginner/noob 
- we'll do a playlist on `burp suite` - we'll do it via TryHackMe & `WAPT` we'll do by a different playlist , so that both gets interconnected , so if anyone knows `burp suite` , `OWASP TOP 10` , & know over all `OWASP` including all test cases , that guy can go for WAPT jobs
- coz Anuj sir working as a Penetration Tester in deloitte

### overview
- u can go webapp penetration testing if you're from developer background or like u know programming stuff then u can come in appSec (application security)

---

- WebApp : means interactive application , not the static website 

### 1. what's Penetration Testing
- `Situation Example` - consider yourself as thief , u want to enter inside somebody's home
- so what you'll think first about ways to enter inside home 
    - either you'll see that i should get the door open or window via which we can enter
    - or will u try to pretend to be unknown or u can take a marriage card of someone to give them , etc
- so it's like doing penetration testing (means entering inside the house) 
- so same way we want to enter inside that webapp to get the access/loophole/vulnerability/issues
- so we're saying window/door/etc... -> these are considered as vulnerabilities
- *Example of webApp vulnerabilities*
    1) misconfiguration of web server
    2) directory traversal attack (means due to misconfiguration of web server , directories are open)
    3) used default password
    - so these are vulnerabilities , same way for their's house , door is open or window is open
- *`definition`*  
    - it's a process to identify those vulnerabilities & to check those vulnerabilities, we can exploit to do impact analysis on those vulnerabilities 
    - find/identify those issues & we exploit those issues , so that we know the impact of those issues 
- *Penetration Testing Report - To fix those issues*
    - we go directly to developer or either can share with management team/project team
    - & we can also tell them ways to fix aka `suggested remediation` & these are processors , so do it
    - all these comes under aka `Penetration Testing Report`

### 2. what's webApp Penetration Testing (WAPT)
	- webApp's vulnerabilities are different from android's vulnerabilities due to different OS & platform
	- webApp's vulnerabilities are also browsers based such as XSS (Cross Site Scripting) aka client side vulnerabilities , which you'll not vulnerabilities in their native android apps 
	- webApp's vulnerabilities such as [OWASP Top Ten | OWASP Foundation](https://owasp.org/www-project-top-ten/) , injection vulnerabilities , XSS , etc
	- `Definition` : WAPT means to identify webApp's vulnerabilities & then exploit them to understand their impact/severity of the issues

### 3. techniques of WAPT
- we'll follow OWASP (Open Web Application Security Project)
- OWASP is a non-profitable organization
- So OWASP made a standard on WAPT & it release TOP 10 webApp's vulnerabilities

### 4. Tools to use
1) burp suite/burp sweet (`v imp tool`)

