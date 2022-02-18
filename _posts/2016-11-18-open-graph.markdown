---
layout: post
title:  "Open Graph metadata"
date:   2016-11-18 06:06:51
tags:   [development, devops, web]
disqus: true
image:  "https://upload.wikimedia.org/wikipedia/commons/7/72/Open_Graph_protocol_logo.png"
---


This post is part of an assignment in the course
["1DV022 -- Client-based Web Programming"][1dv022] at Linnaeus
University in Kalmar.

What is Open Graph?
===================
This is a brief overview of [The Open Graph Protocol][opengraph],
a metadata _standard_ created by Facebook.

Facebook supremacy
------------------
Open Graph was created by Facebook in 2010. It is part of their plan
for world domination by embedding proprietary code in basically
_every, single, webpage_ ..
This is an interesting read on contemporary trends and use of the
internet: ["The Myth of Openness"][floss-myth].

Excerpt from ["What You Need to Know About Open Graph Meta Tags for Total Facebook and Twitter Mastery"][kissmetrics]:

> It promotes integration between Facebook and other websites by
> allowing them to become rich “graph” objects with the same
> functionality as other Facebook objects.

This means allowing for connections to be made between sites and
storing information in a way that is transferable across sites and
services.

The most obvious example of how this might be useful is
"sharing" websites or posts to different social media. Often when
sharing something; a neat looking preview is shown before and/or after
the share is posted. This preview might contain an image somehow
related to the content, maybe an excerpt from the text or some other
information that is used to neatly sum up the post you've shared.

Social graphs and metadata
--------------------------
More about Open Graph from the [official website][opengraph]:

> The Open Graph protocol enables any web page to become a rich object in a
> social graph.  For instance, this is used on Facebook to allow any web page
> to have the same functionality as any other object on Facebook.
>
> While many different technologies and schemas exist and could be combined
> together, there isn't a single technology which provides enough information
> to richly represent any web page within the social graph. The Open Graph
> protocol builds on these existing technologies and gives developers one thing
> to implement. Developer simplicity is a key goal of the Open Graph protocol
> which has informed many of [the technical design decisions][designdecisions].


This is done with Open Graph metadata. [Metadata][wiki-metadata]
is simply "data about data", such as `author`, `create date`, `title`,
`categories`, etc.

### Example metadata
An example listed on the [official website][opengraph] is the following
Open Graph protocol markup for the movie _The Rock_ on [IMDB][imdb-therock]:

{% highlight html %}
<html prefix="og: http://ogp.me/ns#">
<head>
<title>The Rock (1996)</title>
<meta property="og:title" content="The Rock" />
<meta property="og:type" content="video.movie" />
<meta property="og:url" content="http://www.imdb.com/title/tt0117500/" />
<meta property="og:image" content="http://ia.media-imdb.com/images/rock.jpg" />
...
</head>
...
</html>
{% endhighlight %}


Using Open Graph with Jekyll
----------------------------
Integrating the Open Graph metadata into the Jekyll website went
pretty smooth, once again thanks to the "programmable" templating
functionality _liquid_ that Jekyll provides.

I do a lot of testing that variables are defined in either the site
configuration file `_config.yml` or the YAML front matter data
contained in individual pages/posts; _before_ setting the Open Graph metadata.

There is also a couple of fallbacks for the cases where some field
isn't defined.

Another example of this is image metadata -- if a blog post specifies an URL
to a image in its YAML front matter data, it is added to the Open Graph
metadata. And if the blog post does not specify an image, a fallback
image defined in the site configuration file is substituted in its place.

The Open Graph code is kept in a separate file that can be inserted
where applicable. This also makes future modifications and re-use much
easier.

References
----------
I followed a bunch of guides and referenced the source code for a couple of
Jekyll templates that included support for Open Graph.

* ["Integrating social meta tags into Jekyll"][milanaryal] by Milan Aryal
* ["Jekyll: how to add metadata to your site"][vrepin] by Vitaly Repin
* ["Adding Open Graph Tags to Jekyll"][davidensinger] by David Ensinger




[1dv022]: https://coursepress.lnu.se/kurs/klientbaserad-webbprogrammering/
[kissmetrics]: https://blog.kissmetrics.com/open-graph-meta-tags/
[opengraph]: http://ogp.me/
[wiki-metadata]: https://en.wikipedia.org/wiki/Metadata
[designdecisions]: http://www.scribd.com/doc/30715288/The-Open-Graph-Protocol-Design-Decisions
[imdb-therock]: http://www.imdb.com/title/tt0117500/
[milanaryal]: https://milanaryal.com/integrating-social-meta-tags-into-jekyll/
[vrepin]: http://vrepin.org/vr/JekyllMeta/
[davidensinger]: http://davidensinger.com/2013/04/adding-open-graph-tags-to-jekyll/
[floss-myth]: http://write.flossmanuals.net/an-open-web/the-myth-of-openness/
