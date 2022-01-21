![banner](https://github.com/JMMoseley/THM-Writeups/blob/main/OhSINT/Images/banner.png)

# [OhSINT](https://tryhackme.com/room/ohsint)  - created by [TryHackMe](https://tryhackme.com)

This is an OSINT (Open-Source Intelligence) room. There are no tools required for this room and
all the information is readily available on the Interweb. 

## Are you able to use open source intelligence to solve this challenge?

### What information can you possibly get with just one photo? - Download Task Files 

Firstly, I download the task files which contain only one image called WindowxXP.jpg

![taskfile](https://github.com/JMMoseley/THM-Writeups/blob/main/OhSINT/Images/WindowsXP.jpg)

### 1. What is this user avatar of?
A good way to extract image metadata is using exiftool in the CLI or you can also gather the same information on [Jeffrey's Image Metadata Viewer Website](http://exif.regex.info/exif.cgi). Here you can see the output of both options:

ExifTool Screenshot
![exiftool](https://github.com/JMMoseley/THM-Writeups/blob/main/OhSINT/Images/exiftool.png)

Jeffrey's Image Metadata Viewer Website Screenshot:
![JeffreysMetadata](https://github.com/JMMoseley/THM-Writeups/blob/main/OhSINT/Images/Jeffrey's%20Image%20Metadata%20screenshot.png)

Upon running exiftool, the handle/name of the owner of the image was added to the copyright section. A quick google search shows that he has a Twitter profile, a Wordpress blog, and a GitHub account.

![google](https://github.com/JMMoseley/THM-Writeups/blob/main/OhSINT/Images/googleresults.png)

Clicking on the first result (Owoodflint's Twitter Profile) I can immediately see the first answer. 

![twitterProfile](https://github.com/JMMoseley/THM-Writeups/blob/main/OhSINT/Images/TwitterProfile.png)

### 2. What city is this person in?
I did some digging through his Twitter account and blog and didn't find anything at first, so I then decided to visit their GitHub account we can see our second answer upon visiting the page.

![GitHub](https://github.com/JMMoseley/THM-Writeups/blob/main/OhSINT/Images/github.png)

### 3. Whats the SSID of the WAP he connected to?
To find the SSID (Service Set Identifier) which identifies the wireless network he is connected to. I recall that his twitter seemed to have some information that can be useful to answering this question.  

![tweet](https://github.com/JMMoseley/THM-Writeups/blob/main/OhSINT/Images/BSSIDTweet.png)

The user has shared his BSSID (Basic service set identifier) in a tweet! If you don't know what to do with this information you can visit [Osint Curious Website](https://osintcurio.us/2019/01/15/tracking-all-the-wifi-things/) and read more about wigle.net. 

![wigle](https://github.com/JMMoseley/THM-Writeups/blob/main/OhSINT/Images/wiglescreenshot.pngg)

Using the wigle.net search, I find a purple circle pointing to the location and zoom in as far as I can to see the SSID.

![ssid](https://github.com/JMMoseley/THM-Writeups/blob/main/OhSINT/Images/ssid.png)

### 4. What is his personal email address?
Fortunately this and the question 5 answer was already given to us! Both can be found by going to the users GitHub account.

### 5. What site did you find his email address on?

![GitHub](https://github.com/JMMoseley/THM-Writeups/blob/main/OhSINT/Images/github.png)

### 6. Where has he gone on holiday?

I went back to Twitter and didn't find anything. So visited his blog one more time and found the location where he went on holiday.

![blogpost](https://github.com/JMMoseley/THM-Writeups/blob/main/OhSINT/Images/blogscreenshot.png)

### 7. What is this persons password?
While it is bad practice to write notes, specifically credentials in the source code, developers sometimes do this to leave comments for other people in their team. Not finding much else on the page, I take a look at the source code where I find a hidden (the font color is the same the background color) word that looks like it can be the password.  

![password](https://github.com/JMMoseley/THM-Writeups/blob/main/OhSINT/Images/password.png)

This is a great beginners OSINT challenge and it was a lot of fun doing it. I hope this is helpful!
