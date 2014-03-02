date: 2014-03-02 01:44:11
title: Blogofile -> Pelican
category: misc
tags: other

After running blogofile for *four* years (who knew it was that long with the little posting i've done :) and getting less done with it than I hoped, I finally decided to move on again.
The main reason is, that [Blogofile][3] is basically unmaintained and writing custom controllers was harder than it should be (and documentation clearly lacking).

So I looked around for alternatives and found surprisingly few that were interesting to me.
The requirements were:

 - simple static blog compiler
 - solid templating engine
 - python
 - markdown support

The only one that fit well was [Pelican][1] so I decided to give it a go.
Migrating was surprisingly straight forward and done in basically half a day (that includes understanding Pelican, porting the CSS, moving all posts over, and implementing every missing feature I used to have in Blogofile in the Pelican templates.

I'm not 100% happy, but so far Pelican seems nice enough, everything works (even better than before).
A few of the problems I have:

 - the design seems unnecessarily complicated, compared to blogofile
 - the error handling is quite poor, it is basically impossible to get useful error messages
 - the documentation could be better (still much better than Blogofile though)
 - the performance is a bit poor (but acceptable)

However, there are also positive points:

 - development seems quite active
 - jinja2 is a nice templating engine
 - there are a lot of modules
 - powerful features
 - AGPL licensed

So all in all I'm happy with my choice, lets see if it stays that way.
To get started, I wrote a tiny deployment tool (in zsh script), that might be useful for others - as everything on here, it is of course [publicly available][2].

Custom modules are planned next.

By the way, in case you're wondering: yes, it looks pretty much exactly like the old site, the CSS was easy to port.
Also, I finally fixed the mobile view, it is now as fully functional as the desktop site.

[1]: https://github.com/getpelican/ "Pelican"
[2]: https://gitorious.org/tg/blog-layout/source/ba811653829c6c79de40508c40ac34484b71d5d8:pelitool.zsh "pelitool.zsh"
[3]: http://www.blogofile.com/ "Blogofile"
