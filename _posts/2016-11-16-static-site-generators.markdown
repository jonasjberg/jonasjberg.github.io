---
layout: post
title:  "Static Site Generators"
date:   2016-11-16 18:00:52
tags:   [development, jekyll, workflow, web]
disqus: true
---

This post is part of an assignment in the course
["1DV022 -- Client-based Web Programming"][1dv022] at Linnaeus
University in Kalmar.

Separating concerns
===================
One of many core concepts in programming and (software) engineering is
called [Separation of concerns][wiki-sepcon].

It is a important foundational design principle that boils down to
splitting big and/or complex problems into smaller more manageable
chunks --- "divide and conquer".  It then also follows that one should
strive to separate responsibilities and consequences for change.

Content should be concerned with only content, not presentation.

* The content should be _open to modification_ without having to worry
  about inadvertently modifying the presentation.
* Likewise, a change in the presentation should not change the content.
  The presentation should be able to _change without affecting the
  content_.

Advantages of separating style from content
-------------------------------------------
There are numerous advantages to keeping the _content_ separate from
the _style_. Especially when producing documents such as websites and
other literature. The author can concentrate on the content alone,
without having to think about formatting the text as it is entered. It
also makes for more __consistent styling and formatting__ of documents.

*More on this in an upcoming post ..*


Content, structure and presentation
-----------------------------------

### Markup
The most prominent markup language is surely `html` -- "HyperText
Markup Language". `html`-files contain the actual textual content
as well as a description of the contents semantic structure.
The author *marks up* the document with a special syntax that
separates different parts of the text and indicates "intent".

An example of this might be:

#### Raw text form:
This is the plain text, without additional information.

    My cat Gibson

    Gibson is:
    A cat
    Black

    I love my cat Gibson!

#### Raw text With added markup:
Markup adds semantic structure to the raw text.

{% highlight html %}
<title>My cat Gibson</title>

<list>
Gibson is:

<item>A cat</item>
<item>Black</item>
</list>

I <emphasis>love</emphasis> my cat Gibson!
{% endhighlight %}


### Stylesheets
Stylesheets is a standardized way of describing how the different elements
should be presented. This is a mapping of markup syntax to appearances,
for instance saying that  all headings should be some specific color.

This is an example stylesheet that describes how to display the title
`My cat Gibson` in the above markup:

{% highlight css %}
title {
    size: largest
    style: bold
    color: red
}

emphasis {
    style: cursive
}
{% endhighlight %}


Static Site Generators
======================
So, what are _static site generators_?
And what makes a website _static_?

A _static site generator_ takes some number of source files as input
and produces a website. All websites are transmitted as marked up text
(`html`), stylesheets (`css`) and possibly scripts (`JavaScript`).
These are the basic building blocks of all websites.

A site being _static_ means the web server that hosts the site
can deliver only pre-generated content. When a user clicks a link,
a page request is sent from the browser, to which the web server
serves a pre-rendered page. The available set of content is fixed --
there is no dynamic creation of documents prompted by user interaction.

### Advantages to static websites
This brings some advantages:

* __Simplicity__ -- the final website is made up by simple building
  blocks that are standardized and likely supported across platforms and
  browsers.
* __Security__ -- smaller attack vector. I.E. fewer potentially
  vulnerable services and systems reachable for clients. It is very
  difficult to leverage bugs in `html` and `css` to exploit systems..
* __Speed__ -- requires less bandwidth.  The static site generator can
  do various tricks to compress the generated files. Stylesheets can be
  concatenated with some smarts, etc.
* __Usability__
    * The content can be written in a form that is easier to handle
      than pure markup language. [Markdown][markdown] is a popular
      format for entering marked up plain text for use as input to
      static site generators.
    * Website sections can be extracted into modules for re-use, this
      makes it possible to make changes that affect multiple parts of
      the site with a single modification.
* __Programmability__ -- content and structure can be generated
  programmatically, following some defined logic.


### Disadvantages to static websites
The nature of static sites and static site generators makes them less
suitable for some use cases.
Advanced shopping and social sites like say `ebay` or `facebook` requires
a sophisticated content management system, among other things. Static
site generators are not suitable for this kind of heavy-weight corporate
sites with involved interactivity.


Generating static sites
-----------------------
The static site generator enables a natural way of authoring while
keeping content and style separate. The source material can be split
up over many files in a complex structure, while still keeping the
generatated website structure simple and compact.

The content is authored in your favorite text editor. The simple _markdown_
syntax adds markup to your text.
And we all know which is [the one true text editor][onetruetexteditor], right?


### Jekyll
There are __a lot__ of static site generators to choose from, just see
this [pretty comprehensive list][staticgenlist].
Among all these, [`Jekyll`][jekyll] stands out as a popular choice.
It is written and Ruby, is open source and integrates nicely with GitHub pages.

Jekyll can be configured to watch for changes to the site. When the markdown
source files are saved to disk, the entire site is rebuilt from scratch in
(hopefully) a couple of hundred milliseconds. This means that the website is
continously updated as the content is authored, giving a nice preview; like you
would get using "[WYSIWYG][wiki-wysiwyg]" editors.

This means adding content is very easy, everything is handled automatically by
`jekyll`. After having arrived at a good enough design, new content can be
added by simply creating text files in a directory.  Contrast this to manually
updating dozens of `html`-files and keeping track of a possibly complex
directory hierarchy to be mirrored on the server.

Jekyll also provides features for adding media content in various ways,
traditionally handled by _Content Management Systems_.
This is an [interesting read][cms-to-jekyll] about moving from a more
traditional design based on a _CMS_ to using `jekyll`.


Closing thoughts
----------------
This paired with your favourite version control system makes for a very
potent platform for developing websites.
The only real drawback is, just like with any other framework or tool;
as long as you work as the tool intends you to work, things mostly work
out. But _if_ (when) you need to add some unforeseen functionality,
you might have to go all the way -- grab the tool sourcecode and
implement whatever it is you must do in a fork.
Source is open and [available][jekyll-github]. However, `jekyll` is
flexible and very popular, countless plugins and extension
are available and so, most functionality already exists.

Jekyll paired with the free hosting provided by [GitHub pages][github-pages]
is a very popular blogging platform and I have no difficulty seeing why.

Continued reading
-----------------

* ["Why Static Website Generators Are The Next Big Thing" by Mathias Biilmann Christensen][biilmann]
* ["Static vs. Dynamic website design" by SpiderWriting Web Design][spiderwriting]
* ["How We Build CMS-Free Websites" by Dave Cole][cms-to-jekyll]





[1dv022]: https://coursepress.lnu.se/kurs/klientbaserad-webbprogrammering/
[wiki-sepcon]: https://en.wikipedia.org/wiki/Separation_of_concerns
[allincottrell]: http://dsv.su.se/polopoly_fs/1.125295.1361458482!/menu/standard/file/wp.htm
[proprietaryformats]: http://www.podval.org/~sds/data.html
[markdown]: https://daringfireball.net/projects/markdown/
[jekyll]: https://jekyllrb.com/
[jekyll-github]: https://github.com/jekyll/jekyll
[github-pages]: https://pages.github.com/
[cms-to-jekyll]: https://developmentseed.org/blog/2012/07/27/build-cms-free-websites/
[biilmann]: https://www.smashingmagazine.com/2015/11/modern-static-website-generators-next-big-thing/
[spiderwriting]: http://www.spiderwriting.co.uk/static-dynamic.php
[wiki-wysiwyg]: https://en.wikipedia.org/wiki/WYSIWYG
[onetruetexteditor]: https://www.sbf5.com/~cduan/technical/vi/
[staticgenlist]: https://www.staticgen.com/
