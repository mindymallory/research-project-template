---
layout: post
title: "Android: Preventing Gallery thumbnails creation"
---

I'm really having an hard time in this period (***exams, duh***) but considering
the fact I'm having more views that I ever expected,
I'm gonna drop something useful here.

Don't worry, *long posts* with ***many informatics technical stuff*** are
already in background.
I'm thinking about a **server-related tutorial series**, I suppose people will
enjoy.

Anyways, back to the topic.

## What do you mean in the title?
Let's be honest, **Android OS** can't be perfect. We already know this.
But there's lot of customization avaible, which makes it my favourite mobile OS
(*for now... But I think/hope this won't change*).
Anyways, I can detect with [SD Maid](https://play.google.com/store/apps/details?id=eu.thedarken.sdm)
about ***1.8 GB*** of *Stock Gallery thumbnails*. And that's a big bunch of crap.
(**PRO TIP**: visit [darken's website](http://darken.eu/) or take a look to his
[G+](https://plus.google.com/u/0/116634499773478773276/))

## Why this happens?
Actually, Android just tries to speed-up the Gallery (in my case, **Google+ Photos**
app) by creating a local preview that can be loaded really fast by gallery apps...
However, this creates the *junk* I told before.

## Any fixes?
Yeah, the title would be different if it wasn't like this.
However, this requires a mobile with a ***custom recovery***
(*like [ClockWorkMod](http://clockworkmod.com/rommanager) or [TWRP](http://teamw.in/Devices/)*)
and some *Android/Linux OS* knowledge.
(At least, try to understand what follows next.)

## Let's go!
The idea is to make impossible to create new thumbnails; so, why not deleting the
thumbnails and make the folder to be impossible to access?
Exactly, this will make the trick.
Now, reboot your phone in *recovery mode* and open your shell (in *TWRP* there's
one that can be runned in recovery, else connect your phone to your PC and use
an *adb shell*... check that you're using **root** with *whoami*)

{% highlight bash %}
cd /sdcard # Should exist as fallback... anyways, getting in your main memory folder
cd DCIM # Entering photos folder, where thumbnails are
rm -f .thumbnails/* # Removing all thumbnails
chmod 000 .thumbnails # Making the thumbnail folder not accessible anymore
{% endhighlight %}

Done! Now the thumbnails in the Gallery app will be generated on the fly... and you will have some free memory now.
That's all for now, folks!
Wait for the *tutorial series*.
