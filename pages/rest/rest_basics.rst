..
    A rest_basic.meta file is being used.

..
    Comment: Introduce reST.
    
.. _top:    

reStructuredText 
================

Introduction
------------

Introducing **reStructuredText** *reST* as a method of creating web-pages. While
reST is a markup language it is considered to be *light-weight*. It is easy to 
read a reST document as the markup has minimal interference with the content of 
the document.

The Nikola application will convert a document in the reST format to a hyper-
text markup language ~ version 5 *HTML5* file. The HTML5 file will later reside 
in the web-servers directories. When a web-browser is used to retrieve the web-
page over the internet, the HTML5 file is transmitted from the web-server to the 
web-browser. A role of the web-browser is to interpret the HTML5 file and render 
the data so it is displayed in the web-browser window.

This is an introduction to the basic reST features, which should provide enough 
details to create a simple web-page.

Links to External reST Documentation
------------------------------------

The reST wikipedia entry_.

.. _entry: https://en.wikipedia.org/wiki/ReStructuredText

The reST web-site_ provides detailed information, and there are links to web-pages that provide a quick reference guide_, a one page cheat-sheet_ and a reference document for directives_.

.. _web-site: http://docutils.sourceforge.net/rst.html
.. _guide: http://docutils.sourceforge.net/docs/user/rst/quickref.html
.. _cheat-sheet: http://docutils.sourceforge.net/docs/user/rst/cheatsheet.txt
.. _directives: http://docutils.sourceforge.net/docs/ref/rst/directives.html

Files created in this lightweight markup language are normally given a *.rst* 
extension. 

Headings and Sub-headings
-------------------------

Most text in the document will be displayed by the web-browser at the default font-size. There are larger font sizes that are used for headings and sub-headings.

A heading with a large font-size is created by under-lining the heading text with equal signs.
::

    A Main Heading
    ==============

A sub-heading with a smaller font-size is created by underlining the sub-heading with hypens.
::

    A Sub-Heading
    -------------

Emphasis
--------

Words or a group of words may have emphasis applied. By surrounding a word with single asterisks will result in emphasis applied which a web-browser will normally render as italics. For example:

This is normal text and *this is with emphasis*.
::

    This is normal text and *this is with emphasis*.

If double asterisks are placed around a word or group of words, then stronger emphasis is applied. This is normally rendered by web-browsers by using a bold font.

This is normal text and **this is strong emphasis text**.

Literal Text
------------

Often literal text is desired to be displayed. If double grave marks are placed around a word or group of words then this will normally result in being rendered by the web-browser in a mono-spaced font.

This is normal text and ``this is literal text``.

::

    This is normal text and ``this is literal text``.

User Defined
------------

Single graves around a word or group of words will depend on the current definition. The default definition will be the same as with using single asterisk for emphasis.

This is normal text and `this text is bounded by single graves`.
::

    This is normal text and `this text is bounded by single graves`.

If the default role is changed to strong, then a word or group of words surrounded by single graves will be strong

.. default-role:: strong

This is normal text and after setting the default role `this is text is surrounded by single graves`.
::

    .. default-role:: strong

    This is normal text and after setting the default role `this is text surrounded by single graves`.


.. default-role::

After resetting the default role the text surrounded by graves `returns to normal emphasis`.
::

    .. default-role::

The way that the default role is changed with ``.. default-role::`` is known in reST as using a **Directive**.

Paragraphs and Horizontal White-space
-------------------------------------

The web-browser provides compliance with the HTML5 specifications. Thus it performs rendering of text in each paragraph it displays. One aspect of the rendering is with regard to the *white-space* between words. Normally there is only one space character between words in a paragraph. If you increase the number of spaces or insert horizontal tabs, then the additional spaces are removed and the paragraph is displayed with only one space character between each word.

Also there is a new-line character, which is inserted by typing the *Enter* key, is of importance in the HTML5 specification. If a paragraph is being typed, then often the typist will type the Enter key at about the 80th character position on a line so the next word typed is at the beginning of the  next line. The browser will remove this single newline character and replace it with a single space character. When the browser displays a paragraph then it determines how long a line of text may be before reaching the right-hand margin. It is the browser that decides what is the last word on a line and to insert a wrap around so the next word is at the start of the next line. This is especially useful when adjusting the width of a display. The amount of text in each line will be adjusted to fit within the boundaries of the width of the display.

In summary, when you enter the text of a paragraph into a reST document it does not matter if you have additional spaces, or tabs, or at what character position you wrap one line to the next as this will all be over-ridden by the web-browser adhering to the HTML5 rules.

For example, this is sentence one of a paragraph. The paragraph    contains     multiple
spaces    between some words and also    tabs    between words.
It  also     contains        lines
of  text    that    only
contain four words. When
this paragraph is converted from reST to an HTML file the spacing will be adjusted. If
for some reason it isn't then the web-browser will perform the adjustment.
::

    For example, this is sentence one of a paragraph. The paragraph    contains     multiple
    spaces    between some words and also    tabs    between words.
    It  also     contains        lines
    of  text    that    only
    contain four words. When
    this paragraph is converted from reST to an HTML file the spacing will be adjusted. If
    for some reason it is not then the web-browser will perform the adjustment.

Be careful with punctuation marks. For example a full-stop or question mark should be the next character after the last letter of a word. Do not complete the word and add a space and then add the punctuation mark. This is because the single punctuation mark may be treated as a single character word and be wrapped at the end of a line. This could result in having a line starting with a full-stop or question mark.

Paragraphs and Vertical White-space
-----------------------------------

A paragraph in a reST document normally ends by typing the Enter key twice. The next paragraph begins and there is one blank line between the paragraphs. If the Enter key is pressed more than twice, it will create multiple blank lines between the paragraphs in the reST document. In converting the reST document to HTML5 the multiple blank lines will be reduced to one blank line.

For example this is a paragraph of one sentence and it's followed by three blank lines.



This is the next paragraph, which in the reST document starts after three blank lines, however
it is displayed with only one blank line between paragraphs.
::

    For example this is a paragraph of one sentence and its followed by three blank lines.



    This is the next paragraph, which in the reST document starts after three blank lines, however
    it is displayed with only one blank line between paragraphs.

In summary, when creating a reST document it doesn't matter how many blank lines are placed between paragraphs, the web-browser will only display one blank line.


Links
-----

A link is automatically created if its full address is entered. For example https://google.com and https://stuff.co.nz is as follows:
::

    For example https://google.com and https://stuff.co.nz 
    

Named Links
-----------

A sentence with links to `Wikipedia`_ and the `Linux kernel archive`_ is 
created as follows:

.. _Wikipedia: https://www.wikipedia.org/
.. _Linux kernel archive: https://www.kernel.org/

::

    A sentence with links to `Wikipedia`_ and the `Linux kernel archive`_ is 
    created as follows:

    .. _Wikipedia: https://www.wikipedia.org/
    .. _Linux kernel archive: https://www.kernel.org/

Anonymous Links
---------------

Another sentence, but with an `anonymous link to the Python website`__ is as
follows:

__ https://www.python.org/

::

    Another sentence, but with an `anonymous link to the Python website`__ is as
    follows:

    __ https://www.python.org/

Comments
--------

Comments may be embedded into the reST document. They will not be displayed.
To insert a comment place two dots at the beginning of one line. On the next
line or lines, indent and then write the comment.

.. 
    This is a comment. It wont be displayed in the rendered html.
    
    The comment can extend over multiple lines. Just so long as 
        indentations continue to be applied.

The comment as it appears in the .rst document is as follows:

::

    Comments may be embedded into the reST document. They will not be displayed.
    To insert a comment place two dots at the beginning of one line. On the next
    line or lines, indent and then write the comment.

    .. 
        This is a comment. It wont be displayed in the rendered html.
        
        The comment can extend over multiple lines. Just so long as 
            indentations continue to be applied.

It is a bad practice to put a comment on the same line as the double dots. E.g. 

::

    .. This is a comment. 

Any comment defined in this way whose first line matches the syntax of any 
existing explicit markup construct (e.g., citation, directive, footnote, 
substitution) will be silently reinterpreted as that construct rather than as 
a comment.

Bullet Lists
------------

Bullets are "-", "*" or "+". A blank line is required before the first item 
and after the last, but is optional between items.

- This is item 1
- This is item 2
- This is item 3

- This is item 4. Note that
  continuing text must be aligned
  after the bullet and whitespace.

+ This is item 1 with the plus sign bullet
+ This is item 2 with the plus sign bullet

* This is item 1 with the asterisk bullet
* This is item 2 with the asterisk bullet


The bullet list is as follows:
::

    - This is item 1
    - This is item 2
    - This is item 3

    - This is item 4. Note that
      continuing text must be aligned
      after the bullet and whitespace.

    + This is item 1 with the plus sign bullet
    + This is item 2 with the plus sign bullet

    * This is item 1 with the asterisk bullet
    * This is item 2 with the asterisk bullet

 
Bullet list with sub-lists. Strong emphasis automatically gets added to a 
list that has a sub-list.

**List and sub-lists of Items**

- Item 1
- Item 2
    - Item 2-a
        - Item 2-a-x
        - Item 2-a-y
        - Item 2-a-z
    - Item 2-b
        - Item 2-b-x
        - Item 2-b-y
- Item 3
    - Item 3-a

The lists and sub-list is as follows:
::

    **List and sub-lists of Items**

    - Item 1
    - Item 2
        - Item 2-a
            - Item 2-a-x
            - Item 2-a-y
            - Item 2-a-z
        - Item 2-b
            - Item 2-b-x
            - Item 2-b-y
    - Item 3
        - Item 3-a


Enumerated Lists
----------------

This is an enumerated list. Placing a "#" in place of a number, will invoke
auto-enumeration.

1. An enumerated list item.
2. Second item.
#. Third item is auto-enumerated.
#. Another auto-enumerated list item.
#. Yet another auto-enumerated list item.

The above is as follows:
::

    1. An enumerated list item.
    2. Second item.
    #. Third item is auto-enumerated.
    #. Another auto-enumerated list item.
    #. Yet another auto-enumerated list item.

The same list but with a blank line between each item and using a right
parenthesis, which is converted to a dot.

1) An enumerated list item.

2) Second item.

#) Third item is auto-enumerated.

#) Another auto-enumerated list item.

#) Yet another auto-enumerated list item.

The above is as follows:
::

    1) An enumerated list item.

    2) Second item.

    #) Third item is auto-enumerated.

    #) Another auto-enumerated list item.

    #) Yet another auto-enumerated list item.

Enumerated list and sub-list.

1) An enumerated list item with sub-items.
    a) Sub item that goes on at length and thus needs
       to be wrapped. Note the indentation that must
       match the beginning of the text, not the 
       enumerator.

    #) This should be auto-enumerated to be sub-item b.
#) Main Item 2.
    #) Sub item a of item 2. Auto-enumerated, thus it defaults to a number.
    #) Sub item b of 2.
#) Main Item 3 with no sub-items.

The above is as follows:
::

    Enumerated list and sub-list.

    1) An enumerated list item.
        a) Sub item that goes on at length and thus needs
           to be wrapped. Note the indentation that must
           match the beginning of the text, not the 
           enumerator.

        #) This should be auto-enumerated to be sub-item b.
    #) Main Item 2.
        #) Sub item a of item 2. Auto-enumerated, thus it defaults to a number.
        #) Sub item b of 2.
    #) Main Item 3 with no sub-items.


Enumerated list with two sub-levels.

1. First enumerated list item.
    a. Sub item a
        i. Sub-sub-item
        #. Another sub-sub-item which is auto-enumerated.
        #. Yet another sub-sub-item which is auto-enumerated.

    #. This should be auto-enumerated to be sub-item b.
        i. sub-sub item of b
2. Second enumerated list item.
    a. Sub item 2-a
        i. sub-sub-item 2-a-i
        #. sub-sub-item 2-a-ii

The above is as follows:
::

    Enumerated list with two sub-levels.

    1. First enumerated list item.
        a. Sub item a
            i. Sub-sub-item
            #. Another sub-sub-item which is auto-enumerated.
            #. Yet another sub-sub-item which is auto-enumerated.

        #. This should be auto-enumerated to be sub-item b.
            i. sub-sub item of b
    2. Second enumerated list item.
        a. Sub item 2-a
            i. sub-sub-item 2-a-i
            #. sub-sub-item 2-a-ii


Literal blocks
--------------

To create a literal block, commence a line with two colons and make the next 
line blank. After that place indented lines of text. These indented lines of
text will normally be displayed via HTML5 as being in a box and using a 
mono-spaced font.
::

    A line of literal text
    Another line of literal text.

The above is as follows:
::

    ::

        A line of literal text
        Another line of literal text.

This may also be used inline at the end of a paragraph. i.e. Place two colons 
at the end of the paragraph. One is displayed, like so::

    some more literal text


Definition List
---------------

A list that associates a term with a definition.

Hello
    Word used when you meet someone.

Goodbye
    Word used when you farewell someone.

Bon Voyage
    Words used when someone leaves for a holiday.

The above is as follows:

::

    A list that associates a term with a definition.

    Hello
        Word used when you meet someone.

    Goodbye
        Word used when you farewell someone.

    Bon Voyage
        Words used when someone leaves for a holiday.

Field Lists
-----------

Field lists are used as part of an extension syntax, such as options for directives, or database-like records meant for further processing. Field lists may also be used as generic two-column table constructs in documents. 

:Authors:
    Joe Bloggs,
    Fred Fish

    (and a very long list of many other good folks)

:Version: 1.0 of 2019-04-28
:Dedication: To my father. 


The above is as follows:
::

    :Authors:
        Joe Bloggs,
        Fred Fish
    
        (and a very long list of many other good folks)
    
    :Version: 1.0 of 2019-04-28
    :Dedication: To my father. 

Line Blocks
-----------

| Line blocks are useful for addresses,
| verse, and adornment-free lists.
|
| Each new line begins with a
| vertical bar ("|").
|     Line breaks and initial indents
|     are preserved.
| Continuation lines are wrapped
  portions of long lines; they begin
  with spaces in place of vertical bars.

The above is as follows:
::

    | Line blocks are useful for addresses,
    | verse, and adornment-free lists.
    |
    | Each new line begins with a
    | vertical bar ("|").
    |     Line breaks and initial indents
    |     are preserved.
    | Continuation lines are wrapped
      portions of long lines; they begin
      with spaces in place of vertical bars.


Tables
------

There are two syntax's for tables in reStructuredText. Grid tables are complete but cumbersome to create. Simple tables are easy to create but limited (no row spans, etc.).

Grid table:

+------------+------------+-----------+
| Header 1   | Header 2   | Header 3  |
+============+============+===========+
| body row 1 | column 2   | column 3  |
+------------+------------+-----------+
| body row 2 | Cells may span columns.|
+------------+------------+-----------+
| body row 3 | Cells may  | - Cells   |
+------------+ span rows. | - contain |
| body row 4 |            | - blocks. |
+------------+------------+-----------+

Simple table:

=====  =====  ======
   Inputs     Output
------------  ------
  A      B    A or B
=====  =====  ======
False  False  False
True   False  True
False  True   True
True   True   True
=====  =====  ======

The above is as follows:
::

    +------------+------------+-----------+
    | Header 1   | Header 2   | Header 3  |
    +============+============+===========+
    | body row 1 | column 2   | column 3  |
    +------------+------------+-----------+
    | body row 2 | Cells may span columns.|
    +------------+------------+-----------+
    | body row 3 | Cells may  | - Cells   |
    +------------+ span rows. | - contain |
    | body row 4 |            | - blocks. |
    +------------+------------+-----------+


    Simple table:

    =====  =====  ======
       Inputs     Output
    ------------  ------
      A      B    A or B
    =====  =====  ======
    False  False  False
    True   False  True
    False  True   True
    True   True   True
    =====  =====  ======


Transitions
-----------

A transition marker is a horizontal line
of 4 or more repeated punctuation
characters.

------------

A transition should not begin or end a
section or document, nor should two
transitions be immediately adjacent. 

The above is as follows:
::

    A transition marker is a horizontal line
    of 4 or more repeated punctuation
    characters.

    ------------

    A transition should not begin or end a
    section or document, nor should two
    transitions be immediately adjacent. 


Inline Alternatives
-------------------

This sentence contains :strong:`strong text` with inline use of strong instead of using **two** asterisks.

This sentence contains :emphasis:`emphasis text` with inline use of emphasis instead of using *single* asterisks.

::

    This sentence contains :strong:`strong text` with inline use of strong instead of using **two** asterisks.
    
    This sentence contains :emphasis:`emphasis text` with inline use of emphasis instead of using *single* asterisks.
    
`[Top] <#top>`_    
