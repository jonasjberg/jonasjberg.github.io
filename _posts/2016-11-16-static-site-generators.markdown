---
layout: post
title:  "Static Site Generators"
date:   2016-11-16 18:00:52
tags:   [development, jekyll, meta]
---

So, what are _static site generators_? What is a _static_ site?

# Static Site Generators
Simply put, a static site generator is a program that creates webpages.
All webpages are transmitted over the internet and rendered by
various browsers in a special format.

A _static site generator_ takes some number of source files as input
and produces a website, composed of marked up text, stylesheets and
possibly scripts. The word _static_ comes from the fact that the
generated site is pregenerated and then handed to the visitors as-is.
There is no dynamic creation of documents prompted by user interaction.

This brings some advantages:

* Simplicity -- the website is built from simple building blocks
* Security -- small attack vectors. It is very difficult to leverage
  bugs in `html` and `css` to exploit systems..
* Speed -- requires less bandwidth. The static site generator can
  do various tricks to compress the resulting files.


# Separating concerns

## Markup languages
Most prominent markup language is surely `html`. `html`-files contain
the actual textual content as well as a description of the contents
semantic structure.
The author *marks up* the document with a special syntax that separates
different parts of the text and indicates "intent".

An example of this might be:

### Plain textual contents:

    My cat Gibson

    Gibson is:
    A cat
    Black

    I love my cat Gibson!

### With added markup:

{% highlight html %}
<title>My cat Gibson</title>

<list>
Gibson is:

<item>A cat</item>
<item>Black</item>
</list>

I <emphasis>love</emphasis> my cat Gibson!
{% endhighlight %}


## Stylesheets
Another file describes how the different elements should be presented.
This is often called a stylesheet. For example, this is a rule that
describes how to display the title `My cat Gibson`:

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


## Advantages of separating style from content
One of the main concepts in programming and (software) engineering is
called [Separation of concerns][wiki-sepcon].
It is a very important foundational design principle that basically
boils down to splitting big and/or complex problems into smaller more
manageable chunks. It also states that one should strive to separate
responsibilities and consequences for change.
In the context of document preparation, imagine writing a book and
manually formatting all headers while writing. Modifying the headers later
on would mean repetitive and error-prone manual labour, which should
be avoided at all costs when working with computers.. By separating the
concern of *entering text* from the concern of formatting and typesetting
the text, a single line in the stylesheet would control all headers
in the entire book, making the change much easier and predictable.

Much has already been written about this. Some personal favourites of mine include:

* ["Word Processors: Stupid and Inefficient" by Allin Cottrell][allincottrell]
* ["Proprietary Binary Data Formats: Just Say No!" by Sam Steingold][proprietaryformats]


There are numerous advantages to keeping the *content* separate from
the *style*. Especially when producing documents such as websites and
other literature. The author can concentrate on the content alone,
without having to think about formatting the text as it is entered. It
also makes for more *consistent styling and formatting* of documents.

Even though it certainly is *possible* to use conventional Word processors
or `WYSIWYG` editors (InDesign, Scribus) properly and as intended,
*not many users actually do*.. The classic example of inproper use
would be hitting Return repeatedly to align some part of the document
vertically. Or inserting spaces to manually adjust horizontal alignment.

Proper use of Word and similar programs requires use of
paragraph and character-styles throughout, which in turn requires
self-discipline as it in no way is enforced by the program.

I am a long-time advocate of LaTex and John Grubers Markdown combined
with `pandoc`, documents and notes are kept in plain (`utf-8` encoded)
text files. Markdown-syntax allows for very fast typesetting and `pandoc`
can be used to convert the source files to a range of other file formats;
`pdf`, `html` and even proprietary formats such as Word and InDesign.


#### (La)TeX
I prefer to write papers, reports, CV:s, etc. using [LaTeX][wiki-latex].
[TeX][wiki-tex] was released by computer science legend
Donald Knuth in 1978. TeX is programming language developed
to improve typesetting of scientific materials heavy on math.


The blog is built with the static site generator [`Jekyll`][jekyll], which
basically allows authoring the content in simple text-files. The site is built
into static `html`-pages by `Jekyll`, where1 separate configuration files and
stylesheets determine how the content is presented and organized.

Most assignments and projects suitable for public display will be uploaded to
this blog, as well as other miscellaneous "personal" posts.

I've been wanting to create a Jekyll-based personal blog for a couple of years
-- funny how most workflows, toolchains and techniques we've used during the
[Software Development and Operations programme][udm] has lined up almost
perfectly with my private interests and workflows.

More about [Markdown][markdown] and the so-called "plain-text" approach to
writing in future posts .. _(More about workflows too I bet)_





[wiki-tex]: https://en.wikipedia.org/wiki/TeX
[wiki-latex]: https://en.wikipedia.org/wiki/TeX
[wiki-sepcon]: https://en.wikipedia.org/wiki/Separation_of_concerns
[allincottrell]: http://dsv.su.se/polopoly_fs/1.125295.1361458482!/menu/standard/file/wp.htm
[proprietaryformats]: http://www.podval.org/~sds/data.html
