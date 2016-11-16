---
layout: post
title:  "Static Site Generators"
date:   2016-11-16 18:00:52
tags:   [development, jekyll, meta]
---

So, what is _static site generators_?

### Static Site Generators
Simply put, a static site generator is a program that creates webpages.
All webpages are transmitted over the internet and rendered by
various browsers in a special format. Websites can be split up into:

#### `html`-files
`html`-files contain the actual textual content and describes the
semantic structure. This basically means that the author *marks up*
the document with a special syntax.

An example of this might be:

Plain text:
```
My cat Gibson

Gibson is:

A cat
Black

I love my cat Gibson.
```

With added markup:
```
<title>My cat Gibson</title>

<list>
Gibson is:

<item>A cat</item>
<item>Black</item>
</list>

I <emphasis>love</emphasis> my cat Gibson.
```


#### Stylesheets
Another file describes how the different elements should be presented.
This is often called a stylesheet. For example, this is a rule that
describes how to display the title `My cat Gibson`:

```css
title {
    size: largest
    style: bold
    color: red
}
```


#### Advantages of separating style from content
Separation of concerns is a reoccurring and important concept
in programming and (software) engineering in general.

It basically states that one should strive to separate
responsibilities and consequences for change, I.E. split a big
and/or complex problem into smaller more manageable chunks.

There are numerous advantages to keeping the *content* separate from the *style*.
Especially when producing documents such as websites and other literature.
The author can concentrate on the content alone, without having to think about formatting the
text as it is entered. It also makes for more *consistent styling and formatting* of documents.

Even though it certainly is *possible* to use conventional Word processors or
`WYSIWYG` editors (InDesign, Scribus) properly, *not many users actually do*..

I am a long-time advocate of LaTex and John Grubers Markdown combined with `pandoc`.

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
[udm]: https://cms.lnu.se/education/programmes/NGUDM?l=en
[1dv022]: https://coursepress.lnu.se/kurs/klientbaserad-webbprogrammering/
[jekyll]: https://jekyllrb.com/
