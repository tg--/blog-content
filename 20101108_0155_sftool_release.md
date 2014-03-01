tags: projects
category: projects
date: 2010-11-08 01:55:00
title: sftool - initial release


Today I pushed my *sftool* into git.

It doesn't do much yet, except decrypting SandForces PKG firmware archives.
Not much more to be said here, just check it out on my projects page.

As you can probably see on the *TODO*, my next step for sftool is chipset detection, which means, that I would want to identify the chipset of the SandForce based drive and find the matching firmware file in the decrypted archive.
This is far from trivial, but I could use help from every sandforce owner who also has a windows-copy:

SandForces ssdupdate.exe tool creates *two* tempfiles during its runtime (both in the directory you run it from): *sfpkgtmp* and *sfpkgfwtmp*

The first one is created initially after loading of the package file, which works using wine, the second one is supposedly created after you select the drive you want to update, which unfortunately doesn't work in wine.

If you want to help, send my the exact model of your SandForce based drive and the *sfpkgfwtmp* file (less than 1 MByte).
You have to copy the file before you close the ssdupdate.exe tool because it cleans up its tempfiles afterwards.

I'd appreciate any help.

Initially I tried to do this project in the [OCZ forum](http://www.ocztechnologyforum.com/forum/showthread.php?79272-Flashing-SandForce-based-drives-on-Linux-a-research-project) where I hoped to get some help and mainly input, unfortunately OCZ shut this down before I had any code.
No hard feelings, they didn't even delete my useror my topic/posts, and I can understand that they don't want any reversing work done in their forum.
It wasn't really the goal to get anything from OCZ anyways, I just hoped to find some other interested people or at least users who were willing to help. Unfortunately that wasn't the case and there seemed to be no interest at all and I got no input whatsoever. :-(
