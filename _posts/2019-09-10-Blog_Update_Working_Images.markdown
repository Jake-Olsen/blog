---
layout: post
title:  "Blog Update: The site has working images now."
date:   2019-09-10 01:02:03 -0700
---
I got images working now on the site. They were working locally, but when I made it live on GitHub pages it was a bit frustrating getting the links and images to use the correct URL. I couldn't find good documentation on the project name vs the base URL. I ended up updating the "_config.yml" file on these lines:
```
  url: "https://jake-olsen.github.io/"

baseurl: /blog
```

Then updating the images in my posts to this code:

{% raw %}
<img src="{{site.url}}{{site.baseurl}}\assets\images\filename.webp>
{% endraw %}


site.baseurl was just a guess since I didn't see on the [Jekyll documentation]  or the other posts I saw while searching comments on GitHub where other people were having a similar problem. 

After playing around with trying to optimize images for the web. I would resize them to about the size they would appear on the blog. Somewhere around 900 or 1000 pixels wide.  Strangely the file sizes got bigger. I just left the original screenshots since they were the smallest file size. The photos of the cisco lab are a bit bigger, so shrinking the overall size did significantly help the page load faster. Some of them were still large file sizes. Google recommends saving them as webp, but Paint.NET doesn't have an option to save images as webp. 

I went to go look for software on Chocolatey since they usually have pretty good software, and I found the webp program from google surprisingly it is command line only, but easy to use.
https://developers.google.com/speed/webp/docs/using

<details>
  <summary> I'll just open a command prompt as an admin and install webp.</summary>
{% highlight bat %}
C:\WINDOWS\system32>choco install webp -y
Chocolatey v0.10.15
Installing the following packages:
webp
By installing you accept licenses for the packages.
Progress: Downloading webp 1.0.0... 100%

webp v1.0.0 [Approved]
webp package files install completed. Performing other installation steps.
Installing 64 bit version
Extracting C:\ProgramData\chocolatey\lib\webp\tools\webp_x64.zip to C:\ProgramData\chocolatey\lib\webp\tools...
C:\ProgramData\chocolatey\lib\webp\tools
Environment Vars (like PATH) have changed. Close/reopen your shell to
 see the changes (or in powershell/cmd.exe just type `refreshenv`).
 ShimGen has successfully created a shim for anim_diff.exe
 ShimGen has successfully created a shim for cwebp.exe
 ShimGen has successfully created a shim for dwebp.exe
 ShimGen has successfully created a shim for get_disto.exe
 ShimGen has successfully created a shim for gif2webp.exe
 ShimGen has successfully created a shim for img2webp.exe
 ShimGen has successfully created a shim for vwebp.exe
 ShimGen has successfully created a shim for vwebp_sdl.exe
 ShimGen has successfully created a shim for webpinfo.exe
 ShimGen has successfully created a shim for webpmux.exe
 ShimGen has successfully created a shim for webp_quality.exe
 The install of webp was successful.
  Software installed to 'C:\ProgramData\chocolatey\lib\webp\tools'

Chocolatey installed 1/1 packages.
 See the log for details (C:\ProgramData\chocolatey\logs\chocolatey.log).

C:\WINDOWS\system32>refreshenv
Refreshing environment variables from registry for cmd.exe. Please wait...Finished..
C:\WINDOWS\system32>
{% endhighlight %}
</details>

Then I just used the default example from google to optimize the photo.

{% highlight bat %}
C:\WINDOWS\system32> cd C:\Users\Jake_\blog\assets\images
C:\Users\Jake_\blog\assets\images>cwebp -q 80 image.png -o image.webp
{% endhighlight %}

Which worked out very well. It took the image from 4000+ KB down to 99KB!

I wanted to try it out on a few other images to see if I could get better quality and have a smaller size.
I cropped it inside of Paint.NET for it to be easier. Then I had to trial and error a bit to get the command correctly.
{% highlight bat %}
cwebp -resize 1000 0 -q 80 croppedimage.png -o croppedimage.webp
{% endhighlight %}


<br>Original File before Crop 3,000KB .jpg 
<br>File after crop 12,000KB .png
<br>File after cwebp resize and optimization 80KB .webp

Some images don't decrease their file size, so I just leave them as their original png if the webp format ends up being larger.

Test it locally before uploading by serving locally
{% highlight bat %}
C:\Users\Jake_\blog>bundle exec jekyll serve
Server address: http://127.0.0.1:4000/blog/
{% endhighlight %}

Then viewing http://127.0.0.1:4000/blog/ in a web browser and make sure the updates are working as expected before uploading.

[Jekyll documentation]: https://jekyllrb.com/docs/variables/