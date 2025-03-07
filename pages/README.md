<a id="Top"></a>

Nikola Static Website Generator on Github
=========================================

As this website is in Github, then you may make use of Github's ability to provide and run the Nikola 
application, and also run up to 120+ other applications that may be required by Nikola. This is
done by Github using the `.github/workflow/main.yml` file.

It does not require a PC to have Nikola software installed and for the PC to *push* and 
*pull* / *nikola github_deploy* files to Github.

The documents in the *src* (source) branch are the only ones that are edited to modifiy the 
website and any of its pages. After editing a file, click on *Commit* and the CPU's at 
Github will start running the applications to re-build the whole website in the *main* branch. 

The *Updating* and *pages build and deployment* phases can be monitored by clicking on the *Actions* tab. 
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

**Tree diagram of the *src* branch directory and its sub-directories and files.** - 2025-03-07 

  <!--the line-height is reduced slightly so vertical lines do not have spaces-->  
  <p style="line-height: 0.99em; font-family: monospace, monospace;"> 
  src <br>
  . <br>
  │ <br>
  ├── .github <br> 
  │&nbsp;&nbsp;&nbsp;└── workflows <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── main.yml <br> 
  │ <br> 
  ├── files <br> 
  │&nbsp;&nbsp;&nbsp;└── assets <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── css <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── custom.css <br> 
  │ <br> 
  ├── images <br> 
  │&nbsp;&nbsp;&nbsp;├── background.jpg <br> 
  │&nbsp;&nbsp;&nbsp;├── clinton_obama.jpg <br> 
  │&nbsp;&nbsp;&nbsp;├── HamPUG_hidetitle_about.png <br> 
  │&nbsp;&nbsp;&nbsp;├── HamPUG_hidetitle_index.png <br> 
  │&nbsp;&nbsp;&nbsp;├── HamPUG_initial_about_page.png <br> 
  │&nbsp;&nbsp;&nbsp;├── HamPUG_initial_index_page.png <br> 
  │&nbsp;&nbsp;&nbsp;├── hampug_lawrence_2018_03_12.jpg <br> 
  │&nbsp;&nbsp;&nbsp;├── hampug_lawrence_2018_03_12.png <br> 
  │&nbsp;&nbsp;&nbsp;├── logo.svg <br> 
  │&nbsp;&nbsp;&nbsp;├── ms4g02-map.png <br> 
  │&nbsp;&nbsp;&nbsp;├── nikola_demo_website.png <br> 
  │&nbsp;&nbsp;&nbsp;├── nikola_quiet_website.png <br> 
  │&nbsp;&nbsp;&nbsp;├── pug_100x74.png <br> 
  │&nbsp;&nbsp;&nbsp;├── pug_138x102.png <br> 
  │&nbsp;&nbsp;&nbsp;├── pug_24x24.png <br> 
  │&nbsp;&nbsp;&nbsp;├── pug_50x37.png <br> 
  │&nbsp;&nbsp;&nbsp;├── pug_50x50.ico <br> 
  │&nbsp;&nbsp;&nbsp;├── pug_50x50.png <br> 
  │&nbsp;&nbsp;&nbsp;├── pythonanywhere_hello_world.png <br> 
  │&nbsp;&nbsp;&nbsp;├── python-logo-generic.svg <br> 
  │&nbsp;&nbsp;&nbsp;├── python-logo-master-v3-TM.png <br> 
  │&nbsp;&nbsp;&nbsp;├── python-logo.png <br> 
  │&nbsp;&nbsp;&nbsp;└── website <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── ws10.png <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── ws11.png <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── ws12.png <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── ws13.png <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── ws1.png <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── ws2.png <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── ws3.png <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── ws4.png <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── ws5.png <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── ws6.png <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── ws7.png <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── ws8.png <br> 
  │&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── ws9.png <br> 
  │ <br> 
  ├── pages <br> 
  │&nbsp;&nbsp;&nbsp;├── about <br>
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── about-us.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── about-us.rst <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── history.md <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── history.meta <br>
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── map.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;└── map.md <br> 
  │&nbsp;&nbsp;&nbsp;│ <br>
  │&nbsp;&nbsp;&nbsp;├── index.md <br> 
  │&nbsp;&nbsp;&nbsp;├── index.meta <br> 
  │&nbsp;&nbsp;&nbsp;│ <br> 
  │&nbsp;&nbsp;&nbsp;├── meeting <br>   
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── meeting_overview.md <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;└── meeting_overview.meta <br> 
  │&nbsp;&nbsp;&nbsp;│ <br>  
  │&nbsp;&nbsp;&nbsp;├── meetup.md <br> 
  │&nbsp;&nbsp;&nbsp;├── meetup.meta <br> 
  │&nbsp;&nbsp;&nbsp;├── nikola_basics.meta <br> 
  │&nbsp;&nbsp;&nbsp;├── nikola_basics.rst <br> 
  │&nbsp;&nbsp;&nbsp;├── pythonanywhere.meta <br> 
  │&nbsp;&nbsp;&nbsp;├── pythonanywhere.rst <br>  
  │&nbsp;&nbsp;&nbsp;├── README.md <br> 
  │&nbsp;&nbsp;&nbsp;├── README.meta <br> 
  │&nbsp;&nbsp;&nbsp;│ <br>   
  │&nbsp;&nbsp;&nbsp;├── repository <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── general_code_examples.md <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── general_code_examples.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── ncea_code_examples.md <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── ncea_code_examples.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── repository_overview.md <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;└── repository_overview.meta <br> 
  │&nbsp;&nbsp;&nbsp;│ <br>  
  │&nbsp;&nbsp;&nbsp;├── rest <br>
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── rest_basics.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── rest_basics.rst <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── rest_directive.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── rest_directive.rst <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── rest_editor.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;└── rest_editor.rst <br>
  │&nbsp;&nbsp;&nbsp;│ <br> 
  │&nbsp;&nbsp;&nbsp;├── steps <br>  
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── step1.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── step1.rst <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── step2.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── step2.rst <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── step3.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── step3.rst <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── step4.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── step4.rst <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── step5.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── step5.rst <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── step6.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── step6.rst <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├── steps.meta <br> 
  │&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;└── steps.rst <br> 
  │&nbsp;&nbsp;&nbsp;│ <br> 
  │&nbsp;&nbsp;&nbsp;├── website-creation.meta <br> 
  │&nbsp;&nbsp;&nbsp;└── website-creation.rst <br> 
  │ <br> 
  ├── .gitignore <br> 
  └── conf.py <br> 
  </p> 
  
Directories in Github can have a README.rst or README.md file that contains a 
brief explanation of the purpose of the directory. 

Although the README files are passed to the "main" branch as .html files, 
their contents are not normally displayed by the website.


Metadata Template for .rst files
--------------------------------

All *reStructuredText .rst* filenames should only use **a to z**, **0-9** and 
a literal dash **-**.

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
Github will display the .rst metadata as a table using three hyphens before and 
after the metadata, however a bug seems to cause it to not incorporate at least 
the last line of metadata.

Metadata Template for .md files
-------------------------------

All *markdown .md* filenames should only use **a to z**, **0-9** and a literal 
dash **-**.

This is what the *slug* metadata expects.

When creating a new .md file copy and paste the template below:

```
title: *My Title
slug: *name of file without .md extension.
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
[Top](#top)
```
When using Github to display a markdown .md file, the metadata can be presented 
as a table at the top of the displayed content if three hyphens are placed 
above and below the metadata. In which case this is the .md template:
```
---
title: *My Title
slug: *name of file without .md extension.
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
[Top](#top)
```

[Top](#top)

