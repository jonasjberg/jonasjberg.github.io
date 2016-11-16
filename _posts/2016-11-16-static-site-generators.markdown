---
layout: post
title:  "Static Site Generators"
date:   2016-11-16 18:00:52
tags:   [development, jekyll, meta, workflow]
---

Separating concerns
===================
One of many core concepts in programming and (software) engineering is
called [Separation of concerns][wiki-sepcon].

It is a important foundational design principle that boils down to
splitting big and/or complex problems into smaller more manageable
chunks --- "divide and conquer".  It also states that one should
strive to separate responsibilities and consequences for change.

Content should describe content, not presentation.
Likewise, a change in the presentation should not change the content.

Advantages of separating style from content
-------------------------------------------
There are numerous advantages to keeping the _content_ separate from
the _style_. Especially when producing documents such as websites and
other literature. The author can concentrate on the content alone,
without having to think about formatting the text as it is entered. It
also makes for more __consistent styling and formatting__ of documents.


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


Advantages to static websites
-----------------------------
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


Content, structure and presentation
-----------------------------------

### Markup
Most prominent markup language is surely `html`. `html`-files contain
the actual textual content as well as a description of the contents
semantic structure.
The author *marks up* the document with a special syntax that separates
different parts of the text and indicates "intent".

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


Generating static sites
-----------------------
The static site generator enables a natural way of authoring while
keeping the content and style separate.

### Jekyll
The content is authored in your favorite text editor with markdown
syntax. The static site generator [`jekyll`][jekyll] can be
configured to watch for changes to the site. Any time the markdown
source files are saved to disk, the entire site is rebuilt from
scratch in (hopefully) a couple of hundred milliseconds.

This means adding content is very easy, everything is handled
automatically by `jekyll`. After having arrived at a good enough design,
new content can be added by simply creating text files in a directory.
Contrast this to manually updating dozens of `html`-files and keeping
track of a possibly complex directory hierarchy to be mirrored on the
server.
This used to be done with a _Content Management System_. [Interesting
read][cms-to-jekyll] about moving from a _CMS_ to using `jekyll`.

### Closing thoughts
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


[wiki-sepcon]: https://en.wikipedia.org/wiki/Separation_of_concerns
[allincottrell]: http://dsv.su.se/polopoly_fs/1.125295.1361458482!/menu/standard/file/wp.htm
[proprietaryformats]: http://www.podval.org/~sds/data.html
[markdown]: https://daringfireball.net/projects/markdown/
[jekyll]: https://jekyllrb.com/
[jekyll-github]: https://github.com/jekyll/jekyll
[github-pages]: https://pages.github.com/
[cms-to-jekyll]: https://developmentseed.org/blog/2012/07/27/build-cms-free-websites/
