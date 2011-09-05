---
categories: Other
date: 2011/09/05 18:30:00
title: Trust issues (and the web)
---

The last couple of days, a company named [DigiNotar](http://en.wikipedia.org/wiki/DigiNotar) was in the news for issueing fake SSL certificates. I don't need and want to go into details, but what was clear before, has now officially been proven big time: The whole trust concept of SSL certificates and with it a corner stone of http security does not work and thus is completely worthless.
The sad thing is, that this is the _only_ http/web security system supported on a large scale to this day.

Overall the concept of trusting a hand full of companies out of good will is just _stupid_.
Each and every one of them is very susceptible to single hackers or small groups of hackers, not to mention foreign agencies and more importantly local agencies with proper funding or even a "legal" way to mess with certificates.

So, what is a solution that works? Learn from filesharing.
To this day a lot of filesharing networks have been put down due to the SPOF nature they share with the CA companies.
A single target which can compromise the whole network and system.
What followed was decentralization - and with so many other systems (from network architecture over source code management and storage systems) that prove how good this works, this clearly is the way to go.

So what's out there to accomplish this? Sadly: nothing that works out-of-the-box and/or everywhere.
But there are some concepts:

 - [Web Of Trust](http://www.mywot.com/), closely related to GPG/PGP
 - [Convergence](http://convergence.io/), a firefox plugin to allow a completely decentralized web of trust

Sadly, all of those come with some effort and are not available for every browser, let alone on every machine.
I will evaluate these and probably other solutions in the next time, and report back.
