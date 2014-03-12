tags: gentoo, enlightenment
category: personal
date: 2011-11-10 00:30:00
title: Moving to systemd



I'm back from Sweden, and while I was away, [ELCE](https://events.linuxfoundation.org/events/embedded-linux-conference-europe) was held.
The nice people from Free Electrons luckily put up [all the conference videos in webm format](http://free-electrons.com/blog/elce-2011-videos/), so whoever missed it can catch up.
One of the first videos I watched was [Integrating systemd: Booting Userspace in Less Than 1 Second](http://free-electrons.com/pub/video/2011/elce/elce-2011-kooi-integrating-systemd.webm), held by Koen Kooi, who I remembered from the time I used Openembedded on Openmoko devices.

Some know that I like to show off my neat little Thinkpad x200s for its boot time; so far under 5 seconds (from bootloader to X) using Gentoo, OpenRC, and Enlightenment.
I wanted to try systemd for a while but never really was in the mood to do the actual work. The video inspired me to actually give it a try now.

Installing systemd is incredibly straight-forward, just read the gentoo-wiki articles and make sure you have your "init scripts" (or .service files in systemd jargon) ready.
Enough talk, just let me finish with this: I was utterly impressed how well systemd works and I'm looking forward to it replacing all other init systems currently out there (including OpenRC which I actually liked).
But look for yourself:

<video width="100%" controls="controls">
 <source src="//gstaedtner.net/videos/linux/x200s_fastboot.webm" type="video/webm" />
 Your browser does not support the video tag.
</video>

###Some stats:
	Linux version 3.1  
	systemd version 37  
	udev 175

	Linux -> systemd: ~1s  
	systemd -> e17: ~1s  
	e17 -> ready: ~1.5s


If you have questions or need config files, just ping me via mail/jabber/irc.
