{\rtf1\ansi\ansicpg1252\cocoartf2513
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\froman\fcharset0 Times-Roman;\f1\fnil\fcharset0 Calibri;}
{\colortbl;\red255\green255\blue255;\red5\green99\blue193;}
{\*\expandedcolortbl;;\csgenericrgb\c1961\c38824\c75686;}
\margl1440\margr1440\vieww25400\viewh16000\viewkind0
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0

\f0\fs24 \cf0 OhSINT - created by TryHackMe \
Link: https://tryhackme.com/room/ohsint\
\
This is an OSINT (Open-Source Intelligence) Room. There are no tools required for this room,\
all the information is readily available on the Interweb. \
\
Are you able to use open source intelligence to solve this challenge?\
\
What information can you possibly get with just one photo? - Download Task Files \
\
\pard\pardeftab720\ri0\partightenfactor0
\cf0 Firstly, I download the task files which contain only one image called WindowxXP.jpg\
\
<taskfile.jpg>\
\
1. What is this user avatar of?\
A good way to extract image metadata is using exiftool on the cli or you can also gather the same information on {\field{\*\fldinst{HYPERLINK "http://exif.regex.info/exif.cgi"}}{\fldrslt \cf2 \ul \ulc2 http://exif.regex.info/exif.cgi}} website.  Here you can see the output of both options. \
\
<exiftool.png>\
<Jeffrey's Image Metadata screenshot>\
\

\f1 Upon running exiftool we can gather that the handle/name of the owner to the image which is OWoodflint. A google search shows us that he has a Twitter profile, a Wordpress blog, and a GitHub account.\

\f0 \
<googleresults.png>\
\

\f1 Clicking on the first result (Owoodflint\'92s Twitter Profrile) we can immediately get our first answer. \

\f0 <twitterprofile.png>\
\
2. 
\f1 What city is this person in?\
I tried doing some digging through their Twitter account and their blog and I didn\'92t find anything, so I then decided to visit their GitHub account we can see our answer upon visiting the page. \
\
<github.png>\
\
\
\
3. Whats the SSID of the WAP he connected to?\
To find the answer to this question we first have to dig into those previous google results and see if there is any information that can helps us identify the SSID (Service Set Identifier) which identifies the wireless network he is connected to. Starting from the top of the google results, twitter seems to have some information that can be useful to answering this question.  The user has shared with us his BSSID (Basic service set identifier). If you don\'92t know what to do with this information you can visit https://osintcurio.us/2019/01/15/tracking-all-the-wifi-things/ and read more about wigle.net. \
\
<wiglescreenshot>\
Find the purple circle pointing to the location and zoom in as far as you can to see the SSID.\
<ssid.png>\
\
4. What is his personal email address?\
We can go back to the google results to find this answer. I found it by going to the users GitHub account.\
<github.png>\
\
5. What site did you find his email address on?\
GitHub\
\
6. Where has he gone on holiday?\
I went back to Twitter and didn\'92t find anything. So visited his blog one more time and found the location where he went on holiday.\
<blogscreenshot.png>\
\
7. What is this persons password?\
While it is bad practice to write notes, specifically credentials in the source code, developers sometimes do this to leave comments for other people in their team. If we take a look at the source code we can find a hidden word that looks like it can be the password. \
<password>\
}
