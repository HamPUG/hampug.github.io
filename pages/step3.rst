.. _top:

3. Creating a Website
=====================

Introduction
------------

At this stage you may have done the following in creating a website
::

    $ source venv1/bin/activate
    $ nikola init --quiet mywebsite
    $ cd mywebsite
    $ nikola build
    $ nikola serve

You would then have used a web-browser to connect to 127.0.0.1:8000 and check the website works OK.


Create some new pages for your web-site

Each page needs to contain meta-data. You can choose to have the meta-data at the start of your web-page, or as a separate file with a .meta extension. If you opt for the default, then a reST page is created with the meta-data at the begining. For example the *About* page with default settings
::

    (venv2) ian@X200:~/hampug1/static$ nikola new_page
    Creating New Page
    -----------------
    
    Title: About Us
    Scanning posts.....done!
    [2019-05-05T22:18:11Z] INFO: new_page: Your page's text is at: pages/about-us.rst

Now review the pages/about-us.rst file. The first 8 lines are composed of meta-data, followed by a blank line, and on the tenth line is the start of the page content, which is currently, *Write your text here*. 

.. code:: rest
    :number-lines:
   
    .. title: About Us
    .. slug: about-us
    .. date: 2019-05-06 10:18:11 UTC+12:00
    .. tags: 
    .. category: 
    .. link: 
    .. description: 
    .. type: text
    
    Write your page here
    
What if the first line of the content contained a reST syntax error? For example instead of "``Write your page here``" it was "``Write your *page here``", with the syntax error of the word "page" starting with an asterisk for emphasis and not having an ending asterisk. When the page is displayed on the web-browser there will be a warning message::

    Write your *page here.
    System Message: WARNING/2 (<string>, line 1); backlink
    Inline emphasis start-string without end-string.
    
Note that the above message states the issue is with line 1, when it is actually line 10 of the *about-us.rst* file.

This could cause confusion when writing reST as the error message line numbers do not match the actual line numbers.

One method of over-coming this confusing error information is to place the metadata in a separate file. When the new page is created with ``$ nikola new_page --title="About Us"`` a *-2* is appended to the command. This will then create the page using the two file format where one page is the content and the other page is the meta-data. For example::

    $ nikola new_page --title = "About Us" -2
    
    $ ls pages/about-us*
    pages/about-us.meta  pages/about-us.rst
    
    $ cat pages/about-us.rst
    Write your page here.
    
    $ cat pages/about-us.meta
    .. title: About Us
    .. slug: about-us
    .. date: 2019-05-06 12:14:47 UTC+12:00
    .. tags: 
    .. link: 
    .. description: 
    .. type: text

If there is now the same syntax error, "``Write your *page here``", then the error message will now have the correct line numbering for the .rst file::

    Write your *page here.
    System Message: WARNING/2 (<string>, line 1); backlink
    Inline emphasis start-string without end-string.

It is your choice whether or not to have two page format or one page, but if you opt for the one page format then be aware that error message line numbering will not match the line numbering of the reST editor you are using to create the content of the page.

From ``$ nikola help new_page`` this is the information on the -1 and -2 options.
::

  -1 Create the page with embedded metadata (single file format)  (config: onefile)
  -2 Create the page with separate metadata (two file format)  (config: twofile) 


Creating this Website
---------------------

The web-site generated with --quiet argument has the following folders in the top directory::

    cache files  galleries  listings  output  pages  posts  __pycache__

The folders: files, galleries, listings, pages, and posts contain no files. These are the folders that are normally used to make a conventional web-site.

The output folder has files in its galleries and listings folders and contains a index.html which becomes the home page of this web-site.

To convert this to a conventional web-site, then, for demonstration purposes, we initial want to have a home page of index.html in the output folder with one tab for an "About Us". To do so, the following editing of conf.py and new_page creation is performed.

In the pages folder we want to create the index.rst file as the home page. This will end up in the output folder as index.html. Plus an about-us.rst file which will end up in an about-us folder in the output folder as the file index.html. Thus we have 4 files in pages, nothing in the other folders files, galleries, images and posts, and the output file structure will be the home page index file in output and the folder. 

::

    hampug
        ├── pages
        │   ├── about-us.meta
        │   ├── about-us.rst
        │   ├── index.meta
        │   └── index.rst
        ├── files
        ├── galleries
        ├── images
        ├── posts
        └── output
            ├── index.html
            ├── index.rst
            └── about-us
                ├── index.html
                └── index.rst

Commence editing conf.py. Change the following Data about this site::

    BLOG_AUTHOR = "Your Name"  # (translatable)
    BLOG_TITLE = "Demo Site"  # (translatable)
    SITE_URL = "https://example.com/"
    BLOG_EMAIL = "joe@demo.site"
    BLOG_DESCRIPTION = "This is a demo site for Nikola."  # (translatable)
    
changed to::

    BLOG_AUTHOR = "HamPUG Team"  # (translatable)
    BLOG_TITLE = "HamPUG"  # (translatable)
    SITE_URL = "http://hampug1.pythonanywhere.com/"
    BLOG_EMAIL = "hampug@gmail.com"
    BLOG_DESCRIPTION = "Demonstrations of reST, Nikola, and a static website."  # (translatable)
    

Now change the navigation link from::

    NAVIGATION_LINKS = {
        DEFAULT_LANG: (
            ("/archive.html", "Archives"),
            ("/categories/index.html", "Tags"),
            ("/rss.xml", "RSS feed"),
        ),
    }
    
To the two initial link that will be created to get started::

    NAVIGATION_LINKS = {
        DEFAULT_LANG: (
            ("/index.html", "Home"),
            ("/about-us/", "About Us"),
        ),
    }

Next change the POSTS and PAGES from this::

    POSTS = (
        ("posts/*.rst", "posts", "post.tmpl"),
        ("posts/*.md", "posts", "post.tmpl"),
        ("posts/*.txt", "posts", "post.tmpl"),
        ("posts/*.html", "posts", "post.tmpl"),
    )
    PAGES = (
        ("pages/*.rst", "pages", "page.tmpl"),
        ("pages/*.md", "pages", "page.tmpl"),
        ("pages/*.txt", "pages", "page.tmpl"),
        ("pages/*.html", "pages", "page.tmpl"),
    )

To the following. We don't want to support posts on the web-site and for pages the the tuple (wildcard, destination, template) the destination is changed from "pages" to ""::

    POSTS = ()
    PAGES = (
        ("pages/*.rst", "", "page.tmpl"),
        ("pages/*.md", "", "page.tmpl"),
        ("pages/*.txt", "", "page.tmpl"),
        ("pages/*.html", "", "page.tmpl"),
    )

As Nikola defaults to creating a blog site, then by default it will have a blog page as an index.html in the top level directory, instead of the home page you create a part of building a regualr web-site. Therefore locate the following::

    # Final location for the main blog page and sibling paginated pages is
    # output / TRANSLATION[lang] / INDEX_PATH / index-*.html
    # (translatable)
    # INDEX_PATH = ""

Remove the comment and point the index page for the blog to not be in the top level directory, but in its own directory called "blog". If we don't do this we get an attempt to have two index.html files in the top directory::

    INDEX_PATH = "blog" 

Plus ensure that PRETTY_URLS is set to True::

    # Instead of putting files in <slug>.html, put them in <slug>/index.html.
    # No web server configuration is required. Also enables STRIP_INDEXES.
    # This can be disabled on a per-page/post basis by adding
    #    .. pretty_url: False
    # to the metadata.
    PRETTY_URLS = True

Now create an index page and an about page using the nikola *new_page* command. Start by cleaning out the existing output file::

    (venv2) username@host:~/hampug_quiet$ nikola clean
    Scanning posts....done!
    create_bundles:output/assets/js/all.js - removing file 'output/assets/js/all.js'
    create_bundles:output/assets/js/all-nocdn.js - removing file 'output/assets/js/all-nocdn.js'
    create_bundles:output/assets/css/all.css - removing file 'output/assets/css/all.css'
    create_bundles:output/assets/css/all-nocdn.css - removing file 'output/assets/css/all-nocdn.css'
    robots_file:output/robots.txt - removing file 'output/robots.txt'
    sitemap:output/sitemapindex.xml - removing file 'output/sitemapindex.xml'
    sitemap:output/sitemap.xml - removing file 'output/sitemap.xml'
    copy_assets:output/assets/js/fancydates.min.js - removing file 'output/assets/js/fancydates.min.js'
    copy_assets:output/assets/css/code.css - removing file 'output/assets/css/code.css'
    copy_assets:output/assets/xml/rss.xsl - removing file 'output/assets/xml/rss.xsl'
    copy_assets:output/assets/xml/atom.xsl - removing file 'output/assets/xml/atom.xsl'
    copy_assets:output/assets/js/justified-layout.min.js - removing file 'output/assets/js/justified-layout.min.js'
    copy_assets:output/assets/js/gallery.js - removing file 'output/assets/js/gallery.js'
    copy_assets:output/assets/js/html5shiv-printshiv.min.js - removing file 'output/assets/js/html5shiv-printshiv.min.js'
    copy_assets:output/assets/js/moment-with-locales.min.js - removing file 'output/assets/js/moment-with-locales.min.js'
    copy_assets:output/assets/js/baguetteBox.min.js - removing file 'output/assets/js/baguetteBox.min.js'
    copy_assets:output/assets/js/gallery.min.js - removing file 'output/assets/js/gallery.min.js'
    copy_assets:output/assets/js/fancydates.js - removing file 'output/assets/js/fancydates.js'
    copy_assets:output/assets/js/html5.js - removing file 'output/assets/js/html5.js'
    copy_assets:output/assets/css/nikola_rst.css - removing file 'output/assets/css/nikola_rst.css'
    copy_assets:output/assets/css/baguetteBox.min.css - removing file 'output/assets/css/baguetteBox.min.css'
    copy_assets:output/assets/css/html4css1.css - removing file 'output/assets/css/html4css1.css'
    copy_assets:output/assets/css/ipython.min.css - removing file 'output/assets/css/ipython.min.css'
    copy_assets:output/assets/css/nikola_ipython.css - removing file 'output/assets/css/nikola_ipython.css'
    copy_assets:output/assets/css/rst_base.css - removing file 'output/assets/css/rst_base.css'
    copy_assets:output/assets/css/rst.css - removing file 'output/assets/css/rst.css'
    copy_assets:output/assets/js/jquery.min.js - removing file 'output/assets/js/jquery.min.js'
    copy_assets:output/assets/js/popper.min.js - removing file 'output/assets/js/popper.min.js'
    copy_assets:output/assets/js/bootstrap.min.js - removing file 'output/assets/js/bootstrap.min.js'
    copy_assets:output/assets/css/bootstrap.min.css - removing file 'output/assets/css/bootstrap.min.css'
    copy_assets:output/assets/css/theme.css - removing file 'output/assets/css/theme.css'
    copy_assets:output/assets/css/bootblog.css - removing file 'output/assets/css/bootblog.css'
    render_galleries:output/galleries/rss.xml - removing file 'output/galleries/rss.xml'
    render_galleries:output/galleries/index.html - removing file 'output/galleries/index.html'
    render_galleries:output/galleries - removing dir 'output/galleries'
    render_taxonomies:output/categories/index.html - removing file 'output/categories/index.html'
    render_taxonomies:output/rss.xml - removing file 'output/rss.xml'
    render_taxonomies:output/archive.html - removing file 'output/archive.html'
    render_listings:output/listings/index.html - removing file 'output/listings/index.html'

There are still some folders and the index.html file in output::

    (venv2) username@host:~/hampug_quiet$ ls output
    assets  categories  index.html  listings
    
To really clean out the output folder then::

    (venv2) username@host:~/hampug_quiet$ rm -R output

    (venv2) username@host:~/hampug_quiet$ ls
    conf.py  files  galleries  listings  pages  posts  __pycache__
    
Now create an index page and an about page with

- nikola new_page --title = "Index" -2
- nikola new_page --title = "About Us" -2

::

    (venv2) ian@X200:~/hampug_quiet$ nikola new_page --title = "Index" -2
    Creating New Page
    -----------------
    
    Title: Index
    Scanning posts....done!
    [2019-05-08T01:12:55Z] INFO: new_page: Your page's metadata is at: pages/index.meta
    [2019-05-08T01:12:55Z] INFO: new_page: Your page's text is at: pages/index.rst
    
    (venv2) ian@X200:~/hampug_quiet$ nikola new_page --title = "About Us" -2
    Creating New Page
    -----------------
    
    Title: About Us
    Scanning posts....done!
    [2019-05-08T01:13:34Z] INFO: new_page: Your page's metadata is at: pages/about-us.meta
    [2019-05-08T01:13:34Z] INFO: new_page: Your page's text is at: pages/about-us.rst
    (venv2) ian@X200:~/hampug_quiet$ 

Ready to build and serve the web-site::

    (venv2) username@host:~/hampug_quiet$ nikola build
    Scanning posts....done!
    .  render_galleries:output/galleries
    .  render_galleries:output/galleries/index.html
    .  render_galleries:output/galleries/rss.xml
    .  copy_assets:output/assets/css/bootblog.css
    .  copy_assets:output/assets/css/theme.css
    .  copy_assets:output/assets/css/bootstrap.min.css
    .  copy_assets:output/assets/js/bootstrap.min.js
    .  copy_assets:output/assets/js/popper.min.js
    .  copy_assets:output/assets/js/jquery.min.js
    .  copy_assets:output/assets/css/rst.css
    .  copy_assets:output/assets/css/rst_base.css
    .  copy_assets:output/assets/css/nikola_ipython.css
    .  copy_assets:output/assets/css/ipython.min.css
    .  copy_assets:output/assets/css/html4css1.css
    .  copy_assets:output/assets/css/baguetteBox.min.css
    .  copy_assets:output/assets/css/nikola_rst.css
    .  copy_assets:output/assets/js/html5.js
    .  copy_assets:output/assets/js/fancydates.js
    .  copy_assets:output/assets/js/gallery.min.js
    .  copy_assets:output/assets/js/baguetteBox.min.js
    .  copy_assets:output/assets/js/moment-with-locales.min.js
    .  copy_assets:output/assets/js/html5shiv-printshiv.min.js
    .  copy_assets:output/assets/js/fancydates.min.js
    .  copy_assets:output/assets/js/gallery.js
    .  copy_assets:output/assets/js/justified-layout.min.js
    .  copy_assets:output/assets/xml/atom.xsl
    .  copy_assets:output/assets/xml/rss.xsl
    .  copy_assets:output/assets/css/code.css
    .  render_taxonomies:output/blog/index.html
    .  render_taxonomies:output/archive.html
    .  render_taxonomies:output/categories/index.html
    .  render_sources:output/about-us/index.rst
    .  render_sources:output/index.rst
    .  render_listings:output/listings/index.html
    .  render_posts:timeline_changes
    .  render_posts:cache/pages/about-us.html
    .  render_posts:cache/pages/index.html
    .  render_pages:output/about-us/index.html
    .  render_pages:output/index.html
    .  render_taxonomies:output/rss.xml
    .  create_bundles:output/assets/css/all-nocdn.css
    .  create_bundles:output/assets/css/all.css
    .  create_bundles:output/assets/js/all-nocdn.js
    .  create_bundles:output/assets/js/all.js
    .  sitemap:output/sitemap.xml
    .  sitemap:output/sitemapindex.xml
    .  robots_file:output/robots.txt

    (venv2) username@host:~/hampug_quiet$ nikola serve -b
    [2019-05-08T01:18:05Z] INFO: serve: Serving on http://127.0.0.1:8000/ ...
    [2019-05-08T01:18:05Z] INFO: serve: Opening http://127.0.0.1:8000/ in the default web browser...
    127.0.0.1 - - [08/May/2019 13:18:06] "GET / HTTP/1.1" 200 -
    
The website now launches. If we look at the output folder, which is the web-site, we now see the index.html that is the home page and the folder about-us that contains its own index.html for the about webpage::

    username@host:~/hampug_quiet/output$ ls -R
    .:
    about-us      assets  categories  index.html  listings    rss.xml           sitemap.xml
    archive.html  blog    galleries   index.rst   robots.txt  sitemapindex.xml


    ./about-us:
    index.html  index.rst

The about-us, and all other web-pages we create, have their own folders as conf.py has ``PRETTY_URLS = True``. This is the default in conf.py::

    # Instead of putting files in <slug>.html, put them in <slug>/index.html.
    # No web server configuration is required. Also enables STRIP_INDEXES.
    # This can be disabled on a per-page/post basis by adding
    #    .. pretty_url: False
    # to the metadata.
    PRETTY_URLS = True

From a browser the web-site appears as follows, with two tabs, the Home/Index tab and the About Us tab. 

.. figure:: /images/HamPUG_initial_index_page.png
    :alt: nikola_demo
    :align: center

    Home page of HamPUG website, where the URL ends with /index.html

.. figure:: /images/HamPUG_initial_about_page.png
    :alt: nikola_demo
    :align: center

    About Us page of HamPUG website, where the Pretty URL ends with /about-us/

Note that both pages display their titles in a blue font as links. i.e. Index and About Us. You might want to hide these titles and have your own headings for the pages. In this case you edit the /pages/index.meta and the /pages/about-us.meta files and add *.. hidetitle: True* The following is the website after adding the hidetitle: True meta data and placing a heading and a line of text into the .reST files.

.. figure:: /images/HamPUG_hidetitle_index.png
    :alt: nikola_demo
    :align: center

    Home page of HamPUG website with ``hidetitle: True`` in meta-data. Commenced editing index.rst file.

.. figure:: /images/HamPUG_hidetitle_about.png
    :alt: nikola_demo
    :align: center

    About Us page of HamPUG website with ``hidetitle: True`` in meta-data. Commenced editing about-us.rst file. 


The folder that contains your static web-site pages will default to being off the top level folder called "output":: 

    # Where the output site should be located
    # If you don't use an absolute path, it will be considered as relative
    # to the location of conf.py
    # OUTPUT_FOLDER = 'output'

You may wish to change this to another name, for example *static*, or place it in a folder outside of your default top level folder:: 

    # Place in folder named static off the top level folder 
    OUTPUT_FOLDER = 'static'

    # OR: place in folder in separate path relative to the top level folder
    OUTPUT_FOLDER = '.. my_website'

`[Top] <#top>`_
