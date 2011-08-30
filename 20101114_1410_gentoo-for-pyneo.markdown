---
categories: Gentoo, Pyneo
date: 2010/11/14 14:10:00
title: Pyneo for Gentoo
---
Something I wanted to do for a while, but never actually got started: Get [pyneo](http://www.pyneo.org) supported in gentoo.
So I finally wrote some ebuilds, starting of course with *pyneod* and its dependencies *gsm0710muxd* as well as *python-pyneo*.
More to follow soon.

The packages are based on the 1.32 tag in pyneo's git and pretty much identical to upstream, with the exception of the initscripts.
My ebuilds replace them by proper gentoo-style initscripts that work well in openrc.

###How to use it
Using this overlay is easy.
Make sure you have layman installed, using the *git* USE-flag, and set up, e.g. as [described here](http://www.gentoo.org/proj/en/overlays/userguide.xml).
After that you just have to add this overlay using:

	layman -o "http://gitorious.org/tg/gentoo-pyneo/blobs/raw/master/overlay.xml" \
	-f -a pyneo

That's it!

Check it out on gitorious if you like!

[http://gitorious.org/tg/gentoo-pyneo](http://gitorious.org/tg/gentoo-pyneo)
