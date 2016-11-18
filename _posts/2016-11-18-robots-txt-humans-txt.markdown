---
layout: post
title:  "robots.txt and humans.txt"
date:   2016-11-18 03:37:06
tags:   [development, devops, web]
disqus: true
image:  "https://c1.staticflickr.com/5/4038/4492547207_0214fbb43b_b.jpg"
---

What does this strange title mean? And what could it possibly entail?

This post is part of an assignment in the course
["1DV022 -- Client-based Web Programming"][1dv022] at Linnaeus
University in Kalmar.

Internet courtesy and de-facto standards
----------------------------------------
This is yet another part of the ongoing assignment to explore static
site generators and a variety of concepts related to the web in general
and website creation in particular.

This time it is about some agreed upon, (defacto) standardization
and internet history.

robots.txt
==========

Overview
--------
According to [robotstxt.org][robotstxt], `robots.txt` can be
[described thusly][robotstxt-about]:

> ### In a nutshell
> Web site owners use the /robots.txt file to give instructions about
> their site to web robots; this is called The Robots Exclusion Protocol.

The file is used as a sort of configuration file for passer-by robots.
Using a special syntax, the website owner can specify which parts of
the website, I.E. what resources on the server, specified as paths;
that visiting robots are allowed to scan.

Alternative description by [robotstxt.org][robotstxt-about]:

> It works likes this: a robot wants to vists a Web site URL, say
> `http://www.example.com/welcome.html`. Before it does so, it firsts
> checks for `http://www.example.com/robots.txt`, and finds:
>
>     User-agent: *
>     Disallow: /
>
> The `"User-agent: *"` means this section applies to all robots.
> The `"Disallow: /"` tells the robot that it should not visit any
> pages on the site.

History
-------
And this is where the internet history comes in. The internet _used
to be much more friendly_ place. There were barely any users compared
to today, which means barely any malware. Users average skill level
were higher, most users had access through academia or employers.

Maybe robots were more courteous back in the 90's.
There is nothing stopping them from completely ignoring the `robots.txt` file.

Again, [robotstxt.org][robotstxt-about] writes:

> There are two important considerations when using `/robots.txt`:
>
> - robots can ignore your `/robots.txt`. Especially malware robots
>   that scan the web for security vulnerabilities, and email address
>   harvesters used by spammers will pay no attention.
> - the `/robots.txt` file is a publicly available file. Anyone can
>   see what sections of your server you don't want robots to use.
>   So don't try to use `/robots.txt` to hide information.

There are two historical descriptions:

* Original ["A Standard for Robot Exclusion"][robot-1994] document from 1994.
* Internet Draft specification ["A Method for Web Robots Control"][robot-1997] from 1997.
  (I just love these plain text _Request For Comments_ documents..)


Standardization
---------------
The `robots.txt` file is a _de-facto_ standard, I.E. it has come to be
accepted as a standard after having ["achieved a dominant position
by public acceptance or market forces"][wiki-defacto].

Additional references:

* [HTML 4.01 specification, Appendix B.4.1][html401]
* [Wikipedia - Robots Exclusion Standard][wiki-robots]


Also, see the [robotstxt.org][robotstxt-about] site for more information.



humans.txt
==========
This is a much newer idea than `robots.txt`. Similar in naming but not
in function. It seems like someone likes playing around with words ---
"well _I'm not_ a robot ..". Humans need a separate txt file.

The [initiative website][humanstxt] describes `humans.txt` as follows:

> ### What is humans.txt?
> It's an initiative for knowing the people behind a website.
> It's a TXT file that contains information about the different people
> who have contributed to building the website.

The choice of file format and name is motivated as follows:

> ### Why a TXT?
> Because it's something simple and fast to create. Because it's not
> intrusive with the code. More often than not, the owners of the site
> don't like the authors signing it; they claim that doing so may make
> the site less efficient. By adding a txt file, you can prove your
> authorship (not your property) in an external, fast, easy and
> accessible way.

And just like with `robots.txt`, there is no attempt at controlling
or enforcing how this is used. It is just a initiative that might catch
on and with time become a sort of standard, just like `robots.txt`.


[1dv022]: https://coursepress.lnu.se/kurs/klientbaserad-webbprogrammering/
[robotstxt]: http://www.robotstxt.org/
[robotstxt-about]: http://www.robotstxt.org/robotstxt.html
[wiki-defacto]: https://en.wikipedia.org/wiki/De_facto_standard
[robot-1994]: http://www.robotstxt.org/orig.html
[robot-1997]: http://www.robotstxt.org/norobots-rfc.txt
[html401]: http://www.w3.org/TR/html4/appendix/notes.html#h-B.4.1.1
[wiki-robots]: http://en.wikipedia.org/wiki/Robots.txt
[humanstxt]: http://humanstxt.org/

