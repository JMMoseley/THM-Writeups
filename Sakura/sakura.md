![banner](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/banner.png)

# [SAKURA](https://tryhackme.com/room/sakura)  - created by [OSINT DOJO]((https://www.osintdojo.com))

This room was created to test different OSINT techniques and take us through a sample OSINT investigation in which we will identify a number of identifiers and other information to help catch a cybercriminal. Answers will be obtained using passive OSINT techniques.
Task five gives you the option to get answers from the Dark Web, however, I attempted this and the Deep Paste links didn't work. 

Task 1 include a basic intro. So lets start with task 2. 

## Task 2 - TIP-OFF 

OSINT Dojo have found themselves victims of a cyber-attack. While there were not indicators of compromise or damage, there was an image left behind. 

![sakurapwnedletter](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/sakurapwnedletter.jpg)

### What username does the attacker go by?

Upon clicking on the link to download the image we can see that the link takes us to a GitHub page containing an image which has binary numbers as the background. I originally thought there could be a message here, or maybe more information in the metadata for this image. I was not able to do a quick save of this image to analyze it with Exiftool. So instead I looked at the source code for the page.

Going through the page source we can see that there is a file path for the image with the user name we are looking for. 

![sourcecode](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/sourcecode.png)

## Task 3 - Recon

The attacker has reused this username through social media, this will help us gather more information on them. 

### What is the full email address used by the attacker?

Firstly, use the username we found in the first task and do a simple google search. Tools like Sherlock or Spiderfoot can also be used to look up associated accounts with this username.
The google search gives us some interesting results. First we see that user has a GitHub account. Going to GitHub we can see they have several repositories, one of them is called PGP. Surprisingly this repository contains a PGP key. This can be useful information since PGP is used for signing, encrypting and decrypting texts, emails, etc.  

I downloaded the repo from GitHub and then unzipped the file.
We can obtain the email address by using gpg

![PublicKey](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/gpg.png)

Here we can find the user's email address.

### What is the attacker's full real name?

In the same search results we see a LinkedIn page for what appears to be the user. That name matches the first name of user who owns the GitHub and also the username from our first task, which appears in the URL bar.

![LinkedIn](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/linkedin.png)

## Task 4 - UVEIL

The cybercriminal is on to us. They have already started updating their GitHub and "deleting/editing" information to throw us off. 

GitHub maintains history of commits, including edits, deletions, or insertions. This information can be utilized to trace some of the attacker's cryptocurrency transactions.

### What cryptocurrency does the attacker own a cryptocurrency wallet for?

Looking through the user's repositories we can see that they have a few crypto related repos. After looking through those I found some interesting information on their ETH repository. 
Upon clicking on the repo, we can see there is only a mining script file. Nothing much to see here. However, if we click on commits we can see the user's commit history and here we can discover a cryptocurrency wallet address and also the website of the cryptocurrency mining pool. 

![ETH](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/eth.png)

### What is the attacker's cryptocurrency wallet address?

We can gather this information from the above image. 

### What mining pool did the attacker receive payments from on January 23, 2021 UTC?

For this we need to check the transaction history on an Ethereum blockchain explorer.
Looking at various options, I found that the best one to use for this task is Ethplorer (https://ethplorer.io/).
Enter the users wallet address and search. 
If we navigate to the page with the January transactions we can find the mining pool the attacker used.

![Ethexplorer](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/ethexplorer.png)


### What other cryptocurrency did the attacker exchange with using their cryptocurrency wallet?

Right on the same page where we found the mining pool received payments from, we can see the other type of cryptocurrency used by the attacker.

![othercrypto](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/othercrypto.png)

## Task 5 - TAUNT

The cybercriminal has gone as far as to taunt the OSINT Dojo on Twitter for their efforts of gathering info on them, but it appears they used a different username than the one we previously found. Here is a screenshot of the message:

![taunt](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/taunt.jpg)

### What is the attacker's current Twitter handle?

If we do a quick google search for the twitter handle AikoAbe3 we can see the attackers current handle listed under the results. We can confirm by going into that profile and their first tweet mentions their old Twitter handle.

![aikoabe3](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/aikoabe3.png)

### What is the URL for the location where the attacker saved their WiFi  SSIDs and passwords?

We will use leads from the Twitter account to the Dark Web and other platforms to find additional information.

If we go to the user's Twitter we can find a Tweet where the user mentions Access Points (APs)
which contains an image that has an MD5 hash and text referring to WiFi and passwords. 

![APs Tweet](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/APsTweet.jpg)

The user also mentions their lack of concern about someone finding their APs on the Dark Web, and hints that in order to do so, we will have to do a DEEP search and find where they PASTEd them. 
They are refering to a paste site called Deep Paste. 

There is a hint here. This is the task I mentioned at the beginning, were deep paste was unavailable. 

Here is a list of the Deep Web Pastebin Links https://deepweblinks.net/pastebin/ in case you want to try to use the Dark Web to answer this question. 

![deeppaste](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/deeppaste.jpg)

Using the image provided by OSINT Dojo, we can see the URL for the location where the attacker save their WiFi SSIDs and passwords. However in order to view this specific paste, you must complete this URL by adding the MD5 hash to the end of the URL.

### What is the BSSID for the attacker's Home WiFi?

If you don't know how you can find the BSSID (Basic service set identifier) visit [Osint Curious Website](https://osintcurio.us/2019/01/15/tracking-all-the-wifi-things/) and read more about wigle.net. 

An account (free) is needed for wigle.net. Doing an advanced search and using information we found on the deep paste site, we can search for the network names listed here. 

Go to wigle.net, click on view, then click on advanced search and enter the user's network names. 

![bssidwigle](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/bssidwigle.png)

Here we can see the user's BSSID, and more information that might be relevant for the next task so don't close Wigle. 

## Task 6 - HOMEBOUND

Based on the user's tweets we can gather they are on their way home. Look at the photos to determine their route back home. 

### What airport is closest to the location the attacker shared a photo from prior to getting on their flight?

Their twitter account shows a retweet before their layover. And this image is of cherry blossoms in Bethesda. The attacker also took pictures of cherry blossoms before going home and in the background you can see the Washington monument. 
Look up some airports close to Bethesda to answer this question. 

![retweet](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/retweet.jpg)

![washingtonmonument](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/washigntonmonument.jpg)

### What airport did the attacker have their last layover in?

![finallayover](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/finallayover.jpg)

The attacker clearly states this is their last layover. We can search for Japan Airlines Sakura Lounge on google. Results will yield information on where the lounges are located. We can also do a reverse image search. Yandex does not yield anything, but a google reverse image search reveals similar images of where the cybercriminal took this picture. We can indeed confirm that there is a lounge located near the final layover.


### What lake can be seen in the map shared by the attacker as they were on their final flight home?

![lake](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/lake.jpg)

For image search I prefer to use Yandex before Google since the two often return different images. I simply saved the image and searched and the first result looks very similar to the picture in the attackers tweet. 

![reverseimagelake](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/reverseimagelake.jpg)

clicking on it we can determine this lake is located in Japan.

![reverseimageresult](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/reverseimageresult.jpg)

looking at google maps and zooming in we can find the lake.

![lakeinjapan](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/googlemapslake.png)

### What city does the attacker likely consider "home"?

We know our attacker lives in Japan from the information we have gathered so far through our investigation. We can piece this all together or we can use the information we found on the AP (Access Point) image and use Wigle to find the location of the home WiFi. In fact all Wi-Fi locations point to the same city or locations very close to it. 

![home wifi](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/DK1F-G.jpg.png)

![Buffalo-G-19D0-1](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/Buffalo-G-19D0-1.jpg.png)

![hirosaki_Free_Wi-Fi](https://github.com/JMMoseley/THM-Writeups/blob/main/Sakura/images/Hirosaki_free_wi-fi.jpg.png)

Passive OSINT is usually the first step in any information gathering campaign. As you can see this room demonstrates how much information can be gathered without having to interact with a target. We went from a single image left in a cyberattack that revealed a username, to being able to find the attackers home. I really enjoyed solving this challenge, I hope it was helpful if you were stuck on this room.
