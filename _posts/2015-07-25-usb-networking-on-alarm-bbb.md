---
layout: post
title: "ArchLinuxARM on BeagleBone Black: getting network working over USB"
---

As written in title, this post will be about setting up a working USB connection
for [ArchLinuxARM](http://archlinuxarm.org) (a port of the magnificent
[ArchLinux](https://www.archlinux.org) for the ARM architecture).
This is made for this kind of setup:

* a shared DHCP connection through NetworkManager (can be adapted to everything else though)
* a *BeagleBoneBlack* connected by mini-USB to the computer.

With this tutorial you will have a working shared network between the *BeagleBoneBlack*
and your computer,
with included dynamic IP resolution (no more *ssh IP_HERE*).

Some thoughts:

* I'll say when commands have to be done on the *host* (see: your computer/laptop),
else they have to be done on the client (the *BeagleBoneBlack*).
* In a theoric way, this tutorial should be fine for any **ArchLinuxARM** device;
just pay a bit more of attention.
* I assume that the users reading this tutorial are a bit experienced (else *GTFO*);
also, the commands with before a *$*
will be commands that can be given as users, the ones with *!* should be given
by the user *root*.

## Let's do this
So, these are the steps:

- Install ***ArchLinuxARM*** (from now on **ALARM**) on your *BeagleBoneBlack*;
for this, I just suggest the
[official tutorial](http://archlinuxarm.org/platforms/armv7/ti/beaglebone-black).
For the following part of this tutorial, I assume you've installed your **ALARM**
(on MicroSD or on eMMC is the same).

- From your *host*, share connection to your *BeagleBoneBoard*;
I did this by connecting the device using an Ethernet cable plus an USB for power.
Also, I allowed sharing connection through Ethernet with *NetworkManager*
  * install *dnsmasq*, as it will allow shared networking through NetworkManager
  * open *nm-connection-editor*
  * Suggested: create a specific connection for the *BeagleBoneBlack* with *nm-connection-editor*
  * under IPv4 settings set "*Shared*"

- I had then to use *nmap* on the *host* to find out the IP
  * go on NetworkManager
  * find out the IP of the shared Ethernet network (*e.g. 10.42.0.1*)
  * find the actual IP of the *BeagleBoardBlack* by inspecting the network, doing something like:
{% highlight bash %}
$ nmap 10.42.0.1/24
# Here comes the output
Starting Nmap 6.47 ( http://nmap.org ) at 2015-07-24 17:21 CEST
Nmap scan report for 10.42.0.1
Host is up (0.00064s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE
53/tcp open  domain
# Here it is!
Nmap scan report for 10.42.0.143
Host is up (0.00056s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh # See, SSH port is open
Nmap done: 256 IP addresses (2 hosts up) scanned in 2.56 seconds
{% endhighlight %}

- Actually, connect from the *host* to your device with **SSH**
{% highlight bash %}
$ ssh root@10.42.0.143 # Use the IP found in the step before, user 'root' password 'root'
{% endhighlight %}

- In order to work with just the USB cable, you need to download the *gadget-deadbeef-dhcp* package;
the package was meant to enable connections through USB, I made the *-dhcp* version to have dynamic IP
(we won't have problem with it later). You can get it with a:
{% highlight bash %}
$ yaourt -S gadget-deadbeef-dhcp
{% endhighlight %}
Else, you will have to build it:
{% highlight bash %}
! pacman -S base base-devel wget # Let's have all installed
$ wget https://aur4.archlinux.org/cgit/aur.git/snapshot/gadget-deadbeef-dhcp.tar.gz
$ tar xf gadget-deadbeef-dhcp.tar.gz
$ cd gadget-deadbeef-dhcp
$ makepkg -srci # Builds without dependencies problems, clean up the temporary files and install
# If you've problems, use 'pacman -U' as root
{% endhighlight %}
**Notice**: people that want it to work even with *Windows* have to install
the *gadget-deadbeef-legacy-dhcp* package, as the one above uses a driver which
is not (*still*) supported from **BeagleBoard** official *Windows* drivers; so,
just follow the steps above, replacing *gadget-deadbeef-dhcp* with *gadget-deadbeef-legacy-dhcp*.

**PRO TIP**: I had to reinstall the official **BeagleBoard** drivers, which can
be found [here](http://beagleboard.org/getting-started#step2). I had problems as
*Windows 8.1* didn't allow me to install *unsigned* drivers; so, if you get to
the last step of drivers installation and you get red crosses (*error in installation*)
and you don't know why, try reinstalling after doing
[this](http://www.howtogeek.com/167723/how-to-disable-driver-signature-verification-on-64-bit-windows-8.1-so-that-you-can-install-unsigned-drivers/).

- Now we have to set up things for hostname resolution. Well'use *Samba* for this.
It can be used for many more things, but in this case we'll use just its ***NetBIOS*** ability.
So, get *Samba* and enable the *NetBIOS* daemon:
{% highlight bash %}
! pacman -S samba
! cp /etc/samba/smb.conf.default /etc/samba/smb.conf
! systemctl enable nmbd
! systemctl start nmbd
{% endhighlight %}

- On the *host*, enable *NetBIOS* name resolution by adding *wins* to the */etc/nsswitch.conf* file.
It will look like this:
{% highlight bash %}
$ cat /etc/nsswitch.conf 
...
hosts: files wins dns myhostname # See? We added 'wins' 
...
{% endhighlight %}

## And now?
Now, just connect with a
{% highlight bash %}
$ ssh alarm # Assuming that you've not changed the BeagleBoneBlack hostname
{% endhighlight %}
No more fuss for looking for IP, setting things or else.
This tutorial is a bit long, but I hope it can be useful to someone. Cheers.
