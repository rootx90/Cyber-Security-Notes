#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : System Hacking ( storm-breaker )
> 1) Intro 
> 2) Download & Installation : StormBreaker tool
> 3) Practical Work : StormBreaker tool

---
### Intro
- we'll do advance things , in previous lecture - we're able to access only Camera of Victim's system <br>- now we'll access more things of Victim's system
- we're gonna use a tool - StormBreaker
- Storm-Breaker is a GUI tool & camphish is a CLI based tool ✔
	- camphish tool : just giving & getting the camera access of a victim's system
	- Storm-Breaker tool : has many templates including camera access

### Download & Installation - StormBreaker tool
- STEP 1 : search either "StormBreaker github"<br>or click on link [StormBreaker: Social engineering tool [Access Webcam & Microphone & Location Finder] With {Py,JS,PHP}](https://github.com/ultrasecurity/Storm-Breaker)
- STEP 2 : then copy `git clone https://github.com/ultrasecurity/Storm-Breaker`
- STEP 3 : open Kali terminal , run `sudo su` & paste this `git clone https://github.com/ultrasecurity/Storm-Breaker.git`
- STEP 4 : `cd Storm-Breaker` - then run `ls` <br>- output : u'll see a "requirement.txt" file - which contains all the stuff required to run "install.sh" file
- STEP 5 : installing "requirements.txt" file , run `pip install -r requirements.txt`
- STEP 6 : to install "install.sh" file , 2 ways
	- - 1st way : use `./install.sh` <br>- 2nd way : use `bash install.sh`
	- STEP 6.1 : run `./install.sh` , output : <br>![[22_lecture-0-M3.jpg | 500]] <br>- if this error comes then don't think about it , cuz everything is setup 
- STEP 7 : run `ls` , output : we'll get a file "st.py" - it doesn't have executable permission <br>> STEP 7.1 : run `chmod +x st.py`
- STEP 8 : execute the "st.py" file , run `./st.py`
	- output : we'll get syntax error cuz its a python file ✔
	- STEP 8.1 : run `python3 st.py` , output : <br>![[22_lecture-1-M3.jpg | 500]]
	- in output , "storm-breaker" tool put all the programs & templates inside this localhost link "http://localhost:2525"
	- STEP 8.1 : copy the link of localhost & paste in a browser , output : a login page will come <br>STEP 8.2 : in the login page , for both username & password by-default is "admin" <br>- then click on "login" button , output <br>![[22_lecture-2-M3.jpg | 500]]
	- in output , these are templates which contains inside "storm-breaker" tool
	- it contains templates like camera , microphone , nearyou (means location) ✔ , normal data , weather
	- Q : all the templates are hosted by "storm-breaker" on which ? ✔<br>Ans : i.e localhost <br>Q : if Sir share any URL based on a template , then will u able to reach on this link or any data will share b/w u & sir via localhost ✔ <br>Ans : No , Solution : we need to take the localhost to world wide
	- Note : we'll not use "ngrok" tool - cuz it reveals the Public Static IP address of attacker's system ✔ <br>- we'll use "cloudflared" tool
	- Q : if we make that localhost link - world wide access , <br>then all those templates (of "storm-breaker" tool) will get world-wide access or not ✔ <br>Ans : Yes , those templates will become world-wide access

### Practical Work : StormBreaker tool
- STEP 0 : open kali terminal , run `sudo su`
- STEP 1 : run `cloudflared --url http://localhost:2525` : means take this URL & make it accessible world-wide
	- output : <br>![[22_lecture-3-M3.jpg | 500]]
	- STEP 1.1 : copy the cloudflared generated link & paste it in a browser , output : login page <br>STEP 1.2 : username & password is admin , output : all the templates will be shown <br>![[22_lecture-4-M3.jpg | 500]]
	- Q : is there any difference b/w these 2 different outputs ✔
		- 1st output of localhost : <br>![[22_lecture-2-M3.jpg | 400]]
		- 2nd output of world-wide : <br>![[22_lecture-4-M3.jpg | 400]]
		- difference is <br>> in 1st output : all those templates are inside localhost <br>> in 2nd output : all those templates are world-wide
- STEP 2 : copy the world-wide url of camera access 
	- i.e `http://observed-inquiries-documented-deputy.trycloudflare.com/templates/camera_temp/index.html`
	- & send it to Victim's system 
- STEP 3 : once that Victim open the link on his/her own system
	- output : we'll get details for that Victim's system <br>![[22_lecture-5-M3.jpg | 500]]
	- in output , we got details like Public Static IP address , OS name , etc
	- STEP 3.1 : when that Victim allow the camera access , output : we'll also get pic of that victim
	- imp one is nearyou i.e location access ✔
- STEP 4 : copy the link of "nearyou" i.e location & send to the Victim's system
	- if that victim don't allow - output : "user denied the request for Geolocation"
	- if that victim allow - output : we'll get a google map link <br>![[22_lecture-6-M3.jpg | 500]]
	- STEP 4.1 : copy that google map link & open in a browser , output : we'll got to know the location of the Victim
	- we'll get almost accurate location in PC
	- `imp note ✅` : in phone , we'll not get a accurate location of that Victim cuz due to security purpose <br>- in phone , 200-300 meter a location will be shown from the actual location ✔
	- if output errors comes like this 
		- error : <br>![[22_lecture-7-M3.jpg | 500]]
		- means ur PC or laptop's location is off by-default , that's why location not showing - go to setting & fix it

---
### Homework
1. 

---
### End of the lecture (Doubts) :
1. Q : in github , clone means ?  <br>Ans : clone - means downloading that file from github , means make a copy of that folder in ur system
2. Github is a 3rd party playstore
3. Q : which one thing mostly hacking performed <br>Ans : via a IP address of a Victim's system
- alternative of Storm-Breaker : [GitHub - jaykali/maskphish](https://github.com/jaykali/maskphish)