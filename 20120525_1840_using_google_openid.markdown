---
categories: other
date: 2012/05/25 18:40:00
title: Using a google account as OpenID
---

You might have an google account, and encountered various websites and services who allow you to log in with for example a Facebook account, a Google account or an OpenID account.

As usual, Facebook wants (or rather forces) you to use their services exclusively, so if a Facebook login is the only possibility, you're screwed.

Google however tends to use open systems, and they do this for logins, too.
Even if a website requires you to log in using your Google account,
it is using Googles OpenID services.
Unfortunately you're still screwed: if the site supports the Google account excuisively,
it will have the Google OpenID URI hardcoded.

Now for the good news: if a site offers OpenID login directly,
you cannot only use any OpenID provider you'd like, you can also use your Google account.
Unfortunately, it is (imho) less than obvious - Google doesn't provide a short, practical URI for this purpose.
The Google OpenID URI is https://www.google.com/accounts/o8/id
Not terrible, yet inconvenient, because you'll have to type it in if there is no huge "Google Login" button.

To make it easier, I first tried various link-shorteners, but this usually doesn't work,
because redirections are usually not possible at OpenID logins.
Also, while google allows you to use your "Google Profile" for html redirections,
this requires you to have a Google+ account, which you might not want to have.

However, there is a solid possibility, using your own domain: Just do a hard rewrite.

In [nginx](http://www.nginx.org) this could be done like this:

``
server {
	listen [::]:80;
	server_name id.example.tld;
	rewrite ^ https://www.google.com/accounts/o8/id permanent;
}
``

Now just type id.example.tld in your OpenID login field, an Google will log you in.
In other webservers it should work in a similar fashion.
