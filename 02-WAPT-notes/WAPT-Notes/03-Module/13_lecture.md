#WAPT-notes  

---
### what we'll learn
> Lecture Name : [HINDI] XML External Entity (XXE) Injection | Types of Attacks | Prevention
> 1) About XXE (XML External Entity (XXE) Injection)
> 2) How do XXE vulnerabilities arise ?
> 3) XML entities
> 4) What are XML custom entities ?
> 5) What are XML external entities ?
> 6) Different types of XXE attacks
> 7) Exploiting XXE to retrieve files - Example 1st XXE attack
> 8) Remediation / how to prevent XXE vulnerabilities

### Overview
- what is XXE
- how XXE vulnerabilities arise
- XML entities
- XML custom entities & external entities
- Overview : how SSRF attacks can be done
- types of XXE attacks

### reference 
- in this module , we're following PortSwigger academy - web security
---

### 1. About XXE (XML External Entity (XXE) Injection)
- Reference : [What is XXE ? Tutorial & Examples | Web Security Academy](https://portswigger.net/web-security/xxe)
- When data of an application & the data processed via XML (markup language) then a attacker interfere/intercept <br>
	that "processing" & from the web server , he/she could do such things like read the file , attack can be done like SSRF , <br>
	compromise the backend server , so this web security vulnerability aka XXE ✔️
- in it , we're saying `injection` cuz payload is inserted/used & via payload , everything done ✔️
- define : those applications which use XML to transferring data , so mostly XML has those features via which <br>
	we can define/declare custom entity , as a attacker , we can intercept in the middle of process of transferring data <br>
	& we can read the files , types of attacks of XXE like SSRF can be done ✔️

### 2. How do XXE vulnerabilities arise ?
- Q : When this XXE attack possible `imp ⭐`
	- cuz if specification (of the document of XML) is done properly then XXE attack can be possible 
	- or XML standard partials potentially support dangerous features via which these kind of payloads possible to execute 

### 3. XML entities
- Q : what is XML ?
    - XML stands for "extensible markup language"
	- it is a language designed for storing & transporting data & Like HTML, XML uses a tree-like structure of tags and data & unlike HTML , it doesn't have predefined tags 
- Q : what are XML entities ?
	- Define : XML entities are a way of representing an item of data within an XML document, instead of using the data itself
	- Eg of XML Entities : he entities `&lt;` and `&gt;` represent the characters `<` and `>`
	- These are metacharacters used to denote XML tags
- Q : What is document type definition (DTD) ?
	- The XML DTD contains declarations that can define the structure of an XML document

### 4. What are XML custom entities ? `v imp ⭐`
- XML allows us to define/declare our own custom entities
- Eg : of Format/syntax to define `<!DOCTYPE foo [ <!ENTITY myentity "my entity value" > ]>` - myentity <br>
  	means name of the entity u want to give & inside double quotes contain the value of that entity

### 5. What are XML external entities ? 
- XML external entities looks like `<!DOCTYPE foo [ <!ENTITY ext SYSTEM "http://normal-website.com" > ]>`
- here `ext` - means it's communicating with ur external resource i.e that URL
- Eg : `<!DOCTYPE foo [ <!ENTITY ext SYSTEM "file:///path/to/file" > ]>`
- Q : how different attacks can be done in XXE ✔️
	- so we can define XML custom entities & external entities 
	- Example : <br><img src="../../notes-pics/03-Module/13_lecture/13_lecture-0-M3.jpg" alt="" width="500"/>
	- `"file:///etc/passwd"` - here we're able to retrieve the file <br>
		cuz we define the `file` which is stored on the server i.e `etc/passwd` ✔️
	- Overview : how SSRF attack can be done : here `"file:///etc/passwd"` , <br>
		the address (of the file path we'll give) of malicious server or where we can get the user control ✔️

### 6. Different types of XXE attacks 
1) File retrieve
2) SSRF attacks
3) exfiltrate data out-of-band
4) retrieving data via error messages

### 7. Exploiting XXE to retrieve files - Example 1st XXE attack
- Reference : [Exploiting XXE to retrieve files | portswigger](https://portswigger.net/web-security/xxe#exploiting-xxe-to-retrieve-files)
- STEP 1 : For example, suppose a shopping application checks for the stock level of a product by submitting the following XML to the server:
    ```xml
    <?xml version="1.0" encoding="UTF-8"?> 
    <stockCheck><productId>381</productId></stockCheck>
    ```
- STEP 2: so we changed the above XMl code into this 
	- The application performs no particular defenses against XXE attacks, so u can exploit the XXE vulnerability <br>
		to retrieve the `/etc/passwd` file by submitting the following XXE payload:
		```xml
		<?xml version="1.0" encoding="UTF-8"?> 
		<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]> 
		<stockCheck><productId>&xxe;</productId></stockCheck>
		```
	- to exploit that above code , we took `DOCTYPE foo` then `!ENTITY xxe` entity we declared/define (what ENTITY xxe doing?) which is retrieving `"file:///etc/passwd"`
	- & then for "productId" we define `&xxe;` - here we put `&` to tell it's a entity
- STEP 3: the code of STEP 2 
	- This XXE payload defines an external entity `&xxe;` whose value is the contents of the `/etc/passwd` file and <br>
		uses the entity within the `productId` value. This causes the application's response to include the contents of the file:
    ```xml
    Invalid product ID: root:x:0:0:root:/root:/bin/bash 
    daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin 
    bin:x:2:2:bin:/bin:/usr/sbin/nologin ...
    ```
	- it'll retrieve the contents of the `/etc/password` & show the contents
	- so we got `invalid product ID` - cuz in `productId` , we define `&xxe;` & then we got the content of `/etc/password` i.e 
	```xml
	root:x:0:0:root:/root:/bin/bash daemon 
	1:1:daemon:/usr/sbin:/usr/sbin/nologin 
	bin:x:2:2:bin:/bin:/usr/sbin/nologin
	```

### 8. Remediation / how to prevent XXE vulnerabilities
- all XXE vulnerabilities arise/come cuz XML parsing library supports dangerous XML features
- easiest & most effective way to protect/prevent XXE attacks is to disable those features such as `XInclude` - disable it <br>
	but if u can't disable then overwrite the default behavior of it ✔️

