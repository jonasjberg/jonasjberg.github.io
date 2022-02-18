---
layout: post
title:  "The autonameow Project"
date:   2017-06-18 21:54:48
tags:   [autonameow, projects, development, workflow, python, pim]
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


This post contains some of the documents produced during the course.

__Note that this post describes `autonameow` version `v0.4.0` and does
not reflect the current state of the project.__


--------------------------------------------------------------------------------


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



Architecture and System Design
==============================
This is a description of the system design and software architecture of the
central code in the `autonameow` project as of version `v0.4.0`.


Overview
--------

### Problem Description
The main purpose of the program is to simplify renaming of files.

The program operation should preferably be non-interactive and require minimal
user supervision.

### Proposed Solution
The user specifies the target file name format, defined as a number of
ordered fields.  The available fields are fixed and not user-configurable.
This configuration should preferably be stored in a user-editable configuration
file. Alternative methods for configuration could also be provided.

For example, given the original file name `bellovin-report-april-1-98.txt`;

| Filename Template                   | Resulting File Name                                   |
| ----------------------------------- | ------------------------------------------------------|
| `{date} {title} - {author}.{ext}`   | `1998-04-01 IAB Architecture Report - Bellovin.txt`   |
| `{author} - {title} - {date}.{ext}` | `Bellovin - IAB Architecture Report - 1998-04-01.txt` |
| `{date} {basename}.{ext}`           | `1998-04-01_bellovin-report-april-1-98.txt`           |


The program is to fill out the template fields by extracting information from
the file name, textual contents and metadata.

Another set of rules determine which of the extracted data that will be used
to populate the template fields. It is likely that an analysis returns multiple
possibly conflicting date/time-entries, for instance.  In this case, the entries
are prioritized and ranked in a manner that is specific to file types, also
configurable by the user.


### Example Use Case
A most basic use-case is described below. In this case the program is executed
from a terminal, but the program might just as well be executed from a GUI file manager.
Many GUI file managers have some functionality for executing external commands,
passing the currently selected files to the external command for processing.
This could be used to execute `autonameow`, passing the files currently
selected in the GUI file manager as positional arguments.

The following example demonstrates the core concepts of the application.

#### User Configuration
The output format is configurable by the user. In this example, the user has
configured `autonameow` to use the following filename template:

```
[datetime]  [description] . [ext]
```

#### Program Invocation
The user wants to rename an image file called `DSCI0001.jpg` using `autonameow`,
which is executed by running the following command:

```bash
$ autonameow DSCI0001.jpg
```

#### Expected Results
Following the invocation, the original file `DSCI0001.jpg` is expected
to be renamed using the defined filename template and the available data.

```
"DSCI0001.jpg"  -->  "2017-04-14T204325 Gibson at work.jpg"
```

A detailed description of the program operation and method for arriving at this
result is given below.


System Design
-------------
The system is separated into two main parts; the `core` and *"the rest"*.

The `core` is the main command-line application and contains most of the
code.

The `core` uses other pluggable parts to extract and analyze information.
These parts are `analyzers`, `extractors` and `plugins`.

It should be easy to add functionality and custom behaviour to the program,
much thought has gone into making this possible. And although the current
version `v0.4.0` does not fulfill these goals, it comes a lot closer
than previous versions. I feel I have made substantial progress, future
versions will continue to improve towards the truly modular design.

The `core` takes given input files and determines which analyzers are
suited for the file type. Most of the normal program execution path happens in
the context of an `Analysis`. The `Analysis` executes analyzers and stores
collected information in the analysis `Results`.

Analyzers are given a callback function that they use to pass data back to the
parent `Analysis`.

Results are labeled and ordered in data structures. These data structures are
used in communication between the `core` and *"the rest"*, in the configuration
file, etc.

One single reference data structure is stored as a constant, and all other
internal structures are derived from this constant at runtime.  This makes
changes easier and many complex interactions automatically adjust to the
changes. The problem of defining internal data structures and communications
between parts was the biggest problem during development.

I finally came up with this solution which has worked very well so far.


### Overview
The program will act on one or many files at once. The following processing
pipeline is executed for each given file.

1. Receive file to process
2. __Analysis Phase__ -- Gather information about the file
3. __Evaluation Phase__ -- Determine suitable actions from rules and data
4. __Action Phase__ -- Apply active action


### Detailed Description
Once again, with additional implementation details (some of which is still
unimplemented..) included:

1. Receive file argument
    1. Perform various basic sanity checks;
        * Is the argument a file?
        * Is the argument a directory?
        * Is the argument a symbolic link?
        * Is the file readable?
        * Is the file writable?
    2. `autonameow` constructs a `FileObject` instance to represent the file.
        * Extract basic information about the file.
        * Determine the file (MIME) type from the "magic header bytes".
          (I.E. image, pdf, video, txt, etc.)

2. __Start of the Analysis Phase__
    1. Create an instance of the `Analysis` class.
        * The `Analysis` instance creates an instance of the `AnalysisRunQueue` class.
        * The analysis run queue is populated with MIME-type specific
          analyzers, depending on the `FileObject` MIME-type.
        * Each analyzer in the run queue is executed in succession and the
          results are stored in an instance variable `results` in the
          `Analysis` instance.
        * The analyzers are given a callback function that they use to pass
          results back to the parent `Analysis`.

    2. Execute analyzers applicable to the file. Information in gathered from;
        1. The file __name__
            * The `FilenameAnalyzer` is always included (most files have
              names), tries to extract information from the file name;

        2. The file __contents__
            * Get plain text from the file contents.
            * Extraction technique is specific to the current file type;
                * Run `OCR` on images to extract textual content.
                * Convert pdf documents to plain text.

        3. The file __metadata__
            * Extract information from embedded metadata.
            * Metadata type and extraction technique is specific to file type;
              "media" often contain `EXIF` data, other document types use
              specific metadata formats.

        4. The file __surroundings__ *(optional)*
            * Extract information from the surrounding structure;
                * Parent directory name
                * Other files in the directory
    3. Some analyzers call data `extractors` to perform generic extraction that
       might be used by many extractors.
       One exmaple of this is extracting plain text from a pdf document.

3. __Start of the Evaluation Phase__
    1. The `NameBuilder` and `Configuration` interact to evaluate which rules
       apply to the file.
        * Rules that require an exact match are discarded if any condition
          evaluates to false.
        * Remaining rules are priorized, first by the number of conditions that
          evaluated to true, then by the user-specified `weight` if need be.
    2. The active configuration is validated;
        * If the active configuration rule specifies the name template
          `{datetime} {title}.{extension}`, these fields must be "reachable".
          I.E. there must be some information on which data should be used to
          populate these fields.
        * The current version `v0.4.0` simply verifies that the active
          configuration rule includes all required sources.
    4. Further validation and refinement in the `NameBuilder` class.
        * The matched rule specifies;
            * The file name template to use when constructing a new name.
            * Which analysis data should be used to populate the placeholder
              fields in the name template.
            * Additional options, date/time-information formatting, etc.
        * With the above information, the `Results` in queried for the required
          fields, the data is cleaned up and finally used to construct a new
          file name.

4. __Start of the Action Phase__
    1. Determine active action.
        * Simulate (`-d`, `--dry-run`)? --- Print what would have happened.
        * If running with `--automagic`,  rename the file.
    2. Perform the action.
        * Make sure the target destination does not already exist.
        * Check OS-specific restrictions of file/path-name lengths.
        * Rename the file.


### Generalization
The software design strives to keep a strict separation between certain
components. This is motivated by ease of development and the fact that a lot of
development time is needed to implement the various type-specific metadata
extractors and analyzers. Therefore, the underlying base should be well
designed and flexible enough as to not require invasive refactoring.

The main points of separation are:

1. Main `autonameow` __core__
    * High-level control of all main functionality.
2. File type -specific __Analyzers__
    * Sub-classes `AbstractAnalyzer`, must implement certain methods;
      I.E. implement an interface defined by `AbstractAnalyzer`.
3. Data __Extractors__
    * Sub-classes `Extractor`, must implement certain methods;
      used for utlity extraction performed by analyzers.
4. __Plugins__
    * Currently very much a work in progress! Version `v0.4.0` includes a
      script that queries the Microsoft Vision API as a proof of concept.
    * Should provide some interface that allows integrating other code.



### Modularization
Communication between components requires a set data structure that should be
tolerant to change and not require major refactoring if changed. Ideally, the
data structure would be defined and frozen, disallowing any future
modifications.  Alternatively, the data structure would be designed in such a
way that it allows for future extension and effectively modification without
breaking compatibility with older versions.


#### Redesigned Internal Data Structure for Analyzers
Analyzers are moving towards using callbacks and simple "query strings" when gathering data.

The "query strings" are simply flattened nested dictionary lookup keys.

For instance, the data might be stored in the nested data structure;

    DATA = {
        'contents': {
            'mime_type': None,
            'textual': {
                'raw_text': None,
            }
        }
    }

The corresponding flattened "query strings" for this structure would be;

    QUERY_STRINGS = [
        'contents.mime_type',
        'contents.textual.raw_text'
    ]

The analyzer data storage formats are derived from a single reference, just
like most other formats.  This reference; `RESULTS_DATA_STRUCTURE`, is located
in `core/constants.py`.



#### Legacy Internal Data Structure for Analyzers
Analyzers that subclass the `AbstractAnalyzer` class use this
following data structure for each gathered result;

    analyzer_result = { 'field': 'DateTimeOriginal',
                        'value': '2017-05-02 17:47:19',
                         'type': ('metadata', 'exif'),
                       'source': 'ImageAnalyzer',
                       'weight': 0.75 }

This format will be removed and replaced with the new way using callbacks.

#### Internal Data Structure for the Analysis
All results are stored in an instance of the `Results` class.

This class also derives its internal format from the reference,
`RESULTS_DATA_STRUCTURE`.

This class also provides means for querying the nested results data using
"query strings".

### Configuration Files
Most of the critical behavior of `autonameow` is user-configurable and 
can be stored in a configuration file.

The configuration file is in `yaml` syntax.
At first launch, a default template configuration file is written to the
standard operating system configuration directory.  Different alternative paths
are used depending on the environment.  The first default location on MacOS is
`~/Library/Application support/autonameow.yaml`, while Linux uses
`~/.config/autonameow.yaml`.

The configuration file contains two main parts, __file rules__ and *other
options*.

Each rule contains; 

* __Conditions__ that are evaluated to determine if the rule should be applied
  for a given file.
* __Data Sources__ instructions on which data should be used to construct new file names.
* __Name Template__ to fill out using analysis data from the specified sources.
  Placeholder fields are certain words surrounded by curly braces, which will
  be populated with data by `autonameow`.

Each rule also contains other fields, that are optional, such as a
user-specified __weight__ that is used to resolve deadlocks when the rules are
prioritized. If the  __exact match__ option is set to `True`, all conditions
must evaluate true for a rule to be considered to apply to a given file.


External Libraries and Modules
------------------------------
A lot of difficult problems has already been solved. And much of the heavy
lifting is done with open source code authored by others.
The freedom to leverage existing quality code ("Standing on the shoulders of
giants") is surely one of the key benefits of the open source model.

So, to all developers that has been involved with any of the projects listed
below;   
__THANK YOU for sharing your work with the world!__

Licenses for third party code are included with the main `autonameow` source
code repository under the `license` directory.

`autonameow` makes use of the following libraries, modules, scripts and
executables:


### Image Optical Character Recognition --- `tesseract`
Very popular and well established OCR Engine used to extract text from images.

`autonameow` uses the Python wrapper `pytesseract` to interface with
`tesseract`, which is a compiled binary application. This simply provides an
additional layer of abstraction between the OS-specific installation of
`tesseract` and the calling `autonameow` code.

* `tesseract`
    * Author: Ray Smith, Hewlett-Packard, Google
    * License: [Apache v2.0][2]
    * Website: <https://github.com/tesseract-ocr>
    * Documentation: <https://github.com/tesseract-ocr/tesseract/wiki/Documentation>
    * Source repository: <https://github.com/tesseract-ocr/tesseract>

* `pytesseract`
    * Author: Samuel Hoffstaetter, Juarez Bochi, Matthias Lee
    * License: [GNU General Public License v3][1]
    * Website: <https://github.com/madmaze/python-tesseract>
    * Documentation: <https://pypi.python.org/pypi/pytesseract>
    * Source repository: <https://github.com/madmaze/python-tesseract>

### Metadata and Meta Information tool --- `exiftool`
Powerful general purpose tool for viewing, editing and writing various metadata
and meta information formats. Supports a wide range of formats and file types.

`autonameow` uses the Python wrapper `pyexiftool` to interface with `exiftool`.

* `exiftool`
    * Author: Phil Harvey
    * License: [GNU General Public License][3][(note)][4]
    * Website: <http://owl.phy.queensu.ca/~phil/exiftool/>
    * Documentation: <http://owl.phy.queensu.ca/~phil/exiftool/exiftool_pod.html>
    * Source repository: <https://sourceforge.net/p/exiftool/code/ci/master/tree/>

* `pyexiftool`
    * Author: Sven Marnach
    * License: [BSD][5] and [GPL][6]
    * Website: <http://smarnach.github.com/pyexiftool/>
    * Documentation: <http://smarnach.github.com/pyexiftool/>
    * Source repository: <http://github.com/smarnach/pyexiftool>



> This document was part of an examination in the course
> "`1DV430` -- Individual Software Development Project", given at
> [Linnaeus University](https://lnu.se/en/) as port of the
> "[Software Development and Operations](https://udm-devops.se/)" programme.




[autonameowrelated]: https://github.com/jonasjberg/autonameow/blob/master/docs/related.md
[beetboxbeets]: https://github.com/beetbox/beets
[autonameowgithub]: https://github.com/jonasjberg/autonameow
[1]: https://www.gnu.org/licenses/gpl-3.0.en.html
[2]: http://www.apache.org/licenses/LICENSE-2.0
[3]: http://owl.phy.queensu.ca/~phil/exiftool/#license
[4]: http://dev.perl.org/licenses/
[5]: https://raw.githubusercontent.com/smarnach/pyexiftool/master/COPYING.BSD
[6]: https://raw.githubusercontent.com/smarnach/pyexiftool/master/COPYING.GPL
[7]: https://github.com/novoid/filetags
[8]: https://xkcd.com/1179/
