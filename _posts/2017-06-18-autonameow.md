---
layout: post
title:  "The autonameow Project"
date:   2017-06-18 21:54:48
tags:   [development, workflow, python, pim]
disqus: true
image: "" 
---

This is an introduction of the `autonameow` project.

I've been working on `autonameow` off and on for about two years now.  The
project is pretty ambitious and I got stuck at some point, and several factors
made me put the project on hold for a while. 

Nothing much happened until just about two months ago, when I took the course
"`1DV430` -- Individual Software Development Project", where I could choose
practically without restrictions what I'd like to work on.

I chose to revisit `autonameow` and spend some quality time working on it.
Some serious progress was made during the course. I just recently completed the
course (with very good results) and development has continued since.

The project has since been made public and is available [here][autonameowgithub]


Project Plan
============
This is the project plan for the `autonameow` project.


Project Introduction and History
--------------------------------
The project and the main software application is called `autonameow` --- a play
on the compounded words __automatic__, __name__ and __meow__.

The first two words relate to the central project goal -- to *simplify naming
of files to the point of automating the task*. The last part of the name;
__meow__, is attributed to my cat __Gibson__, a most reliable and dedicated
contributor to not only this project but in fact most of the projects I've been
involved with.

I started the `autonameow` project in late February 2016 as a personal hobby
project, primarily for my own entertainment but also with some aspiration to
possibly release the program to the public and the open source community under
some free software license.


Work on the project has been sporadic and in the time leading up to this all
but halted.  When presented with the opportunity to freely choose a project for
the course, I took the chance to revisit `autonameow` and once again spend some
quality time working with it.


Project Goals
-------------
`autonameow` does automatic renaming of files.

> The primary goal is to reduce the overhead and manual work required to
> apply a strict file naming convention uniformly and consistently.
> 
> The main function is to find suitable file names from some set of rules,
> given the available data.


### Target Features
The high-level goal of `autonameow` is simple; __simplify renaming of files__.

These are the basic requirements of `autonameow` functionality and features:

* `autonameow` should greatly simplify tedious file naming tasks
* `autonameow` should be able to rename files *"semi-intelligently"*
* `autonameow` should be configurable and customizable by the user

The "semi-intelligence" primarily means that the program action should be
"hands-off" and safe, but also be able to decide which renaming operation
should be applied for some given file.


Vision Document
===============
This is the initial vision document for the `autonameow` project.


Background and Purpose
----------------------

### Problem Description
The underlying problem stems from the traditional hierarchical file systems,
that are inherently ill suited for structuring content as to facilitate quick
retrieval by humans.
Locating files require some system of sorting and naming the files.
Pictures goes in this folder, document in this other folder, etc.

Locating files *quickly* and keeping track of a lot of data requires a very
well thought out file naming convention and directory hierarchy.
It also requires the __discipline__ to adhere to these rules and apply constant
upkeep to keep things in order.

In practice, most users do not have a system for managing their files, and
do not adhere to a strict file naming scheme.
And even if a system was planned and defined, applying it consistently requires
some work and might prove to be too much of an effort.

Consequently, most users files and directories are not easy to locate and
navigate.


Many users instead rely on metadata search tools to locate their files.  An
example of such a tool is *Spotlight search*, built into `MacOS`.

However, such tools only solve part of the problem. Also, such tools often
perform most optimal when given a well structured data set to work with.

A well structured directory hierarchy allows narrowing searches to specific
directories or directory trees, which allows for more precise search queries.
The combination of searching both __metadata__, such as the file contents
*and* a "traditional" search of file __names__, is very powerful.

In conclusion:
__Users would benefit from a tool that assists them in renaming files.__


### Proposed Solution
The program, if implemented properly, should significantly __speed up tedious
and error-prone tasks__ that most users perform on a daily basis.

The goal of `autonameow` is to __simplify the process of renaming files__ to
the point that keeping to some organizational system or file naming convention
__no longer requires discipline and a great deal of time__.

The application should be the tool that simplifies naming files and in effect
also sticking to some arbitrary archiving strategy.  However, the task of
coming up with said strategy is still left to the user.

The proposed solution will ideally use all available data to __construct
suitable file names__.
This includes things like the file __name__, the file __metadata__, file
__contents__ and possibly other data related to the file.

The way in which the program uses the extracted data to construct file names
should be controllable by the user.  The format of the resulting file names
should likewise also by configured by the user.

In practice, a user could bind the `autonameow` program to a shortcut key in
their file browser, select a couple of files and execute `autonameow` with a
single keystroke. Given sufficient data, the files would be named correctly
with no user interaction.


### Prior Work and Alternatives
There are quite a few programs that provide automatic renaming of files.

See [this page][autonameowrelated] for a longer, detailed listing of programs with
similar functionality as well as other projects related to the domain.


There are many existing products that provide the intended `autonameow`
functionality, but these are often restricted to handle specific types of
files.

I have not yet found a program that solves the main problem description of
greatly simplifying keeping to some strict naming convention.
The user is still left with remembering *which* renaming-program covers which
types of files, as well as configuring each of the individual programs.

A general "one-click" solution seems to be missing.

For example [`beets`][beetboxbeets] does renaming of music
files very well and in a manner close to the way `autonameow` is intended to
work.
But `beets` handles only music files, renaming other types of files requires
additional programs.

There are [multiple programs][autonameowrelated] that automatically rename videos,
movies, TV-shows, etc.  But again, these programs only handle some specific
file types.

The problem with the existing programs is that they all have completely
separate interfaces and modes of operation. `autonameow` would provide a single
solution that covers all file renaming to some extent.


Target Users and Market
-----------------------
The application will primarily be a command-line application and a core library
that could be used by a GUI wrapper application, running as a client or maybe on
a server as a web application.

The intended users of the initial `autonameow` application are *"power users"*
such as developers and computer hobbyists. Users that care enough to think
about applying a rigorous file naming scheme can arguably be assumed to have
some knowledge of command-line applications.

The application will be released as free and open source software, possibly
under the GNU General Public License version 2.  A "market" as such is not
relevant at this time, the program is not written with any such goals in mind.
This is simply a private project that is made public as part of an assignment.

However, the open source community is welcome to contribute patches and
modifications. With this "market" in mind, the project will strive to keep
documentation, tests and source code synchronized and up to date.


Target Features
---------------
The high-level goal of `autonameow` is simple; __simplify renaming of files__.

These are the basic requirements of `autonameow` functionality and features:

* `autonameow` should greatly simplify tedious file naming tasks
* `autonameow` should be able to rename files *"semi-intelligently"*
* `autonameow` should be configurable and customizable by the user

The mentioned "semi-intelligence" means that the program action should be
"hands-off" and safe.
It would also certainly be possible to extend the "intelligence" to arbitrarily
sophisticated behaviour, like guessing a most probable file name when no rules
apply to a  renaming operation, etc.


Technologies
------------
The application will be written in Python 3 (version `3.6`).
Third-party libraries and extensions will be chosen to be compatible with the
project licensing.

The project will use `git` for versioning. The main program source code as well
as the documentation and documentation sources will be hosted on GitHub.

Critical parts of the codebase will be tested with unit tests, using testing
libraries provided with the Python standard libraries.  Some parts might also
require integration testing with more elaborate testing setups. However, most
testing will probably be done using simply Python programs and shell scripts.



> This document was part of an examination in the course
> "`1DV430` -- Individual Software Development Project", given at
> [Linnaeus University](https://lnu.se/en/) as port of the
> "[Software Development and Operations](https://udm-devops.se/)" programme.




[autonameowrelated]: https://github.com/jonasjberg/autonameow/blob/master/docs/related.md
[beetboxbeets]: https://github.com/beetbox/beets
[autonameowgithub]: https://github.com/jonasjberg/autonameow
