---
layout: post
title:  "Plain text authoring"
date:   2016-11-16 22:57:30
tags:   [workflow]
---


Advantages of separating style from content
-------------------------------------------
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

Even though it certainly is *possible* to use conventional
"Word processors" or `WYSIWYG` editors (InDesign, Scribus) properly and
as intended, _not many users actually do_..
A classic chilling example of inproper use would be aligning parts of
a document vertically by repeatedly hitting the Return-key. Or inserting
spaces to manually adjust horizontal alignment.

Proper use of Word and similar programs requires use of
paragraph and character-styles throughout, which in turn requires
self-discipline as it in no way is enforced by the program.

I am a long-time advocate of LaTex and John Grubers Markdown combined
with `pandoc`, documents and notes are kept in plain (`utf-8` encoded)
text files. Markdown-syntax allows for very fast typesetting and
`pandoc` can be used to convert the source files to a range of other
file formats; `pdf`, `html` and even proprietary formats such as
Microsoft Word and Adobe InDesign.


#### (La)TeX
I prefer to write papers, reports, CV:s, etc. using [LaTeX][wiki-latex].
[TeX][wiki-tex] was released by computer science legend
Donald Knuth in 1978. TeX is programming language developed
to improve typesetting of scientific materials heavy on math.




[wiki-tex]: https://en.wikipedia.org/wiki/TeX
[wiki-latex]: https://en.wikipedia.org/wiki/TeX
