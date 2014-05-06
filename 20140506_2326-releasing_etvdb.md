date: 2014-05-06 23:26:43
title: Releasing etvdb
category: projects
tags: projects, enlightenment, gentoo



After having used it for quite a while, I feel it is time to announce the release of *etvdb*.

etvdb libary
------------

etvdb is a high-level C library frontend to [The TVDB][1].
It is based on Eina and Ecore of the Enlightenment Foundation Libraries and easy to use in EFL apps, but can just as easily be used in other programs.
It does not depend on a mainloop.
Additionally it uses libcurl, so the dependencies are quite small.

The current release is version 0.3.0 and you can get it from my [Github Repo][3].
The API documentation is available on [my site][2].

Right now it only has a synchronous API, but I do plan to add a asynchronous one at some point in the future.
This means, that you'll have to run it in a thread for interactive applications for now.

etvdb command line tool
-----------------------

In addition to the library, there is etvdb_cli, which is basically a command line frontend to The TVDB based on etvdb.
It has currently 3 basic usage modes:

* CSV-like output

	In this mode you can get a CSV-like output that you can write to a file.
	This is the default mode.

* query mode

	In query mode you can query single properties from TV show episodes.
	For example:

	``
	etvdb -n Futurama -s 1 -e 1 -q ename
	Space Pilot 3000
	``

* rename mode
	
	In this mode you can pass files to etvdb and they will be renamed.
	It supports templates so you can rename it however you'd like.
	It can run without user input (in scripts e.g.) or interactive.

Try it out, it is easy to use. Just run etvdb --help to see all the options.
It currently only depends on libetvdb itself.
You can get the current 0.1.0 release from my [Github Repo][4].

Gentoo users can get ebuilds from my [Gentoo Overlay][5].

Check it out and let me know what you think, patches and comments welcome!


[1]: http://thetvdb.com
[2]: //gstaedtner.net/etvdb/doc
[3]: https://github.com/tg--/etvdb
[4]: https://github.com/tg--/etvdb_cli
[5]: https://github.com/tg--/gentoo-tg
