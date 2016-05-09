---
layout: post
title: YouTube + HTML5 = PROFIT
---

*Everybody loves YouTube, doesn't it*? I love this service too.

I see lots of videos from it and I'm really satisfied with this service.

So, free candies and hugs for everybody, yuppie...
(Notice: you can skip to the **TL;DR** part at the end of the page.
**PRO TIP**: you can search for it in your browser.)

## But...

Yeah, bad news here. It uses *Adobe's* ***Flash Player***.
The plugin that has just been used for *flash games* and Youtube.

About the first of them, I can still remember some epic ones, as
[Burrito Bison Revenge](http://www.kongregate.com/games/JuicyBeast/burrito-bison-revenge)
and [Robot Unicorn Attack: Heavy Metal](http://games.adultswim.com/robot-unicorn-attack-heavy-metal-twitchy-online-game.html).

For Youtube... well, it's for Youtube.

## So what...?

Actually, as you should know, Linux has *outdated Flash plugin*
(**11.2**, when the upstream one is **11.7**) that is stable but... well,
*it's not updated*, fine?

Apart from this, on my main OS ([Antergos](http://antergos.com), an
[ArchLinux](http://archlinux.org) with lots of goodies in it and a fully working
desktop manager) I've no video thumbnail when shifting the player cursor. And no
 default *hardware accelleration*. Yup. (But read below for some juice.)
Also, even on Windows I've some problems with hardware accelleration (With my
Intel Graphics, I've some *hardware decoding* issues on some formats, as **480p**).

### SPOILER: Nerd stuff ahead... more then usual, yes. If you're not interested, skip to next paragraph.
Thanks to [Rinat Ibragimov](https://github.com/i-rinat/), it's possible to use
an updated version of Flash even on Linux; thanks to his hard work, now we have
avaible a *PPAPI-to-NPAPI conversion plugin* that allows to use the
**PPAPI Chrome** plugin on Firefox.
If you're interested, take a look [here](https://github.com/i-rinat/freshplayerplugin),
while you can track hardware decoding specific stuff and progress
[here](https://github.com/i-rinat/freshplayerplugin/issues/24).
This awesome developer also developed the awesome
[libvdpau-va-gl](https://github.com/i-rinat/libvdpau-va-gl), that allows to use
**VA-API** as a *VDPAU backend* for hardware accelleration.
(As Flash *just* supports **VDPAU** for hardware accelleration... So many
facepalms for me.).
*Translation for human mortals*:
***you use VA-API for VDPAU accelleration = hardware accelleration for Flash on Intel graphics***.
[Here](http://www.webupd8.org/2013/09/adobe-flash-player-hardware.html) you've
installation tutorial for *Ubuntu*.
Instead, for installing **libvdpau-va-gl** on *ArchLinux* you could do something
in a shell like this:
{% highlight bash %}
# Installing required packages
sudo pacman -S libvdpau-va-gl libva-intel-driver flashplugin
# Enabling HardWare Accelleration for Flash plugin
sudo sed -i 's/#Enable/Enable/' /etc/adobe/mms.cfg
# Making avaible the driver through environment variables
echo "export VDPAU_DRIVER=va_gl" >> .bashrc
# Activate it for the actual session
export VDPAU_DRIVER=va_gl
{% endhighlight %}
**Notice**: in this way it'll work just for the user which exports the variable;
to make it default for the whole system, you should create a
***/etc/profile.d/vdpau_vaapi.sh***
script with this commands:
{% highlight sh %}
#!/bin/sh
export VDPAU_DRIVER=va_gl
{% endhighlight %}
This will do the trick.

## The solution is... HTML5!
As you should know, YouTube has made avaible an **HTML5 player** avaible
[here](https://www.youtube.com/html5).
This make the YouTube experience free from the problems given by Flash Player.
Also, it has *no problem* in playing *all the videos* avaible with Flash, it has
**60 FPS videos support** (*and Flash does not*) and uses
**hardware accelleration** (*it should...* I can't be sure about it, as no
related source code is avaible, but it *should* use *hardware accellerated*
***HTML5 canvas***).

## But... #2
Actually, it fully works just on *Chromium/Google Chrome*...
![Fully works on ArchLinux Chromium...]({{ site.baseurl }}public/2015-04-13/chromium.png)
While on *Firefox*...
![Doh #1.]({{ site.baseurl }}public/2015-04-13/firefox-archlinux.png)
And on *Windows Firefox*
![Doh #2.]({{ site.baseurl }}public/2015-04-13/firefox-windows.png)

## The final solution (TL;DR)

In order to have ***a fully working HTML5 YouTube player in Firefox***, you just
have to open the internal configuration
[here (Remember, just for  Firefox)](about:config), press the big "Yeah, I'll be
a fine boy" button (*can't remember the proper English text, sorry*) set the
flags shown below as suggested (**PRO TIP**: you can use the built-in search bar):
{% highlight yaml %}
media.mediasource.enabled: true
media.mediasource.mp4.enabled: true
media.mediasource.webm.enabled: true
media.mediasource.youtubeonly: true

media.fragmented-mp4.enabled: true
media.fragmented-mp4.exposed: true
media.fragmented-mp4.ffmpeg.enabled: true
media.fragmented-mp4.gmp.enabled: true
media.fragmented-mp4.use-blank-decoder: false
{% endhighlight %}

And finally...
*Firefox on ArchLinux*
![Yes #1.]({{ site.baseurl }}public/2015-04-13/firefox-archlinux-working.png)
And on *Firefox on Windows*.
![Yes #2.]({{ site.baseurl }}public/2015-04-13/firefox-windows-working.png)

## The end
Well, that's all folks for now.
If it's interesting, show some love and press the share button I've put below
and thank you for reading up to this point.
See you guys!
