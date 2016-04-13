date: 2016-04-13 20:32:33
title: Connecting to an HTTP/2-enabled webserver using Firefox
category: misc
tags: firefox nginx

Even though this website (and the other sites hosted on this server) isn't very sensitive, I try to maintain the highest possible security by using up-to-date and secure software, as well as strong ciphers for the connection.
After all, it's nobodys business what you read here, but yours.

I also try to use new technology whenever possible, so it makes sense, that I offer HTTP/2 connections.


Unfortunately, it turns out that combining the two isn't always as easy as it should be.
My nginx cipher suite is configured as follows:
`ssl_ciphers ECDH+AESGCM:ECDH+AES256:!AES128:!DH:!RSA:!3DES:!aNULL:!MD5:!DSS;`

This is generally considered close to ideal security (let me know if you disagree), so I figured it should work with HTTP/2 - which emphasizes security greatly - without any problems.

The issue
=========

Unfortunately, I was wrong. After enabling HTTP/2 in nginx, Firefox fails to connect to the server.
Even worse, it did not display an error message, log an error to the console, or show any issue in the network debugger.

It turns out, that I missed, that the HTTP/2 standard has a hard requirement on AES-128 support, specifically `TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256`[1].
Apparently firefox does not yet support AES-256 in GCM, which should also allow a connection.
Partially at fault is my not-very-explicit specification of ciphers in the nginx config, because it is non-obvious, that ECDH+AESGCM will be only AES-256 if AES-128 is disabled.

The fix
=======

The issue can be easily fixed by re-enabling AES-128, for example as follows:
`ssl_ciphers ECDH+AESGCM:ECDH+AES256:ECDH+AES128:!DH:!RSA:!3DES:!aNULL:!MD5:!DSS;`

Now Firefox can connect just fine, even if that means a slight downgrade in SSLLabs' SSL Server Test.
It will still get an A+ though and AES-128 certainly isn't problematic by itself.

I filed a bug at Mozilla anyway, because I think Firefox should at least allow you to see what's going wrong without running Wireshark[2].
Hopefully this article will save you some time should you run into the same issue.

[1]: https://tools.ietf.org/html/rfc7540#section-9.2.2
[2]: https://bugzilla.mozilla.org/show_bug.cgi?id=1264379
