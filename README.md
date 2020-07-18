# #CTFFriday 2020JulyWeek2

* Date: 10th July 2020
* Time: 2:00 to 3:00 PM

## Organized By

 ![](img/0.png)   

 <span style="color:red"> Net Square Solutions Pvt. Ltd.</span>                              

## About Me

Hi,

I am [Deval Khatri](https://twitter.com/devalpkhatri) and I am currently working as a Security Analyst at  [Net Square Solutions Pvt. Ltd.](https://net-square.com) I participated in ctf as Name : `` D ``

## Overview

This `CTF` is build by [Smit Patel](https://twitter.com/smit_2307) . There were 3 challenges based on Enumeration,MISC, Encryption Decryption and User Enumeration.

<h3>Challenge-1</h3>

**Flag 1 :** 10 Points 

**Name:** `` Enumration ``

**Description :** 

First channelge is to enumerate and using enumeration techniques we have to gain the first flag so, For the first flag as it name suggested Enumeration we have to enumerate the as much as possible.

![](img/1_1.png)  
 
As the first try I tried and navigated to the `robots.txt` file when I went through the page after few lines I saw clearly that the flag is written in the clear text in the middle of the lines and I got the first flag.

![](img/1_2.png)

Flag 1 : `nsctf{Fear_of_a_name_only_increases_fear_of_the_thing_itself}`

<h3>Challenge-2</h3>

**Flag 2 :** 150 points

**Name:** `` Welcome to magical world! ``

**Description :** 

After solving the first challenge I moved to the Second challenge which is is based on decoding and find the path using decoded strings in brief. 

![](img/2_1.png)

I was stuck and did't know where to navigate and suddnly I got hint and As explained in hint "find the Father of Harry Potter". So that means that somewhere in the server there should be a page or an image of Harry Potter's father james potter. So I checkd the view source page and searched for string "jamespotter".
  
![](img/2_2.png)

As expected earlier I found the page url jamespotter.html and then navigated to ``jamespotter.html`` page.

![](img/2_3.png)

At this point i think that I have to enumerate first and Check the page source of the ``jamespotter.html`` page. After opening generallythere should be some thing in comments and I observe that there is one string which is given in comment. 
which is ``<!--L3NjcmlwdHMvcmV2YS56aXA=-->``

![](img/2_4.png)

Quickly I copied that string and opened the online base64 decoder available and decode the string and I got one file path. ``/scripts/reva.zip``. which is lead us to one Zip file.

![](img/2_5.png)


Now I followed the path and which downloaded one ``reva.zip`` file in my machine.

![](img/2_6.png)

After extracting the ``reva.zip`` I got one ``reva.pcapng`` and I got confirm that this is the file of pre captured packets so, I rename it to ``reva.pcap`` file.

![](img/2_7.png)

`Rename : reva.pcap`

![](img/2_8.png) 

As it is `pcap` file I quickly open the `wireshark` network analyzer tool and open the `reva.pcap` file into it.

![](img/2_9.png)

There were many packets and connections were captured in that pcap file so As given in the hint I have to look for the packets which have length of `54` bits also I obsered that there is some packet transfer is going on between source ip `192.168.30.31` and Destination ip `192.168.30.141` on `TCP port 8800`. Hence I filtered the result in `wireshark` as `tcp.port == 8800` and I got all the filtered results. 

![](img/2_10.png)

When I I filtered all the packets  and analyze all the packets I got something change in all the packets , As I move further I observed that one bit is constantly changing and which represents single letter as here we got first letter as ` R ` .

![](img/2_11.png)

When I checked all the packets I was collecting all the changing bits and writing in separate notepad afterwords By Combining all the letters from each packets we get one string.and at the end I got another flag for the challenge.<br/>
String : `Ron weasley win 87456 points for gryffindor house nsctf{D0BBy_!5_fr33_N0w!}`

![](img/2_12.png)

Flag2 : `nsctf{D0BBy_!5_fr33_N0w!}`

<h3>Challenge-3</h3>

**Flag 3 :** 200 points 

**Name:** `` Encryption Decryption and User Enumeration``

**Description :**

After collecting two flags its time to check the Third challenge. This challenge is based on Encryption Decryption and User Enumeration fot that first navigate to the challege page as said in the hint `James Potter will help you to gain more points.`

![](img/3_1.png)

Again I started the same approach and first check the view page source Now when we scrolldown to the bottom that page we will find some html encoded characters.I have copied all the characters which is shown in the page.

![](img/3_2.png)
 
I copied that characters and tried to decode using online decoing plateform,Then i started Decode those characters online and  I got one string <br/> 
`<!--Bless him, look, he knows his mummy! Professor Albus Dumbledore give 14986 points to Rubeus Hagrid for figth against pupy!-->`

![](img/3_3.png) 

As I checked I got the below string.

![](img/3_4.png)

I was stuck and again I rolled back and started enumeration and Again I nevigated to the `robots.txt` and observed that there is  one file path `/undermaintenance.html` 

![](img/3_5.png)

So, I tried to access `undermaintenance.html` page and I got this below shown page.

![](img/3_6.png)

As I tried to enumerate the page using page source and I found one string `HermioneGranger dot JointPhotographicGroup is under img` so there must an img named directory in the server.

![](img/3_7.png)

So quicky I tried to access the img directory and I found the directory listing but I saw that there is one pic named `HermioneGranger.jpg` is there.

![](img/3_8.png)

I tried and access that image and download the same image.

![](img/3_9.png)

As from the image the first thought is to check for tho extract data from the image so I opened that image in `stegosuite` tool which is used to extract the data. but then I thout I need the password. Again I went to `robots.txt` and ovserved that there is one directory named `/hidden/hint.txt`.

![](img/3_10.png)

I Access that directory and found thte string `Sha@st3r` which can be used as the password to extract the data from the image.

![](img/3_11.png)
I Applied that string `Sha@st3r` as password and extracted the data and I found another string `Hermione Granger win 64811 points for gryffindor house.`

![](img/3_12.png)

As everytime I got somthing Points so I Again checked the `robots.txt` file and observed that there is another directory named `/score/score.txt.c`.

![](img/3_13.png)

I found one string which is aes encrypted. `ypEo6RrCiItk8rUGudBeBjgZbTEzAkcCzm+tTXrk8kSzWPCw8m7NOPSAGZcAj2tr` 

![](img/3_14.png)

Also when I looked into the `/hidden/hint.txt` I found some strings may be that can be used as the AES Decryption Secret key.So I tried following string `Fearofthenameincreasesss` as secret key.

![](img/3_15.png)

Now I have AES encrypted string `ypEo6RrCiItk8rUGudBeBjgZbTEzAkcCzm+tTXrk8kSzWPCw8m7NOPSAGZcAj2tr`  and its Secret key `Fearofthenameincreasesss` so I tried both values in online AES Decryption tool and set the mode as `Select Mode : CBC` and `Key size in Bits : 192` And by decrypting I got below string. `SGFycnkgUG90dGVyIHdpbnMgMDk0NzIgcG9pbnRzIGZvciBncnlmZmluZG9y` and again decoding it in plain text finally I got below plain text message as `Harry Potter wins 09472 points for gryffindor`
 
![](img/3_16.png)

Now I got another points but then I found under path `/hidden/hint.txt` and scrolled till middle of the page and got the random string `SSBhbSBuc2N0ZiBhcyBhIHVzZXIu`.
 
![](img/3_17.png)

I tried online base64 decoder and decoded as plain text as `I am nsctf as a user`. 

![](img/3_18.png)

So I get to know that there is one user running on the system and may be I have to login as nsctf user. So I used `nmap` and check the ssh service. and I got open running ssh service.

```
deval@ns:~$ nmap -p 22 10.90.137.137
Starting Nmap 7.80 ( https://nmap.org )
Nmap scan report for 10.90.137.137
Host is up (0.0093s latency).

PORT   STATE SERVICE
22/tcp open  ssh
```

Now I have the user as `nsctf` but not the password so for the password I combined the collected points and which created one number `87456149866481109472` and that can be used as the password.

![](img/3_19.png)

Now I have username and password and ssh service open. So I logged in with command `ssh nsctf@10.90.137.137` and it asked password and I entered as `87456149866481109472` And I logged in successfully. 


![](img/3_20.png)

Naviated to `/home/master` directory and I got one `winner.txt` file. do `cat winner.txt` and you get your third and final flag.

![](img/3_21.png)

Flag 3 : `nsctf{@1w@y5_+h3_!nn0c3n+_@r3_+h3_F!rs+_v!c+!m5}`

It was a very nice CTF by [Smit Patel](https://twitter.com/smit_2307).

Winner and writeup Author : [Deval Khatri](https://twitter.com/devalpkhatri).

Here are the scoreboard of CTF.

![](img/3_22.png)
