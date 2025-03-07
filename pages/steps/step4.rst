.. _top:

4. Website Tailoring
====================

Introduction
------------

There are many ways to tailor your website to enhance it. Before moving on to writing web-pages using reStructuredText this section will highlight tailoring that may be performed mostly through adjustment of parameters in the *conf.py* file.

Navigation
----------

As you create more webpages, then you must update in conf.py your *NAVIGATION_LINKS*. With just an Index and an About Us, we had the following::

    NAVIGATION_LINKS = {
        DEFAULT_LANG: (
            ("/index.html", "Home"),
            ("/about-us/", "About Us"),
        ),
    }
    

With this website, this has become more complex as webpages have been added and it is now as follows::

    NAVIGATION_LINKS = {
        DEFAULT_LANG: (
            ("/index.html", "Home"),
            (
                (
                    ('/steps/', 'Overview of Steps'),
                    ('/step1/', '1. PythonAnywhere Account'),
                    ('/step2/', '2. Nikola Installation'),
                    ('/step3/', '3. Creating a Website'),
                    ('/step4/', '4. Website Tailoring'),
                    ('/step5/', '5. ReST Editor'),
                ),
                '<strong>Steps</strong>'
            ),
            ("/rest_editor/", "reST Editor"),
            ("/rest_basics/", "reST Basics"),
            ("/rest_directive/", "reST Directive"),
            ("/nikola_basics/", "Nikola Basics"),
            ("/pythonanywhere/", "PythonAnywhere"),
            ("/about-us/", "About Us"),
        ),
    }

Note the **steps** section above. The main *Steps* in the navigation bar is with strong emphasis. Then, when you click on *Steps*, there are six items in the drop down menu.


Images Folder
-------------

As a result of creating a website from the ``nikola init --quiet`` template a *galleries* folder has been created. Photos in a gallery are for displaying in a different manor than individual images that are embedded in the text of a web-page. An *images* folder should be created in the top level directory for storage of all images used by any web-page. The conf.py file sets images to be found in a folder called "images". All images have a thumbnail variant generated as part of the website creation by nikola. The default is of the thumbnail size of 400 pixels. This size may be adjusted in conf.py. These are the image related parameters in conf.py::

    IMAGE_FOLDERS = {'images': 'images'}
    # IMAGE_THUMBNAIL_SIZE = 400
    # IMAGE_THUMBNAIL_FORMAT = '{name}.thumbnail{ext}'   

As examples, in a reST webpage you insert an image with *image* or *figure* command. Note that the images are in the /images/ folder::

    .. image:: /images/photo_1.png 
        
    .. figure:: /images/photo_2.jpg 
        
        This is the title for the above photo_2.jpg image.


Favicons for Web-browser Tab
----------------------------

The conf.py file allows you to build a tuple of favourite icons which has the name *FAVICONS*. This is the icon that will be displayed on your browser tab::

    # FAVICONS contains (name, file, size) tuples.
    # Used to create favicon link like this:
    # <link rel="name" href="file" sizes="size"/>
    # FAVICONS = (
    #     ("icon", "/favicon.ico", "16x16"),
    #     ("icon", "/icon_128x128.png", "128x128"),
    # )

For example this website uses an icon of a pugs face::

    FAVICONS = (
         ("icon", "/images/pug_24x24.png", "24x24"),
    )

Displaying a Logo with the Webpage Title
----------------------------------------

The conf.py file allows a logo to be displayed as part of the title of the web-pages:: 

    # Nikola supports logo display.  If you have one, you can put the URL here.
    # Final output is <img src="LOGO_URL" id="logo" alt="BLOG_TITLE">.
    # The URL may be relative to the site root.
    # LOGO_URL = ''

By placing a logo image in the images folder and setting the LOGO_URL to point to the image then each page will display the logo with the website title. This places the pugs face logo to the left of the title::

    LOGO_URL = '/images/pug_50x37.png'

Hide the Webpage Title
----------------------

If the logo image contained your web-site title, for example the name of your company, then you may wish to hide the text and only allow the logo to be displayed::

    # If you want to hide the title of your website (for example, if your logo
    # already contains the text), set this to False.
    SHOW_BLOG_TITLE = False


Enabling the use of Content Distribution Networks ~ CDN
-------------------------------------------------------

Content Distribution Networks (CDN) can be used to provide the CSS for a websites web-pages. This reduces the amount of data that your web-server needs to send out with every page, as the CDN web-servers provide the CSS, etc. The conf.py file states::

    # Use content distribution networks for jQuery, twitter-bootstrap css and js,
    # and html5shiv (for older versions of Internet Explorer)
    # If this is True, jQuery and html5shiv are served from the Google CDN and
    # Bootstrap is served from BootstrapCDN (provided by MaxCDN)
    # Set this to False if you want to host your site without requiring access to
    # external resources.
    # USE_CDN = False
    #
    # Check for USE_CDN compatibility.
    # If you are using custom themes, have configured the CSS properly and are
    # receiving warnings about incompatibility but believe they are incorrect, you
    # can set this to False.
    # USE_CDN_WARNING = True
    
Thus, to enable CDN set the conf.py file to::

    USE_CDN = True

If you look at the header of your web-pages html you will now see the stylesheets as follows:

.. code:: html

    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/baguettebox.js/1.11.0/baguetteBox.min.css" integrity="sha256-cKiyvRKpm8RaTdU71Oq2RUVgvfWrdIXjvVdQF2oZ1Y4=" crossorigin="anonymous">
    <link href="../assets/css/all.css" rel="stylesheet" type="text/css">

Also javascript and jQuery are from external sources:

.. code:: html

    <script src="https://code.jquery.com/jquery-3.3.1.min.js" integrity="sha256-FgpCb/KJQlLNfOu91ta32o/NMZxltwRo8QtmkMRdAu8=" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha256-ZvOgfh+ptkpoa2Y4HkRY28ir89u/+VRyDE7sB7hEEcI=" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/baguettebox.js/1.11.0/baguetteBox.min.js" integrity="sha256-yQGjQhFs3LtyiN5hhr3k9s9TWZOh/RzCkD3gwwCKlkg=" crossorigin="anonymous"></script>
    <script src="../assets/js/all.js"></script>
    <script>
    baguetteBox.run('div#content', {
        ignoreClass: 'islink',
        captions: function(element) {
            return element.getElementsByTagName('img')[0].alt;
    }});
    </script>

The locally sourced ``<link href="../assets/css/all.css" rel="stylesheet" type="text/css">`` is for:

.. code:: html

    /* This CSS2.1_ stylesheet defines rules for Docutils elements without    */
    /* HTML equivalent. It is required to make the document semantic visible. */

The locally sourced javascript ``<script src="../assets/js/all.js"></script>`` is:

.. code:: javascript

    function fancydates(t,e){if(0!=t)for(var a=document.querySelectorAll(".dt-published, .dt-updated, .listdate"),o=a.length,r=0;r<o;r++){var d,l=moment(a[r].attributes.datetime.value);d=1==t?l.local().format(e):l.fromNow(),a[r].innerHTML=d}}

Note that the assets folder is not part of your development environment. Expected to get ``all.css`` and ``all.js`` from a folder off the virtual environment, like these::

    ./lib/python3.6/site-packages/nikola/data/themes/bootblog4/assets/css/bootblog.css
    ./lib/python3.6/site-packages/nikola/data/themes/base/assets/js/fancydates.js
    
... but unable to find them. Need to review how *Themes* are performed.


No RSS Feeds
------------

If your website has no Rich Site Summary feeds (RSS) then the following will not apply::

    # A simple copyright tag for inclusion in RSS feeds that works just
    # like CONTENT_FOOTER and CONTENT_FOOTER_FORMATS
    RSS_COPYRIGHT = 'Contents © {date} <a href="mailto:{email}">{author}</a> {license}'
    RSS_COPYRIGHT_PLAIN = 'Contents © {date} {author} {license}'
    RSS_COPYRIGHT_FORMATS = CONTENT_FOOTER_FORMATS

Comment out as follows::
    
    # A simple copyright tag for inclusion in RSS feeds that works just
    # like CONTENT_FOOTER and CONTENT_FOOTER_FORMATS
    # Ian Comment out - no RSS
    #RSS_COPYRIGHT = 'Contents © {date} <a href="mailto:{email}">{author}</a> {license}'
    #RSS_COPYRIGHT_PLAIN = 'Contents © {date} {author} {license}'
    #RSS_COPYRIGHT_FORMATS = CONTENT_FOOTER_FORMATS


Creating a License suitable for the Page Footer
-----------------------------------------------

In conf.py there is the ability to assign a *LICENSE*. An example is provided of using a Creative commons license that could be commented out to be put into use::

    # A HTML fragment describing the license, for the sidebar.
    # (translatable)
    LICENSE = ""
    # I recommend using the Creative Commons' wizard:
    # https://creativecommons.org/choose/
    # LICENSE = """
    # <a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/">
    # <img alt="Creative Commons License BY-NC-SA"
    # style="border-width:0; margin-bottom:12px;"
    # src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png"></a>"""

This is a variation of the above CC license, but the image will be on the same level as the text, but right aligned. This is used on this web-site in the Page Footer::

    LICENSE = """
    <a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/">
    <img alt="Creative Commons License BY-NC-SA"
    style="float: right; margin: 0px 0px 5px 5px; border-width:0;"
    src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png"></a>"""
    

Content of the Page Footer
--------------------------

The content of the page footer is designed in the conf.py file::

    # A small copyright notice for the page footer (in HTML).
    # (translatable)
    CONTENT_FOOTER = 'Contents &copy; {date}         <a href="mailto:{email}">{author}</a> - Powered by         <a href="https://getnikola.com" rel="nofollow">Nikola</a>         {license}'
    
    # Things that will be passed to CONTENT_FOOTER.format().  This is done
    # for translatability, as dicts are not formattable.  Nikola will
    # intelligently format the setting properly.
    # The setting takes a dict. The keys are languages. The values are
    # tuples of tuples of positional arguments and dicts of keyword arguments
    # to format().  For example, {'en': (('Hello'), {'target': 'World'})}
    # results in CONTENT_FOOTER['en'].format('Hello', target='World').
    # If you need to use the literal braces '{' and '}' in your footer text, use
    # '{{' and '}}' to escape them (str.format is used)
    # WARNING: If you do not use multiple languages with CONTENT_FOOTER, this
    #          still needs to be a dict of this format.  (it can be empty if you
    #          do not need formatting)
    # (translatable)
    CONTENT_FOOTER_FORMATS = {
        DEFAULT_LANG: (
            (),
            {
                "email": BLOG_EMAIL,
                "author": BLOG_AUTHOR,
                "date": time.gmtime().tm_year,
                "license": LICENSE
            }
        )
    }

For this web-site the settings are as follows::

    CONTENT_FOOTER = '&copy; {date} {author} - Powered by <a href="https://getnikola.com" rel="nofollow">Nikola</a>         {license}'

Summary
-------

The above is an introduction to changes you may wish to make to conf.py to tailor your web-site. Take time to read and familiarise yourself with the whole of the conf.py file, so other adjustments may be made to the web-site you create.

`[Top] <#top>`_




