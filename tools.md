---
layout: page
title: Tools I Like
---

While this isn't a full exhaustive list. It is mostly tools that aren't built in or may not widely be known about. 

<details><summary>Multi-Platform Tools:</summary><blockquote>
<dl>
	<dt><a href="https://nmap.org/">nmap</a></dt>
	<dd>	Network Mapper is a free and open source utility for network discovery and security auditing.
	</dd>
	
	<dt><a href="https://www.isc.org/download/#BIND">dig</a></dt>
	<dd>	Command-line tool developed by BIND for querying DNS nameservers.
	</dd>
	
	<dt><a href="https://www.diagrams.net/">Diagrams.net</a></dt>
		<dd>	(Formerly known as Draw.io)
			<br>Free Open-Source Tool for designing diagrams and flow charts.
			<br>You can use the web app on their website without install nor signup.
		</dd>
	
</dl>   

</blockquote></details>


<details><summary>Windows Tools:</summary><blockquote>
<dl>
	<dt><a href="https://chocolatey.org/">Chocolatey</a>:</dt>
		<dd>	Chocolatey is a package manager that makes it easier to install
				and upgrade software.
			<br>It downloads software from the source. Checks the hashes to ensure
				it wasn't tampered with.
			<br>Then does a full silent install.
			<br>You can also do a silent upgrade of all installed packages with one command.
		</dd>	
</dl>
  
<details><summary>Programs I like to manage with Chocolatey:</summary><blockquote>
	<dl>
	<dt>Web Browsers:</dt>
		<dd>
			Chromium and Firefox depending on what I need:
		</dd>
		<dd>
			{% highlight console %} choco install chromium {% endhighlight%}
		</dd>
		<dd>
			{% highlight console %} choco install firefox {% endhighlight%}
		</dd>
	
	<dt>Diagrams.net (Formerly Draw.io)</dt>
		<dd>Free Open Source Tool for designing diagrams and flow charts.
			<br>You can use the web app on their website without install nor signup.
		</dd>	
		<dd>{% highlight console %} choco install drawio {% endhighlight%}</dd>
		
	<dt>VLC Media Player</dt>
		<dd>Plays most music and video files without the need for additional codecs</dd>
		<dd>{% highlight console %} choco install vlc {% endhighlight%}</dd>
	
	<dt>MP3 Tag</dt>	
		<dd>Tool to add/edit the tags on mp3 files such as Album Art, Artist, Title, Track #, CD #, ect.</dd>
		<dd>{% highlight console %} choco install mp3tag {% endhighlight%}</dd>
					
	<dt>KeePass 2</dt>
		<dd>
				Free Open-Source password manager.
			<br>It encrypts your passwords into a database that consists of only one file that can be transferred from one computer to another easily.
			<br><del>
				I also like some plugins like keeagent as you can store your ssh keys as attachments in the database. Keeagent can also load the key for your ssh sessions.
				</del>
			<br>Note: I no longer like using agents such as keeagent or pagent as it auto submits keys which is a security issue
				as well as can cause logins to auto-fail.
		</dd>
		
		<dd>{% highlight console %}choco install keepass{% endhighlight%}</dd>
	
	<dt>7Zip</dt>
		<dd>Tool to pack and unpack archives and compressed files of multiple formats such as rar,zip,tar and 7z.</dd>
		<dd>{% highlight console %} choco install 7zip {% endhighlight%}</dd>
	
	<dt>Greenshot</dt>
		<dd>Better replacement for snipping tool that has a built in annotation/edit tool for Highlighting, obscuring sensitive info, numbering steps, drawing arrows ect. It also allows easy export to clipboard, word, outlook, imgur, or save the file.</dd>
		<dd>{% highlight console %} choco install greenshot {% endhighlight%}</dd>
	
	<dt>Flux (f.lux)</dt>
		<dd>Make the screen easier on your eyes by reducing blue light at sunset and at night to help not interfere with your circadium rhythm.</dd>
		<dd>{% highlight console %} choco install flux {% endhighlight%}</dd>
	
	<dt>Paint.Net (Paint dot net)</dt>
		<dd>Free photo editor that supports layers, magic wand selector, and some light editing.</dd>
		<dd>{% highlight console %} choco install paint.net {% endhighlight%}</dd>
	
	<dt>OnTopReplica</dt>
		<dd>	Picture in Picture overlay for any application window.
			<br>Also supports transparency.</dd>
		<dd>{% highlight console %}choco install ontopreplica {% endhighlight%}</dd>	
		
	<dt>4k Video Downloader</dt>
		<dd>	Download videos from youtube.
		</dd>
		<dd>{% highlight console %}choco install 4k-video-downloader{% endhighlight%}</dd>	

	<dt>Audacity</dt>
		<dd>	Free Open-Source Audio Editor
		</dd>
		<dd>{% highlight console %}choco install audacity{% endhighlight%}</dd>
		
		
		
		
		
		
	</dl>
</blockquote></details>
<br>
<br>

<div><span style="color: rgb(181, 232, 83);">I recommend installing these programs manually:</span><br></div>
<dt><a href="https://www.microsoft.com/store/productId/9N0DX20HK701">Windows Terminal</a></dt>
	<dd>It is a more modern CLI terminal with tabs. It can also be customized.
	<br>It supports cmd, powershell, WSL.
</dd>
	
<dt><a href="https://docs.microsoft.com/en-us/sysinternals/downloads/">Sysinternals Utilities</a></dt>
	<dd>Tons of useful tools for Windows directly from Microsoft.
	<br>My favorites are Whois and Autoruns.
</dd>
	
<dt><a href="https://www.balena.io/etcher/">BalenaEtcher</a></dt>
	<dd>ISO / Image installer that works for for multiple OS. For me it works better than Rufus when installing Rasbian on Raspberry Pi SD Cards.</dd>
<dt><a href="https://store.steampowered.com/about/">Steam</a></dt>
	<dd>Popular game client for connecting with friends and playing games on PC</dd>
<dt><a href="https://discordapp.com/">Discord</a></dt>
	<dd>Popular chat client for connecting communities and friends.</dd>

<dt><a href="https://www.wireshark.org/download.html">Wireshark</a></dt>
	<dd>Network packet analyzer to view captured network traffic.</dd>
<dt><a href="https://notepad-plus-plus.org/downloads/">Notepad++ 32bit</a></dt>
	<dd>Versatile notepad with extra features and plugins. Install the 32 bit version if you want to be able to use plugins.</dd>
<dt><a href="https://www.spotify.com/us/download/">Spotify</a></dt>
	<dd>Recommend using the UWP Windows Store version if you want to add/sync tons of local files of media. Otherwise I'd recommend the regular non-UWP Windows Store version as it seems to have less lag on the controls.</dd>
<br>
<br>

<div><span style="color: rgb(181, 232, 83);">Portable Programs:</span><br></div>

<dt><a href="https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html">PuTTY</a></dt>
	<dd>	Remote Terminal/Shell for SSH, Telnet, Serial. 
		<br>Note: I will probably remove this recommendation in the future.
		<br>once I find a good modern alternative for Serial / Telnet.
	</dd>
<dt><a href="https://winscp.net/eng/downloads.php">WinSCP</a></dt>
	<dd>Remote File Transfer GUI for FTP, SSH, SCP. </dd>
<dt><a href="https://winsshterm.blogspot.com/">WinSSHTerm</a></dt>
	<dd>Easily manage multiple putty windows, run scripts, and integrate PuTTY and WinSCP.</dd>
<dt><a href="https://www.pendrivelinux.com/yumi-multiboot-usb-creator/">YUMI</a></dt>
	<dd>Allows you to setup multiple boot images on a single usb device.</dd>
<dt><a href="http://tftpd32.jounin.net/tftpd32_download.html">TFTPD32</a></dt>
	<dd>Portable TFTP Server that also includes DHCP and a few other tools</dd>	
	
</blockquote></details>


<details><summary>Android Tools:</summary><blockquote>
<dl>
	<dt><a href ="https://play.google.com/store/apps/details?id=us.lindanrandy.cidrcalculator&hl=en_US">CIDR Calculator by Randy McEoin</a></dt>
		<dd>An easy to use subnet calculator that works with ipv4 and ipv6.</dd>
		<dd>Shows the network range,# of useable hosts, netmask, wildcard, and even the binary bits.</dd>
	<dt><a href ="https://play.google.com/store/apps/details?id=keepass2android.keepass2android&hl=en_US">KeePass2Android Password Safe by Croco Apps</a></dt>
		<dd>Password Manager that works with the encrypted .kdbx files</dd>
	<dt><a href="https://github.com/TeamNewPipe/NewPipe/releases">NewPipe</a></dt>
		<dd>Youtube/Video player that can play audio in the background/screen lock. Along with other free features</dd>
		<dd>Not available on the Google Play store, you have to manually install the .APK file </dd>
</dl>   
</blockquote></details>


<details><summary>Linux Tools:</summary><blockquote>
<dl>
	<dt><a href="https://github.com/traviscross/mtr">My Traceroute (mtr)</a></dt>
	<dd>A cleaner formatted traceroute</dd>


</dl>   

</blockquote></details>


<details><summary>Tools I no longer use:</summary><blockquote>
<dl>
	<dt>Windows Subsystem for Linux (WSL):</dt>
	<dd>	An easy way to run some Linux tools on Windows 10.
		<br>Though it is not a fully fledged Linux environment so not everything works.
		<br>For example nmap won't work inside the WSL.
		<br>nmap does work on WSL Version 2 but not all features as it doesn't have Layer 2 network access.
		<br>I switched to just accessing a full linux virtual machine over SSH.
	</dd>
	
	<dd> {% highlight console %}
To install:
Enable the windows feature "Windows Subsystem for Linux"
Then install a Linux Distro from the Windows Store.{% endhighlight%}
	</dd>
	
</dl>   

</blockquote></details>

	
		
<!--Template for adding section, Tools, and descriptions
<details><summary>SECTION HERE</summary><blockquote>
<dl>
	<dt><a href="https://LINK">TITLE OF TOOL</a></dt>
	<dd>STUFF ABOUT TITLE
		<br>MORE STUFF ABOUT TITLE
	</dd>
	


	
</dl>
-->
