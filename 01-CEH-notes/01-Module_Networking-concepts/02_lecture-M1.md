#WsCubeTech-CEH-notes 

---
### What we'll learn 
> Lecture Name : Type Of Networks
> 1. What is MAC address
> 2. versions of IP address : IPv4 VS IPv6
> 3. Types of IP address + why types of IP address invented + rules for only private vs public IP
> 4. all about MAC Address

---

### What is MAC address
- Importance of it
	- for network address , we use IP address but with only using network address, communication can't happen <br>cuz in our system - attach with many things which should contain address of those things (like wifi adapter)
	- let's say what if someone connect ur "wifi adapter" with a network for crime & illegal things , <br>then there's no identity left cuz "wifi adapter" is a hardware <br>that's why it's very imp , so MAC address is for every hardware devices ✔
	- Eg : wifi router has it's own unique MAC address , <br>but in network address, IP address used - cuz in network, communication happens via frequencies ✔
	- Eg of hardwares which has a MAC address : bluetooth , etc
- About it
	- MAC address = aka hardware address
	- it's a unique address for every hardware devices (like wifi-adapter)
	- this address can't change cuz it's for hardware devices - to identify particular hardware device , <br>so if u want to change the MAC address of that hardware device permanently <br>then u have to open that hardware device & do it manually ✔ <br>- but in Ethical Hacking , we'll change the MAC address of a hardware device - not completely permanent but kindof ✔ <br>- this we'll see in "anonymous" lecture
	- so a hardware has it's own address i.e a MAC address ✔

### versions of IP address : IPv4 VS IPv6
- difference b/w IPv4 VS IPv6 <br><img src="../notes-pics/01-Module/02_lecture/02_lecture-0-M1.jpg" alt="Pic 1" width="500"/>
- in pic , `v` means version , what version of that IP address , <br>- so `v4` - 4th version of IP address & same with IPv6 , <br>- & we'll not learn about older versions of IP cuz those are not in use in modern world , so no need to do scanning on them
- IPv4 - mostly used & IPv6 - currently not in use globally for a common user , <br>- so currently IPv6 is in testing phase (for to check whether it's working fine or not)
- Explanation : difference b/w them ✅
	- Address size : IPv6 has more storage to send & receive heavy data than IPv4
	- Address format : 
		- in IPv4 , using dot to write/show a IPv4 address known as Dotted Decimal Notation <br>in IPv6 , using semi-colon/double quotes to show a IPv6 address known as hexadecimal notation
		- in IPv4 , total pairs are 4 only & in IPv6 - total 8 pairs 
		- so in IPv6 , first total 4 pairs are same as IPv4 acc. to information wise <br>but last total 4 pairs contains more information about a Device ✔
	- Prefix Notation : 
		- in IPv4 , let's say ur one of the router giving maximum limit for IP addresses <br>for connecting `24` devices  & u want to scan 24 IP addresses of each 24 devices <br>then we have 2 ways : 
			1. either scan all those 24 IP addresses manually one by one 
			2. using Kali's inbuilt tool , so let's say starting IP address is `192.149.0.0` , so if that router support maximum 24 devices <br>then `192.149.0.0/24` , so let's say we're scanning 24 IP addresses , so due to this way - we can scan all 24 IP addresses quickly ✔
			- `192.149.0.0/24` : means we specify starting IP address & `/24` total IP addresses we're assigning to scan them all
		- same in IPv6
	- Number of addresses : 
		- importance of why IPv6 came if we have IPv4 ✔
			- currently internet users are more than around 5 Billions , <br>so via IPv4 address - only maximum IP addresses can be created 4.7 billion IP addresses around the globe 
			- so IPv4 only contain upto 4.7 billions IP addresses , so what if we give 4.7 billion IP addresses <br>to each internet users - then is it possible that each users can use internet properly ?  <br>Ans : no can't possible cuz population rising & growing everyday & day by day internet users are increasing
			- that's why IPv6 came , so IPv6 have total 340 trillion, trillion, trillion IP addresses
			- so more IP addresses can be created via IPv6 than via IPv4 
		- How is it possible to make 340 trillion, trillion, trillion IP addresses via IPv6 instead of via IPv4 ? ✔
			- cuz in IPv4 , IP addresses are created by only numbers <br>but in IPv6 , IP addresses are created by numbers & alphabets
		- how in IPv6 , IP addresses are created ✔
			-  IP addresses are created via taking numbers from `0 - 9`  & alphabets from `A - F OR a - f` 
			- so these are 2 ranges due to which IP addresses are created in IPv6
	- in that above Pic of IPv6 is wrong , actually IPv6 
		- looks like this <br><img src="../notes-pics/01-Module/02_lecture/02_lecture-00-M1.jpg" alt="Pic 1" width="500"/>
		- in IPv6 , in one of the pair out of 5 - will contain double colon & rest pairs <br>will have single colon <br>The IPv6 addressing architecture allows you use the two-colon (::) notation to **represent contiguous 16-bit fields of zeros**
		- for more : <br>> [What is IPv6: Important Features and Uses](https://www.spiceworks.com/tech/networking/articles/what-is-ipv6/) <br>> [IPv6 Address Representation | NetworkAcademy.io](https://www.networkacademy.io/ccna/ipv6/ipv6-address-representation)

### Types of IP address + why types of IP address invented + rules for only private vs public IP
- Types of IP address
	1. Public
	2. private
	3. static
	4. dynamic
- Explanation : each types of IP address
	1. Public IP vs Private IP ✅
		- Private IP : <br>- use in LAN network (where only 4-5 devices are connected) ✔<br>- Private IP is like a nick name of a person , means only close persons or family members call him <br>via his nick name but when that person goes outside then nobody knows his nick name , <br>so same as with Private IP address , this IP address doesn't go outside  & nobody knows about a private IP address
		- Public IP : <br>- use in WAN network ✔, Eg : connected public IP addresses with internet <br>- Eg : public IP are real names like ur name in aadhar card , ur real name used in govt. documents , etc
	2. static vs dynamic IP ✅
		- static IP : it means fix/never-change/non-changeable IP address <br>dynamic IP : means changeable IP address
		- why static & dynamic IP address introduced : 
			- cuz IPv4 address not able to fulfill the demand of no. of internet users - cuz only maximum 4.7 billion IP address can be <br>created & if each IP address (out of 4.7billion) give to each people - then till IPv4 not able to fulfill the demand <br>for each no. of internet users - that's why static & dynamic IP address introduced
			- so static & dynamic IP address provide ways to utilize different IP addresses of IPv4
		- in Dynamic IP address 
			- let's say a phone/lapi is off right now or that phone is currently not using the internet or router is off right now <br>then the IP address (which was given to that phone when phone was online) will be given to the other device , <br>otherwise that IP address will get wasted (cuz that phone is offline right now) <br>so to utilize that IP address , it'll get transferred to the other device which is online <br>- so that IP address will get transferred/given to that user who need or just came online
				- how data stored of dynamic IP address : so let's say - `9am - 10am` that device had that IP address <br>& at `10:11pm` , that IP address is being transferred , so this much of details - IP address kept ✔
				- Q : what's the advantage here <br>Ans : those 4.7 billion IP addresses are getting utilized (instead of getting wasted)
				- Q : how we're utilizing 4.7 billion IP addresses <br>Ans : each phones (who had different IP address) are now offline or not have balance - so due to Dynamic IP address, the 4.7 billion IP addresses (of IPv4) are getting utilizing & giving to those devices (which are online)
			- Dynamic IP addresses used by normal/local internet user like u ✔
		- in static IP address
			- Q : who need static IP address ? <br>Ans : those who wants fix IP address
			- Eg of dynamic IP address : google need static IP address cuz let's say google has dynamic address <br>then today u're searching it but what if google using dynamic IP address <br>then next day u have too look up for it's new IP address & in long term , u'll not able to reach at google servers
			- Eg of static IP address : big brands like ecommerce , clothes , etc - they need a static IP address <br>so all the servers that we search like YouTube , etc - all they use fix IP address
			- Static IP addresses used by bigger companies like google servers that we search for every day
			- Static IP address (of ur website) is linked with ur domain name (which u purchased) - which we'll see in upcoming lectures
		- Eg : understanding Dynamic IP vs Static IP addresses ✅
			- 1st Situation : school's address is changing but 4 friends addresses is fixed
				- let's say a School address is "Sector A" & we have 4 friends/Systems i.e teen , Aditya , kate , tom  
				- & all these 3 friends goes to same school (which has address i.e Sector A) but what if in next day , <br>the school address changed into "Sector B" & even next day becomes "Section C" & so on..
				- Q : are those friends able to reach school easily ? <br>Ans : No , cuz that school's address is not fixed - so school is one of the place which as same fixed address <br>so in reality , if this happen - then u never able to reach at the school
			- 2nd situation : school's address is fixed but 4 friends addresses are changing
				- Q : out of 4 friends , what if anyone's house address gets changed then is there any issue will come ? <br>Ans : No , cuz at the end all those 4 friends will meet at the same school only , <br>then no bothering issue will come even if someone's address gets either changed or remain fixed
			- so the school (which is the main thing) address should be fixed always <br>& address of those 4 friends either remain fixed or address gets change doesn't matter
			- Conclusion : the school = static IP address & those student's home addresses = dynamic IP address
	- Practical Examples : Static vs Dynamic IP address ✅
		- Eg of static IP address : server of a company (like google)
		- Practical Eg of Dynamic IP address : 
			- STEP 1 : don't use router network , on ur SIM internet data & in browser & search `whatsmyipv4` & enter
			- STEP 2 : click on first URL of a website & just focus on only IPv4
			- STEP 3 : remember - ur IPv4 address when u were online will be different<br> & Now keep ur phone in "airplane mode" & again off the "airplane mode" & connect with SIM data net <br>reload that website & again check ur IPv4 address will be different ✔
			- so this is our dynamic IP address
		- Practical Eg of static IP address 
			- don't use ur SIM's internet & use ur Router's Internet -> & follow above same steps <br>& when u follow the STEPS as above then IP address of router will not change cuz it's static IP address
- Rules in Types of IP addresses
	- Rule is for only Public & private IP address , this rule is not for static & dynamic IP address <br>& why no rule for static & dynamic IP address - u'll understand later on
	- Rule for Public & Private IP address `v imp ⭐`
		- Public IP address = never talk to Private IP address & same as vice versa <br>this rule is v imp to remember
		- Private IP address has different network range cuz it's used in LAN network & <br>Public IP address has different network range than Private IP , cuz a Public IP used in WAN network ✔ <br>Conclusion : so network range of a Public IP address has bigger & a Private IP has smaller

### MAC address
- MAC : Media Access Control Address
- Rules of MAC address : a MAC address made of combination i.e `0 - 9` & `A - F (only capital alphabets)` ✔
- understanding MAC address 
	- Pic of MAC address :<br> <img src="../notes-pics/01-Module/02_lecture/02_lecture-1-M1.jpg" alt="Pic 1" width="600"/> <br> - https://ipcisco.com/wp-content/uploads/2023/06/what-is-a-mac-address-ipcisco.com_.jpg
	- in a MAC address , total 6 pairs ✔
		- first 3 starting pairs is organizational Unique Identifier <br>& last 3 pairs is Network Interface Controller
		- 1st pair : country - in which country , for which hardware that MAC address given for <br>2nd Pair : state - which state of that country 
		- 3rd pair : (Vendor + city) details <br>- vendor = means which country made that product & city = means in which city, that product supplied <br>- here ISP will come cuz it's MAC <br>- Eg : if any crime happen via ur wifi which is made by "mercusys" then MAC address of this company router will go to Cyber Police
		- last all 3 pairs : contain only Device information/ID + little bit of billing info <br>(not that bill which u buy but the price at which company bring into market) - same as in IPv6
	- Ques : Eg in this Pic , is the MAC address correct or not ? <br>Ans : no , <br>1) cuz combination is `0 - 9` & `A-F (only capital alphabets)` should be used to make a MAC address <br>2) in a MAC address , each pairs separated by hyphens (which is a standard format of a MAC address) , not colons <br>but colons also fine
- How to check MAC address
	- winOS : cmd = getmac
	- linux & MacOS : Terminal = ifconfig
	- output : <br> <img src="../notes-pics/01-Module/02_lecture/02_lecture-2-M1.jpg" alt="Pic 1" width="600"/>
	- Q : in output , why have different MAC addresses <br>Ans : cuz ur System has motherboard + bluetooth + etc - so all of these device has their own MAC addresses ✔
	- Practical Eg : of getting vendor details of an MAC address (of a device)
		- STEP 1 : take out one of the MAC address , let's say we took `D0-39-5A-13-08`
		- STEP 2 : in browser , go to [MAC vendor + Address Lookup](https://maclookup.app/) & paste that MAC address ✔ <br>u can use alternative websites to see details of this MAC address , we're using this one <br>cuz it gives more details about the MAC address
		- STEP 3 : output : u'll get details like this <br> <img src="../notes-pics/01-Module/02_lecture/02_lecture-3-M1.jpg" alt="Pic 1" width="500"/>
		- here u can see first 3 starting pairs of that MAC Address shown as `OUI` & other details which contain by those first 3 pairs <br>like location , vendor name , address , assignment type & initial registration

### End of the lecture (Doubts) : 
- More about Public vs Private IP : [Public vs Private IP Address - PowerCertAnimatedVideos YT](https://www.youtube.com/watch?v=po8ZFG0Xc4Q&ab_channel=PowerCertAnimatedVideos) ✔
- Q : how to identify which IPv6 format correct & which one is wrong <br>Ans : [parameters to identify which IPv6 correct & which is not](https://www.perplexity.ai/search/examples-of-IPv6-LBMiUVz6QKOshCVRaCIYow) ✔ OR [Ans 2](https://www.perplexity.ai/search/parameters-to-identify-p8kS_P_nQU26L.6h87TeUg)
- Q : About MAC address <br>Ans : <br>> https://medium.com/@lakshanmamalgaha/what-is-a-mac-address-and-why-you-should-know-about-it-9f970b3ba3fd <br>> https://www.techtarget.com/searchnetworking/definition/MAC-address
- Q : static IP or dynamic ip , which used by normal users of internet ✔ = [Ans](https://www.perplexity.ai/search/static-IP-or-jywm81xkRxewtANGmNgQLg) 
- Q : How both IP address + MAC address (of a device) interact with the server ✔<br>Ans : https://www.scaler.com/topics/computer-network/what-is-mac-address/
- My Doubts : 
    - Q : in `whatsmyipv4` website ✔ <br>- but my IPv4 address is not changing when i try to do via connecting with router & disconnecting+connecting with router <br>even after offing the router & on the router again <br>- but when i try to do it via SIM data network then it's working - that IP was Public Dynamic IP address ✔ <br>- Q : why is it like that , is my ISP provided static IP address is it so ? <br>Ans : No , it's the Private IP address but it's dynamic
	- Q : How Dynamic & why it's not changing when u did with the router <br>Ans : cuz in router situation , the private IP address of that system will change only when a new system gets connected with <br>ur router & when u connect again then u'll see a different IP address - but generally the private IP will not change <br>cuz the router kept a large range of Private IP addresses 
    - Q : Can we change the MAC address for temporary? <br>yes , we'll change it for keep ourself anonymous but it's upcoming topic <br>we can't change MAC address permanent but we'll hide/change kindof like permanent
    - Q : about Port & Port no. 80 <br>Ans : we'll understand in later stage of concepts <br>that Demo practical on "hack the system via it's IP address" - just shown for motivation to learn more
- mostly hacking happens on wireless devices , not on wired devices <br>& hacking wired network are easier , so that's why mostly we'll learn about wireless network ✔
- Advice : don't see & learn outside the course otherwise u'll get confuse , so do revision what u have learned yet
