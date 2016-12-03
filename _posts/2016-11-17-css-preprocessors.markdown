---
layout: post
title:  "On CSS preprocessors"
date:   2016-11-17 22:01:49
tags:   [development, devops, web]
disqus: true
---


This post is part of an assignment in the course
["1DV022 -- Client-based Web Programming"][1dv022] at Linnaeus
University in Kalmar.

First of all, keep in mind I have all but a couple of weeks of
experience in web development. These are the thoughts of a _n00b_.

Modern Web Development
======================
A couple of the courses I'm taking cover developing websites and
applications that run in a browser.

First, some thoughts on developing content for the web.

Tools
-----
So much has been written about this already. Oh my, there are [so many
tools][mozilla-webapp] in use.  These _tools_ are programs, frameworks,
languages --- abstractions built upon abstractions; with seemingly infinite
recursion, to make development faster and easier.

This blog posts sums up the experience pretty well, I think:
["How it feels to learn JavaScript in 2016" by Jose Aguinaga][medium-learn-js-2016]

The insane amount of tools and frameworks available in the web development
world makes navigating around them difficult.

Tradeoffs
---------
[Some might say][muratori-quality] webapps like Gmail shouldn't be as
buggy and take so long to load. [Some might say][muratori-quality]
sending _plain text_ over the internet is a problem solved way back in
the 1970s. But even with contemporary computing power, much of modern
software performs __very badly__.

[Casey argues][muratori-quality] that _code quality_ isn't prioritized
-- beating the competition to market with a "good enough" product is
the primary concern.

Insanely slow and often buggy code seems to be considered a worthwhile
sacrifice for ease and speed of development. Casey Muratori says this
very eloquently [here][muratori-quality].

I think he has makes some good points and argues for them very well.
Even if you disagree, it is still [worth a listen][muratori-quality].


That said
---------
Getting to know the modern web development workflow and methodologies
is *very interesting* and worthwhile. Even though I have no interest
in pursuing a career doing web development, the web is unavoidable at
this point.
Even as an electronics engineer, basic knowledge of scripting
languages, HTML and CSS can help improve throughput. At the very least,
the ability to maintain a strong online presence has become very
important when hunting for employment..


CSS Pre-Processors
==================
It is said that programmers should strive to be lazy, meaning one should
be cautious of ones own methods and tools, use the engineering mindset
at all times. Avoid spending time on trivial, repetitive and
time-consuming tasks, the engineer will have the computer do the work.

Problem solving
---------------
I write small scripts in Bash and Python daily to do various tasks.
Why use the "find and replace" function in your text editor ten times
to substitute a word in ten different text files? It takes too long and
is _manual labour_, computers excel at doing the same thing repeatedly.

Instead, I'd probably use a one-liner like this:

{% highlight bash %}
find . -type f -name "*.txt" -exec sed -i 's/OLD/NEW/g' '{}' \;
{% endhighlight %}

This one-liner does recursive search and replace, all files in the
current directory with filenames ending with `*.txt` get any words
matching `OLD` replaced with `NEW`.

Natural extensions
------------------
One might argue that the insane amount of tools and frameworks are a
direct consequence of the will to improve ones own tools.

This post is part of an assignment in [one of the courses][1dv022] I'm taking.
The instructions jokingly suggest writing our own CSS pre-processor --
it probably wouldn't be as difficult as one might think, nor as
far-fetched.

The Bash one-liner above does recursive search and replace; likely
suitable functionality in a pre-processor, think variables in SASS.
Granted, most popular CSS pre-processors are very sophisticated and
does more than simple pattern-matching replacements.

But my point is that the tools are a natural extension of underlying
languages. And if CSS pre-processors wasn't a thing yet and my day job
involved editing a lot of CSS-files, I'd probably start collecting
useful snippets of simple code. With time and refinement, these simple
snippets might evolve into the start of a very own pre-processor.

So, my points are these:

1. Smart programmers are bound to write tools because they are lazy
   and/or engineers (have the engineering mindset)
2. Tools have characteristics -- these fall somewhere along a linear
   axis with endpoints "good" and "bad", depending on context.
3. Use of tools comes with context-dependent costs.
4. Modern web development practices _might not_ have been developed
   with a overarching mission and obligation to produce performant,
   high quality code. Not saying it won't, just that it _might_ not.


First impressions
=================
This blog uses the [Sass CSS pre-processor][sass]. Sass is

> Sass is the most mature, stable, and powerful professional grade CSS
> extension language in the world.

and apparently also

> CSS with superpowers

And it does solve a lot of problems. As a programmer, working with plain
CSS gets annoying very fast. There are no variables or expressions,
which means doing a simple change to the layout like changing the
text color, means replacing a dozen or so `yellow` with `green`.

This is error-prone and repetitious. SASS solves this with variables,
so that one can define the text color only once in a variable that is
referenced throughout the site.

SASS also introduces expressions. These are very useful for the same
reason --- instead of manually calculating constants with relative sizes,
calculations can be done with expressions. For instance, one might
define a base text size to have some numeric constant. All other text
sizes for headings, sub-headings, sub-sub-headings, etc., can then
be calculated from the base using scalars.

{% highlight sass %}
$font-size-base:          16px;
$font-size-small:         $font-size-base * 0.875;      // 14
$font-size-medium:        $font-size-base * 1.125;      // 18
$font-size-big:           $font-size-base * 1.25;       // 20
$font-size-bigger:        $font-size-base * 1.625;      // 26
$font-size-huge:          $font-size-base * 2;          // 32
$font-size-insane:        $font-size-base * 2,625;      // 42
{% endhighlight %}

These features are not exclusive to SASS but common to most CSS
pre-processors.


Pros and cons
-------------
As with everything else, there are pros and cons:

### Pros

* __Ease of development__
    * All kinds of "[syntactic sugar][wiki-syntactic-sugar]".
    * Less repetition -- variables and other means of abstraction
      enables encapsulation of concepts for later reuse.
    * Simpler calculation -- evaluation of expressions with variable
      arithmetic, as well as other expressions means less error-prone,
      manual work.

* __Maintainability__
    * Again, the added "[syntactic sugar][wiki-syntactic-sugar]" can
      help improve human comprehension.
    * Modularizing by splitting into multiple files.
        * __Code re-use__ -- common parts can be extracted into separate
          files for re-use across multiple projects.
        * __Collaboration__ -- version control systems often handle multiple
          smaller files better than one very big file. Also, solving
          merge conflicts in small files seems easier somehow..
        * __Scale__ -- huge websites means huge source files and
          splitting limits file sizes, both on disk and monitor space.

* __"Compiled" result__
    * The final source files that are used in production are generated
      by some kind of compiler, which means their structure and contents
      can be controlled in a separate process.
    * Multiple files and above points must not *necessarily* mean poor
      performance or increased bandwidth requirements -- the "compiler"
      can be modified to counteract such problems.

### Cons

* __Debugging__
    * The code you write is different from what the browser renders.
      This can make debugging a bit more difficult, but there are
      [solutions][sass-sourcemaps] to this problem.
    * Line-numbers in the browser traceback do not match the line-numbers
      in the source files, as per above.

* __Complexity__
    * Requires tools to compile the source files to plain CSS.
    * Site must be rebuilt in order to see changes. Risk becoming very slow for
      big projects with a lot of dependencies.

* __Compilation__
    * Resulting CSS-files could be smaller and more optimized.
      Compiler might do the very best thing 99% of the time but then
      again, it might not.
    * Requires trust that the pre-processor does what is needed for the
      project. What if some feature is missing or the generated CSS is messed
      up? Get the pre-processor source code and dig in..


Conclusions
===========
Programmers write tools because they are programmers.

The amount of tools and frameworks available for use in web development is
staggering.

Working solely with plain html and CSS to produce modern websites to would be
insane. There is no practical alternatives -- learn to love the tools.



*(.. I do not enjoy web development ..)*



[1dv022]: https://coursepress.lnu.se/kurs/klientbaserad-webbprogrammering/
[mozilla-webapp]: https://developer.mozilla.org/en-US/Apps/Fundamentals/Modern_web_app_architecture
[muratori-quality]: https://www.youtube.com/watch?v=6azav9sXK_4
[1dv022]: https://coursepress.lnu.se/kurs/klientbaserad-webbprogrammering/
[sass]: http://sass-lang.com/
[sass-sourcemaps]: http://thesassway.com/intermediate/using-source-maps-with-sass
[medium-learn-js-2016]: https://medium.com/@jjperezaguinaga/how-it-feels-to-learn-javascript-in-2016-d3a717dd577f#.758uh588b
[wiki-syntactic-sugar]: https://en.wikipedia.org/wiki/Syntactic_sugar
