<a id="Top"></a>

Nikola Static Website Generator on Github
=========================================

This website has been created using Github's ability to provide and run the Nikola 
application, and also run up to 120+ other applications that may be required by Nikola.

It does not require a PC to have Nikola software installed and for the PC to *push* and 
*pull* files to Github.

The documents in the *src* (source) branch are the only ones that are edited to modifiy the 
website and any of its pages. After editing a file, click on *Commit* and the CPU's at 
Github will start running the applications to re-build the whole website. These *Updating* 
and *pages build and deployment* phases can be monitored by clicking on the *Actions* tab. 
The website re-build will take about 3 to 5 minutes before a refresh of a web-browser will 
display the updated website.

In some cases it is easier to write a document on a PC in reStructuredText *.rst* or 
Markdown *.md* and then upload this file to a suitable folder in Github *src* branch.

For each *Commit* the website is re-built and located in the *main* branch. Do not edit any 
files in *main* branch as they will get replaced during the next *Commit* that is perform.

The src top-level directory has 4 x folders and 2 x files. 
The four folders are:
```
.github <--- Contains the workflow folder with thew main.yml yaml file for Nikola to rebuild the wbsite
files   <--- Folder for files. For example .pdf's for downloading and to customise css. 
images  <--- Folder for storing .jpg, .png, etc. image files
pages   <--- Folder for all the .rst or .md files that become .html webpages.
```


The two files are:
```
.gitignore <--- Command for *git*. Dont change this file.
conf.py    <--- This python configuration file performs the loading of constants that are
                used by Nikola every time the website is re-built. 
```

**Tree diagram of the *src* branch directory and its sub-directories and files.** - 2025-02-17

All files have an <-- explanation comment. All directories have no comment.
<!--the line-height is reduced slightly so vertical lines do not have spaaces-->
<p style="line-height: 0.99em; font-family: monospace, monospace;">
src <-- Dir Source Code top level branch directory. <br> 
│ <br> 
├── .github/workflows <br> 
│&nbsp;&nbsp;&nbsp;└── main.yml <-- Yaml. Runs Nikola to re-build the website. <br>
│ <br> 
├── files <br> 
│&nbsp;&nbsp;&nbsp;├── assets/css <br> 
│&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;└── custom.css <-- For adding additional CSS. E.g. logo size. <br> 
│&nbsp;&nbsp;&nbsp;│ <br>
│&nbsp;&nbsp;&nbsp;└── files <br> 
│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── test.pdf <-- Used by development to test Demo's downloads <br> 
│ <br> 
├── images <br> 
│&nbsp;&nbsp;&nbsp;├── favicon-16x16.png <-- Icons to insert in the web-browser tab <br> 
│&nbsp;&nbsp;&nbsp;├── favicon-32x32.png <-- <br> 
│&nbsp;&nbsp;&nbsp;└── jd-logo.svg <-- A .svg file that contains the logo. <br> 
│ <br>
├── pages <br> 
│&nbsp;&nbsp;&nbsp;│ <br> 
│&nbsp;&nbsp;&nbsp;├── about-jeremy.rst <br> 
│&nbsp;&nbsp;&nbsp;│ <br> 
│&nbsp;&nbsp;&nbsp;├── legal-introduction.rst <br> 
│&nbsp;&nbsp;&nbsp;├── legal-cm-contempt.rst <-- Write-up file on Craig Murray. <br> 
│&nbsp;&nbsp;&nbsp;├── legal-pcj-writeup.rst <-- Write-up file on PCJ. <br> 
│&nbsp;&nbsp;&nbsp;├── legal-worden-writeup.rst <-- Write-up file on Dr. Robert Worden. <br>
│&nbsp;&nbsp;&nbsp;│ <br>  
│&nbsp;&nbsp;&nbsp;├── streisand-introduction.rst <br> 
│&nbsp;&nbsp;&nbsp;├── streisand-aaa-winstanley.rst <-- Write-up file <br> 
│&nbsp;&nbsp;&nbsp;├── streisand-other-govt.rst <-- Write-up file <br> 
│&nbsp;&nbsp;&nbsp;├── streisand-palestine-congress-notes.rst <-- Write-up file <br> 
│&nbsp;&nbsp;&nbsp;├── streisand-palistine-congress.rst <-- Write-up file <br> 
│&nbsp;&nbsp;&nbsp;├── streisand-social-media.rst <-- Write-up file <br> 
│&nbsp;&nbsp;&nbsp;├── streisand-terrorism.rst <-- Write-up file <br> 
│&nbsp;&nbsp;&nbsp;├── streisand-uk-police.rst <-- Write-up file <br>  
│&nbsp;&nbsp;&nbsp;│ <br> 
│&nbsp;&nbsp;&nbsp;├── index.rst <-- Write-up file. The Welcome or Home page. <br> 
│&nbsp;&nbsp;&nbsp;│ <br> 
│&nbsp;&nbsp;&nbsp;└── readme-src <br> 
│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── README.md  <-- The file you are now reading. <br>
│ <br>
├── .gitignore <-- Commands for Git. Don't touch. <br> 
└── conf.py <-- The python program that Nikola runs. It contains many constants that you modify. <br>
</p>

Most directories have a README.rst file that contains a brief explanation of what is in that
directory. These README.rst files are omitted in the above tree diagram to make it 
easier to comprehend the diagram. Although the README files are passed to the "main"
branch their contents are not normally displayed by the website.


Metadata Template for .rst files
--------------------------------

All *reStructuredText .rst* filenames should only use **a to z**, **0-9** and a literal dash **-**.

This is what the *slug* metadata expects.

When creating a new .rst file copy and paste the template below:
```
.. title: *My Title
.. slug: *name of file without .rst extension.
.. date: *2025-02-14
.. tags: 
.. category: 
.. link: 
.. description: *Write description
.. type: text
.. hidetitle: True

.. _top:

Write or Paste your document here...

`[Goto Top] <#top>`_

```
Github will display the .rst metadata as a table using three hyphens before and after the metadata,
however a bug seems to cause it to not incorporate at least the last line of metadata.

Metadata Template for .md files
-------------------------------

All *markdown .md* filenames should only use **a to z**, **0-9** and a literal dash **-**.

This is what the *slug* metadata expects.

When creating a new .md file copy and paste the template below:

```
title: *My Title
slug: *name of file without .rst extension.
date: *2025-02-15
tags: 
category: 
link: 
description: *Write description 
type: text
hidetitle: true

<a id="Top"></a>

Write or Paste your document here...


<br><hr>
[Goto Top](#top)
```
When using Github to display a markdown .md file, the metadata can be presented as a table at the 
top of the displayed content if three hyphens are placed above and below the metadata. In which
case this is the .md template:
```
---
title: *My Title
slug: *name of file without .rst extension.
date: *2025-02-15
tags: 
category: 
link: 
description: *Write description 
type: text
hidetitle: true
---

<a id="Top"></a>

Write or Paste your document here...

<br><hr>
[Goto Top](#top)
```


[Goto Top](#top)
