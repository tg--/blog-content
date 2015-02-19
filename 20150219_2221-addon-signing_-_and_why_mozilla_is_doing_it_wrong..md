date: 2015-02-19 22:21:25
title: Addon-Signing - and why Mozilla is doing it wrong.
category: other
tags: firefox

While it seems to have been in development for a while, it only recently got public coverage: Mozilla is planning to introduce addon-signing in firefox.
First of all: I welcome that.

However, as beneficial signed addons can be, mozilla is still doing it wrong, and I'll elaborate on how so, and why.

What does it mean?
==================

The idea behind signing addons is, that a trusted party can verify that the addon is what it claims to be, and - in a stretch - does not misbehave.
For this, the addon is signed with a cryptographic key that cannot be faked and the person/organization who does the signing guarantees for the addon with their name.
This certainly isn't a new concept, it is very sound and used in many places. For example: windows device drivers are signed by Microsoft, Linux kernel source releases are signed by Linus Torvalds, debian packages are signed by debian developers, and so on.

How does it work in firefox?
============================

If signed addons are introduced in firefox, it means, that addons *need* to be signed so firefox will load them.
I have not looked in detail on how mozilla will do that, but the easiest way to implement this (and thus most likely what they will use) is to ship a public key with firefox which matches the private key they will use to sign the addons.
A more complex solution would be to use certificates which has some advantages at the cost of more complexity - they might also do this instead.
Firefox will then check every addons against this key or certificate chain to verify that mozilla has signed it with their private key.
This way, the browser will be certain, that the addon has been checked by mozilla and that they vouch for its authenticity and - to a degree - function.

Why do we need this - and why mozilla wants it
==============================================

First of all, personally I think that signing infrastructure is always a good thing, at least if done right.
There are lots of reasons to sign your software, foremost to ensure it isn't changed by some other party without your knowledge.
Mozilla has their own reasons.
For many years it has been common that PC vendors and 3rd party software vendors ship browser addons with PCs or their software.
The most common variant is browser toolbars. Nobody really wants those, they are ugly, don't provide any value and take a lot of your valuable screen real-estate.
This means if you start your browser, it will look terrible. It might also be slow and show annoying adverts. This reflects back on Mozilla as a organization. If your mozilla browser looks terrible when you start it, you might think it is a terrible browser, to no fault of their own.
Even more important, Mozilla's fiercest competitor is google with their "Chrome" browser, which also fights off that stuff, and currently more effectively.
So if you start Firefox and it looks and feels terrible, due to unwanted addons - and you start Chrome and it is just fine, due to the lack of unwanted addons, it is obvious, that you would rather use Chrome.
Additionally, there are even worse addons; some might steal your data, insert advertisements into web pages, and compromise your online banking.
Addons are powerful!

Long story short: Mozilla has all the reason to want this, and you as a user might too!

Why mozilla is doing it wrong
=============================

What I haven't mentioned until now is, that addon signing will be _mandatory_.
This means, that firefox will not load unsigned addons.
Again, this is reasonable.
If unsigned addons can be loaded, the system is effectively subverted.
The problem starts with mozillas implementation of the signature check.
Only addons signed by _Mozilla_ are loaded.
There is no way sign your own addons, nor is there a way for a person/developer you greatly trust to sign an addon for you.
This means the only trusted entity is Mozilla.
You do not have the option to load unsigned addons anyway, neither do you have the option to disable the signing check, nor do you have the option to install another key to check against.
This is where we have a problem: Mozilla has now become the gatekeeper of your browser.
This means no longer are you the party who decides what addons to install, you are the party who depends on Mozilla so they may allow you to install an addon.
Clearly, this goes against anything mozilla stands for, most importantly: freedom.

The limitation applies mainy to official Firefox releases, which are branded with the Firefox name and use the Firefox logo. Mozilla supposedly will offer a "developer" branch which does not have those limitations. Other branded versions (for example Debian's Iceweasel, or real forks like Pale Moon) are not affected.
This means Mozilla is valuing their "Firefox" brand higher than the users freedoms, which is what you would expect of a corporation.
However, Firefox is supposed to be developed by the Firefox community under the roof of the Mozilla foundation - not the Mozilla corporation!

What mozilla needs to do
========================

The solution is simple.

The only thing mozilla needs to change is to allow the user (or system administrator) to install their own keys.
This is trivial to implement, poses no risk, and it is really the obvious solution.

That's what *really* worries me: the solution is so obvious, that at no point Mozilla couldn't and shouldn't have thought of it.

To counter the one valid argument against allowing user supplied keys: it can be used to undermine the security of the system.
This is true to a degree, but only if the key is supplied at the profile level (i.e. in ~/.mozilla respectively %APPDATA%\Mozilla).
Again, the solution is obvious: use the firefox install location for this. On Linux this is some place in /usr, on windows it is in %PROGRAMFILES%.
If these locations are compromised, the whole browser (and very likely the whole system!) are compromised anyway.
The developers behind the addon signing see it the same way, so again, I'm really worried why they didn't support user supplied signing keys in these locations from the start.
