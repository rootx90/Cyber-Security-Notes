#WAPT-notes

---
### what we'll learn
> Lecture Name : Crack Zip File Password in Kali Linux | Fcrackzip
> 1) how to crack the zip file password via "fcrackzip" using directory methods
> 2) how to recover the zip file password via "fcrackzip" using bruteForce method/mode

### Overview
- we'll see "how to recover lost password of zip file" + "How to crack the password of zip file via BruteForce & Dictionary methods" <br>
	Anuj sir already made a vid on it - but that vid made via using JohnTheRipper utility (some people face issues in this utility) <br>
	so this lecture is a simpler solution i.e FCrackZip
- [How to Crack ZIP File Password Using Kali Linux? - YT](https://www.youtube.com/watch?v=1FfTQaFs6Hw&ab_channel=EthicalSharmaji) - but this lecture contain very simpler solution
- `fcrackzip` is a utility for crack password protected zip files with brute force or dictionary based attacks ✔️

---

- Q : Problem statement : is that happen with u , where u put very important documents , files , images , etc <br>
	& u want that those stuff must be password protected & u put the password via Zip feature & u forgot that password ✔️

### 1. Cracking Zip file password via fcrackzip using dictionary method
- STEP 1: make a txt file -> inside of it , write "MYSQL password is ethicalsharmaji" -> save it as secret.txt
- STEP 2: right click on the file -> click 7-zip -> click add to archive , <br>
	keep the password as `admin` & select `ZipCrypto` encryption method
- STEP 3: in terminal, run `apt-get install fcrackzip` command to install fcrackzip  
- About fcrackzip
    - it's a zip password cracker
    - few commands in fcrackzip ✔️
    	- `-v, --verbose` : mode tells how much passwords are cracked & which one are in progress
    	- `-b, --brute-force` : let's say u know the string (like how much length of the password is , <br>
			then u can use different combinations)
    	- `-D, --dictionary` : 
    		- mode used like when u have word list (like generally , word list used rockyou.txt) , <br>
    			so if u have kinda rockyou.txt file , u can use that. if u use word list for password <br>
				like football , password , system , etc then u can use `--dictionary` mode
    		- About `rockyou wordlist` : is a password dictionary used to help to perform <br>
    			different types of password cracking attacks. It is the collection of the most used and potential passwords. <br>
    			Many Password cracking tools are used dictionary attack method to retrieve the password.
    	- `-c , --charset characterset-specification` : in bruteForce mode , let's say if u know <br>
			starting few first characters or length then u can use it
- STEP 4: now cracking via dictionary mode/method
	- STEP 4.1: `man fcrackzip` command to check the man page of it which tells about fcrackzip
	- STEP 4.2: run `cd desktop` & now let's crack run `fcrackzip -u -v -D -p /usr/share/wordlists/rockyou.txt /Desktop/secret.zip`
    	- `-u` : means password could be multiple <br>
			`-v` : verbose mode , `-D` : dictionary & `-p` : means which word lists we're giving i.e rockyou.txt ✔️
    	- output : now we'll got the password <br><img src="../../notes-pics/03-Module/16_lecture/16_lecture-0-M3.jpg" alt="" width="500"/>

### 2. Cracking Zip file password via fcrackzip using bruteForce method/mode
- STEP 1: run `man fcrackzip` command & now check which commands u're gonna use
    - general commands used in bruteForce mode via frackzip
    	- `-b` : for brute force mode
    	- `-c` : for character (as a attacker , we know that password is in lower case)<br>
    		so we'll use `a` : means lowercase character (cuz that password doesn't have uppercase, symbols, etc)
    	- `-u` & `-l` for length
- STEP 2: run `cd desktop` -> run `fcrackzip -u -v -b -c a -l 5 5 secret.zip`
    - here `5 5` - is a length of password (cuz we know about that password)
    - output : <br><img src="../../notes-pics/03-Module/16_lecture/16_lecture-1-M3.jpg" alt="" width="500"/>


