#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : Cryptography
> 1) Theory : Cryptography Concepts
> 2) Theory : Types of Cryptography
> 3) Theory : Types Encryption techniques of Cryptography
> 4) Theory : Types of Encryption Algorithms
> 5) Tools : Hash tools , Cryptography tools - for WinOS
> 7) Practical Work : steganography

---

### Overview - what we'll learn
1. about Cryptography
2. Objectives of it
3. Types of Cryptography
4. Encryption Algorithms

### Cryptography Concepts
- check on : Lecture 33
- More about it
	1. Data Conversion : <br>- converting a data from one form to another - so that unknown person can't understand <br>- sending data in hidden form
	2. Scrambled Code (Encrypted) <br>- means sending data in encrypted form
	3. Protect data : cryptography technology used to protect our data
	4. Email Messages + Web transactions : <br>- cryptography used in email messages , web transactions <br>- Q : in Web Transactions which cryptography will be use - Encoder or Encryption ? ✔<br>Ans : Encoder
- Objectives of Cryptography
	- Objectives : means for what purpose - the Cryptography made
	- 1) Confidentiality
		- means authorization
		- authorized person/people - can only access that data - unauthorized person/people can't <br>Eg : assume , i was sending a PDF to "Friend A" (who's authorized) <br>- but u accidentally send that PDF to "Friend B" (who's not authorized)
		- Conclusion : <br>in Confidentiality , we keep in mind - that data should be send to that person/people (who're authorized)
	- 2) Integrity
		- means only that person/people (who're authorized) can change the data - unauthorized person/people can't
		- Eg 1 : let's say u wrote a Book in PDF form - & someone (edited + wrote something) in that book <br>- due to this , data couldn't be secure 
		- confidentiality = used to secure the data & <br>integrity = used to take-care/provide-protect to secured data - from unauthorized person/people
		- Eg 2 : u're send a message "Hi" to "Friend A" - but "Friend B" changed it & send a bullshit message to "Friend A" <br>- so here no integrity of data <br>that's why Integrity needed
		- Conclusion : Cryptography take care of Integrity - so that data must not change in the middle of sending the data <br>- that's why data send/receive in encrypted form
	- 3) Authentication
		- means the data (which u got) - whether it's genuine or not
		- Eg 1 : if someone sending changed data to u - then how u'll know whether it's fake or real
		- Conclusion : Cryptography provide surety - that the data (which is sent to u) - whether it's fake or real
		- Authentication takes care of 2 things :✔<br>1) whether that data is (real or fake + corrupted or uncorrupted + contain virus or not)<br>2) sender (who send the data to u) - whether sender is real or fake
		- Eg 2 : now a days , a person/people even encrypt the virus/worm - send to receiver <br>- but Authentication - will check whether that data (which u got) - sended by real or fake person
	- 4) Non-repudiation
		- Eg 1 : Vishal (i.e real sender) send the "PDF Book" to Kapil (i.e real receiver) - & Kapil got that book properly <br>by following complete process <br>Q : can Vishal say that "me didn't send the PDF book to Kapil" <br>Ans : No <br>Q : can Kapil say that "me didn't got this data from Vishal" <br>Ans : No <br>- cuz record/details of sender person & receiver person - saved somewhere
		- means sender (who send the data to that receiver) can't deny that "me didn't send the data to that receiver" <br>- Kapil (i.e receiver) can't deny that "me didn't received that data"
		- Eg 2 : non-repudiation = use in Payment method <br>- so receiver can't say "i didn't got the payment" & sender can't say "i didn't send the payment" <br>- so all the records are saved aka non-repudiation
	- Confidentiality + Integrity + Availability = aka CIA Triad

### Types of Cryptography
- 3 types of it <br>1) Symmetric Encryption <br>2) Asymmetric Encryption <br>3) Hash functions (not included in course)
- in Symmetric , only single key used for both (Encryption + Decryption) <br>in Asymmetric , 2 keys used (1st key - for Encrypt & 2nd key - for Decrypt)

### Types Encryption techniques of Cryptography
- Encryption aka Ciphers <br>- we also saw in Wifi-Hacking
- Q : what's Encryption (Ciphers) <br>Ans : These are algorithms used to encrypt or decrypt the data
- Types of Encryption/Ciphers<br>2 Types of it : <br>1) Classical Ciphers <br>2) Modern Ciphers<br>Q : what's Classical & Modern mean<br>Ans : Classical = aka old , Modern = aka new/latest
- in Classical Ciphers techniques/algorithms
	- it has 2 types : <br>1) Substitution cipher techniques <br>2) Transposition cipher techniques
	- these 2 are basic building blocks of all the encryption techniques
	- Substitution cipher : (Note : i didn't wrote further about it - cuz Devendra sir not explained properly , i'll write once doubt of it clear)
		- a block of plaintext is replaced with ciphertext <br>- means in it , letters of the plain text are replaced by other letters or by numbers or symbols <br>- it also takes/count spaces during encryption
		- Eg : message "Hi Im devendra" <br>Q : how Substitution cipher will encrypt this message <br>Ans : it'll take starting 4 pairs including space - from the message <br>- then it'll put a "4 random pair" on that 4 pairs , <br>so it takes 4 pairs i.e "Hi I" - then assume it'll put "H29Z" on that starting 4 pair <br>- then it'll skip "m de" 4 pair , <br>then it'll take "vend" pair & put a random 4 pair - assume it'll "ZB961" <br>- & same process goes - means it'll skip next 4 pair - then take another next 4 pair for encryption
		- Eg : in maths , u learned about substitution <br>- like x = 1 <br>Q : what x = 1 means <br>Ans : means x can be replace by "1" <br>- substitute : means in football - having a substitute person for that person (who's currently playing)
		- at the end that message will look (after applying substitution cipher technique) - "H29Zm de2B961ra" <br>![[34_lecture-0-M3.jpg | 500]]
		- Conclusion : now "H29Zm de2B961ra" is not readable + not understood by anyone , except u
	- Transposition cipher : 
		- in it , letters of the plaintext are shifted about to form the cryptogram
		- Performing some sort of permutations on the plaintext letters <br>- means it reorders/rearrangement of the letters , symbols of the plain text
		- Eg 1 : Name -> EAMN or AENM or MNEA , etc
		- Eg 2 : ABC -> ABC or BAC or CAB , ACB , BCA , CBA <br>- so these are total 6 permutations <br>Q : how did u know that total 6 possibilities/permutations could be from "ABC" <br>Ans : cuz ABC = total 3 characters , so 3! (means 3 factorial) = so 3 × 2 × 1 = 6
		- in it , we can't bring a different pair to do permutation&combinations in let's say "NAME" <br>- means we can only do "permutation & Combinations" by using whatever letters/symbols inside "NAME"
- in Modern Ciphers techniques
	- Types of Modern Ciphers techniques <br>1) based on the type of key used <br>1.1) Private Key / Symmetric Key Ciphers <br>1.2) Public Key / Asymmetric Key Ciphers<br>2) based on the type of input data <br>2.1) Block Ciphers<br>2.2) Stream Ciphers
	- in based on the type of key used :
		- 1) Private Key : only same single key is used for encryption & decryption <br>- Eg : private key used for converting normal file to Zip file for encryption & decryption
		- 2) Public Key : 2 different individual keys are used for encryption & decryption <br>- Eg : it's used in mostly PDF file <br>means like a different password used to encrypt it & a different password for decryption <br>OR a different password used for decrypt - but to edit the PDF requires a different
	- in based on the type of input data :
		- based on the type of input data = means encryption & decryption done based on given input data
		- Block Cipher : Encrypts Blocks of data of fixed size <br>- it's kindof Substitution cipher & process will be same for encryption as Substitution cipher <br>> Block Cipher vs Substitution cipher <br>Eg : message "Hi Im devendra" <br>- Block Cipher encrypt let's say "Hi" & it'll keep "Hi" itself on same position , <br>means it'll not keep a substitute of "Hi"  <br>- Substitution Cipher : will keep a substitute letters/number/symbols - after encrypting that message
		- Stream Cipher : Encrypts continuous streams of data <br>- means it'll encrypt all the data in one go - without skipping anyone <br>that's why it takes time , consume processes of a system <br>- it considered as highly secured cipher technique <br>> other techniques vs Stream cipher <br>- other techniques : are encrypting a pair & skipping a pair - then encrypting a next pair <br>that's why RAM is consumed less <br>- but Stream ciper - not skipping any anything in the message & encrypting everything of the message <br>that's why RAM is consumed more

### Types of Encryption Algorithms
- Pic : <br>![[34_lecture-1-M3.jpg | 500]]
- it's no imp right now - cuz it's little advance stuff <br>- & no need to use these attacks - cuz securities already released on these attacks <br>if u do then = time waste

### Tools : Hash tools , Cryptography tools - for WinOS
- Hash tools
	- MD5 & MD6 Hash calculator tools
		- About : MD5 & MD6 are algorithms - which convert data into hash
		- MD6 Hash Generator : [Browserling – Online cross-browser testing](https://www.browserling.com)
		- All Hash Generator : [Browserling – Online cross-browser testing](https://www.browserling.com)
		- MD6 Hash Generator : https://convert-tool.com
		- md5 hash calculator : https://onlinehashtools.com
		- HashCalc : https://www.slavasoft.com
	- Hash Calculator - Mobile tools
		- these are used for Mobile
		- https://play.google.com - for MDS Checker , Hash Checker , Hashr - Checksum & Hash Digest Calculator , Hash Calc
-  Cryptography tools - for WinOS
	- these are tools completely only for Cryptography
	- AxCrypt : https://www.axcrypt.net
	- Microsoft Cryptography Tools : https://docs.microsoft.com
		- in privilege escalation , we talked about security for winOS
		- STEP 1 : setting -> search encryption -> turn it ON <br>- due to this nobody can't take ur data away - even if somebody take it away - then he/she can't understand it
	- Concealer : https://www.belightsoft.com
	- CryptoForge : https://www.cryptoforge.com
	- Advanced Encryption Package 2017 : https://www.aeppro.com/

### Practical Work : steganography
- STEPS : in WindowOS
	- STEP 1 : tool setup (Download & installation)
		- STEP 1.1 : in browser , search "openstego" tool OR [OpenStego](https://www.openstego.com/)
		- STEP 1.2 : download the ".exe" file for windows & ".deb" for kali
		- Advice : directly use it in kaliOS - if any error coming of it in WindowOS
		- STEP 1.3 : install the ".exe" file
		- open it & if java errors come - then move to STEP 1.3
		- STEP 1.3 : search "java download for everyone" OR [java.com download](java.com/en/download/manual.jsp)<br>STEP 1.3.1 : click "windows offline (x64)" -> install it
		- STEP 1.4 : open the app
	- STEP 2 : in the app
		- STEP 2.1 : in app , in "data hiding" section , select "Hide data" btn
		- STEP 2.2 : on Desktop , create a txt file -> in the file write a message "Hi secret key" -> save the file
		- STEP 2.3 : in app , message file as = select that txt file <br>cover file as = select any img
		- Cover file - means which file u want to use as a cover - so that txt file can be hide behind that cover file
		- STEP 2.3 : in "output stego file" section , save the file as output in Desktop
		- STEP 2.4 : write password as 1234 -> click "Hide data" btn 
		- Conclusion Pic : <br>![[34_lecture-2-M3.jpg | 500]]
		- output : now that file saved as ".bmp" extension
		- Note : u can change the algorithm option during encryption - but not during Decryption
	- STEP 3 : viewing both normal image & .bmp file (which has cover image) <br>STEP 3.1 : open that normal image & .bmp file , u can't tell the difference b/w both
	- STEP 4 : Q : how to find diff b/w both file <br>1) normal file image has .png or .jpg & that encrypted file has .bmp extension <br>2) both files has different size (size of normal image file has in KB & that one has in MB)
	- STEP 5 : Q : how to extract decrypt the file
		- STEP 5.1 : open the app -> click "Extract data" -> select input file as that .bmp file
		- STEP 5.2 : select output file location -> then write the password (which u made while hiding) -> click "extract data"
		- output : u'll get that file back again
- STEPS in KaliOS
	- u can do in Kali properly - cuz kali has pre-installed java version
	- STEP 1 : download that app of .deb extension
	- STEP 2 : for installation , run `dpkg - i <filename>`
	- STEP 3 : to open it , run `openstego`

- Mine thought : we don't need this tool , we can run a command to do steganography

---
### Homework
1. 

---
### End of the lecture (Doubts) :
- Student Doubts : 
	- Q : OTP bypass - via burpSuite - is it a part of WAPT
		- Ans : yes , but in this CEH course - we learned about little bit in Session Hijacking
		- like firstly , we do BruteForce to fetch the session - then bypass it
		- so we see advance concepts in WAPT
- Mine Advice : in order to understand this lecture : make a mind map
- About CIA Triad : a model made to guide policies for information security (infosec) within an organization
- More on : Substitution and transposition techniques | Monoalphabetic and polyalphabetic substitution ciphers <br>[Substitution and transposition techniques | Monoalphabetic and polyalphabetic substitution ciphers - YouTube](https://www.youtube.com/watch?v=bZBVbvNjxKY&ab_channel=AbhishekSharma)
- More on : Types of Cryptography : [Cryptography and its Types - GeeksforGeeks](https://www.geeksforgeeks.org/cryptography-and-its-types/)


