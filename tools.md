---
layout: page
title: Tools I Like
---
<details><summary>Windows Tools</summary><blockquote>
<dl>
	<dt>Windows Subsystem for Linux (WSL):</dt>
		<dd>An easy way to run Linux tools on Windows 10.</dd>
		<dd>Though it isn't a fully fledged Linux enviorment so not everything works. For example nmap won't work inside the WSL.</dd>
		<dd>
{% highlight console %}
To install:
Enable the windows feature "Windows Subsystem for Linux"
Then install a Linux Distro from the Windows Store.{% endhighlight%}
		</dd>
	<dt><a href="https://chocolatey.org/">Chocolatey</a>:</dt>
		<dd>Chocolatey is an easier,faster, and more secure way to install, uninstall, and upgrade software packages.</dd>
		<dd>It downloads software from the source. Checks the hashes to ensure it wasn't tampered with. Then does a full silent install. You can also do a silient upgrade of all installed packages with one command.</dd>	
</dl>
  
	<details><summary>Programs I like to manage with Chocolately</summary><blockquote>
	<dl>
	<dt>Web Browsers:</dt>
		<dd>Chromium and Firefox depending on what I need:</dd>
		<dd>{% highlight console %} choco install chromium {% endhighlight%}</dd> 
		<dd>{% highlight console %} choco install firefox {% endhighlight%}</dd>
	
	<dt>Draw.io</dt>
		<dd>Free Open Source Tool for setting up diagrams and flow charts.</dd>
		<dd>It is also a web app on their website <a href="https://draw.io">https://draw.io</a></dd>
		<dd>{% highlight console %} choco install drawio {% endhighlight%}</dd>
		
	<dt>VLC Media Player</dt>
		<dd>Plays most music and video files without the need for additional codecs</dd>
		<dd>{% highlight console %} choco install vlc {% endhighlight%}</dd>
	
	<dt>MP3 Tag</dt>	
		<dd>Tool to add/edit the tags on mp3 files such as Album Art, Artist, Title, Track #, CD #, ect.</dd>
		<dd>{% highlight console %} choco install mp3tag {% endhighlight%}</dd>
			
	<dt>KeePass 2</dt>
		<dd>Free Open Source password manager that encrypts your passwords into a portable kdbx file.</dd>
		<dd>I also like some plugins like keeagent as you can store your ssh keys as attachments in the database. Keeagent can also load the key for your ssh sessions.</dd>
		
		<dd>
		{% highlight console %}
choco install keepass 
choco install keepass-plugin-keeagent  
choco install keepass-plugin-favicon {% endhighlight%}</dd>
	
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
	</dl>
</blockquote></details>
<br>
<br>
I recommend installing these programs as you normally would as they auto-update often and work better under normal install conditions.
<dt><a href="https://nmap.org/download.html">nmap</a></dt>
	<dd>network/port scanner </dd>
	<dd>Basically a GUI version of nmap with some easy to use options</dd>
	<dd>It also includes a pcap driver which allows other programs to view the network traffic</dd>
<dt><a href="https://www.balena.io/etcher/">BalenaEtcher</a></dt>
	<dd>ISO / Image installer that works for for multiple OS, but it works better than Rufus when install Rasbian on Raspberry Pi SD Cards.</dd>
<dt><a href="https://store.steampowered.com/about/">Steam</a></dt>
	<dd>Popular game client for connecting with friends and playing games on PC</dd>
<dt><a href="https://discordapp.com/">Discord</a></dt>
	<dd>Popular chat client for connecting communities and friends.</dd>

<dt><a href="https://www.wireshark.org/download.html">Wireshark</a></dt>
	<dd>Don't use winpcap use nmap's better packet capture driver.</dd>
	<dd>Network packet analyzer to view captured network traffic.</dd>
<dt><a href="https://notepad-plus-plus.org/downloads/">Notepad++ 32bit</a></dt>
	<dd>Versitle notepad with extra features and plugins. Install the 32 bit version if you want to be able to use plugins.</dd>
<dt><a href="https://www.spotify.com/us/download/">Spotify</a></dt>
	<dd>Recommend the installer over the UWP Windows 10 version as it works better and has less control latency issues.</dd>
<br>
<br>
Portable Programs

<dt><a href="https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html">PuTTY</a></dt>
	<dd>Remote Terminal/Shell for SSH, Telnet, Serial. </dd>
<dt><a href="https://winscp.net/eng/downloads.php">WinSCP</a></dt>
	<dd>Remote File Transfer GUI for FTP, SSH, SCP. </dd>
<dt><a href="https://winsshterm.blogspot.com/">WinSSHTerm</a></dt>
	<dd>Easily manage multiple putty windows, run scripts, and integrate PuTTY and WinSCP.</dd>
<dt><a href="https://www.pendrivelinux.com/yumi-multiboot-usb-creator/">YUMI</a></dt>
	<dd>Allows you to setup multiple boot images on a single usb device.</dd>
<dt><a href="http://tftpd32.jounin.net/tftpd32_download.html">TFTPD32</a></dt>
	<dd>Portable TFTP Server that also includes DHCP and a few other tools</dd>	
	
</blockquote></details>

<details><summary>Android Tools</summary><blockquote>
<dl>
	<dt><a href ="https://play.google.com/store/apps/details?id=us.lindanrandy.cidrcalculator&hl=en_US">CIDR Calculator by Randy McEoin</a></dt>
		<dd>An easy to use subnet calculator that works with ipv4 and ipv6.</dd>
		<dd>Shows the network range,# of usuable hosts, netmask, wildcard, and even the binary bits.</dd>
	<dt><a href ="https://play.google.com/store/apps/details?id=keepass2android.keepass2android&hl=en_US">KeePass2Android Password Safe by Croco Apps</a></dt>
		<dd>Password Manager that works with the encrypted .kdbx files</dd>
	<dt><a href="https://github.com/TeamNewPipe/NewPipe/releases">NewPipe</a></dt>
		<dd>Youtube/Video player that can play audio in the background/screen lock. Along with other free features</dd>
		<dd>Not available on the Google Play store, you have to manually install the .APK file </dd>
</dl>   
</blockquote></details>

<details><summary>Linux Tools</summary><blockquote>
<dl>
	<dt>nmap</dt>
		<dd>A powerful network/port scanner</dd>
		<dd>{% highlight console %} apt install nmap {% endhighlight%}</dd>
	<dt>grep</dt>
		<dd>A built-in tool to find patterns/text within files or output.</dd>
</dl>   

</blockquote></details>