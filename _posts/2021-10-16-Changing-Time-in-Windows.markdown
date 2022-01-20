---
layout: post
title:  "Changing Time in Windows (Game Exploit)"
date:   2021-10-16 01:02:03 -0700
---
Had no internet multiple times for a week due to construction issues where they kept cutting the fiber line. 

Went to play a game I had been into lately. Deep Rock Galactic. There is a timer in the game for when available missions rotate. It is random and has different missions in different zones, different objectives, and modifiers.

<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\CTIW-1.webp" 
		alt="X"
	>
</picture>

Noticed the game mission timer was still active with no internet.
Restarted game. Noticed it was still active.

Wondered what if I change my system time by 30 minutes and open the mission selection screen?  
I was surprised that it worked ?!

The regular mission randomness seeds are based off of time regardless if you have internet or not. As long as you set the time to be the same you can essentially choose the missions you want to do. Instead of waiting for the randomness to occur. For example you can do a Double XP mission with a difficulty modifier for +130% XP and choose to play it whenever you want. My friends and I jokingly referred to this at "time traveling". "Can you time travel us to a 2XP mission".

<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\CTIW-2.webp" 
		alt="X"
	>
</picture>

As I used it more and more I googled how to change it with command line.
I made some simple bat files to easily set the time and reset it back to current time as well as fix applications that broke from the time change.

Script 1
```
:: sets time for Quick DRG XP Farm
date 10/16/2021
time 14:40:50
```

Script 2
```
:: This set of commands should resync time to be current date and time.
net restart w32time
w32tm /resync
:: This will restart Stream Deck to fix the crash due to time change.
taskkill /im StreamDeck.exe /f
start "" "C:\Program Files\Elgato\StreamDeck\StreamDeck.exe"
```

I did slowly discover changing system time breaks a lot of things too though. 
<br>For example:
* Elgato Stream Deck breaks due to logging.
* Reacting to messages in Teams with the built in Emojis like thumbs up ect.
* 2FA Login to Microsoft Office 365 SSOs
* Youtube
* Spotify
<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\CTIW-3.webp" 
		alt="Broken Spotify Picture 1"
	>
</picture>
<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\CTIW-4.webp" 
		alt="Broken Spotify Picture 2"
	>
</picture>


2022 Note: So in regards to the game exploit. My theory has expanded to thinking that the Spawning of Game Events, Spawning of Special Enemies, ect is all based off of a time seed for its randomness. Definitely isn't true random, but after a decent of time in the game it did take a very long time to put it together. So far can't pin it down exactly, but it is predicible enough that I can use it to me & my friends advantage instead of dealing with what we first thought was just pure chance.
