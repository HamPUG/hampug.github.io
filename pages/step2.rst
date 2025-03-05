.. _top:

2. Download and Install Nikola
==============================

We now switch to using your PC or Laptop as a development environment for the static website creation. This section describes the steps to take to install Nikola. More in-depth details may be found in the Nikola `documentation`_

.. _documentation: https://getnikola.com/getting-started.html

Create a Virtual Environment
----------------------------

It is recommended that you create and use a virtual environment. This provides a python environment that you can launch each time you login after starting up your computer. If the venv application is not installed then...
::

    $ sudo apt-get install python3-venv
    ...
    The following NEW packages will be installed:
      python3-venv python3.6-venv
    ...
    Do you want to continue? [Y/n] y
    ...

Check what was installed...
::

    $ ls /usr/lib/python3.6/venv/ -l
    total 32
    -rw-r--r-- 1 root root 19459 Oct 23  2018 __init__.py
    -rw-r--r-- 1 root root   145 Oct 23  2018 __main__.py
    drwxr-xr-x 2 root root  4096 Feb 10 13:15 __pycache__
    drwxr-xr-x 4 root root  4096 Feb 10 13:14 scripts

Create a virtual environment, in this case it will be in the directory off the home folder and be called *venv1*. With the python module venv the argument *--copies* is used to try to use copies rather than symlinks, even when symlinks are the default for the platform.
::

    $ python3.6 -m venv --copies venv1

In this case a total of 346 files were installed into 48 directories. The directory structure of the venv1 is as follows:
::

    $ tree -d venv1
    venv1
    ├── bin
    ├── include
    ├── lib
    │   └── python3.6
    │       └── site-packages
    │           ├── pip
    │           │   ├── commands
    │           │   │   └── __pycache__
    │           │   ├── compat
    │           │   │   └── __pycache__
    │           │   ├── models
    │           │   │   └── __pycache__
    │           │   ├── operations
    │           │   │   └── __pycache__
    │           │   ├── __pycache__
    │           │   ├── req
    │           │   │   └── __pycache__
    │           │   ├── utils
    │           │   │   └── __pycache__
    │           │   ├── vcs
    │           │   │   └── __pycache__
    │           │   └── _vendor
    │           │       └── __pycache__
    │           ├── pip-9.0.1.dist-info
    │           ├── pkg_resources
    │           │   ├── extern
    │           │   │   └── __pycache__
    │           │   ├── __pycache__
    │           │   └── _vendor
    │           │       ├── packaging
    │           │       │   └── __pycache__
    │           │       └── __pycache__
    │           ├── pkg_resources-0.0.0.dist-info
    │           ├── __pycache__
    │           ├── setuptools
    │           │   ├── command
    │           │   │   └── __pycache__
    │           │   ├── extern
    │           │   │   └── __pycache__
    │           │   ├── __pycache__
    │           │   └── _vendor
    │           │       ├── packaging
    │           │       │   └── __pycache__
    │           │       └── __pycache__
    │           └── setuptools-39.0.1.dist-info
    ├── lib64 -> lib
    └── share
        └── python-wheels
    
    48 directories

Note that there are directories for *Pip Installs Packages* (`PIP`_) and `setuptools`_ in this virtual environment tree.

.. _PIP: https://en.wikipedia.org/wiki/Pip_(package_manager)
.. _`setuptools`: https://github.com/pypa/setuptools/blob/master/docs/setuptools.txt

To enter the virtual environment whenever you bootup your computer to develop Nikola web-sites, open a terminal window and from your home directory enter:

.. code:: bash

    $ source venv1/bin/activate

Your prompt will now have venv1 in parenthesis to indicate that you are in a virtual environment.
::

    (venv1) username@host:~$ 

Note that to exit the venv enter: ``$ deactivate``


Use PIP to Install Nikola
-------------------------

Before using *Pip Installs Packages*, check you have PIP available by checking its version number.
::
    
    (venv1) username@host:~$ pip -V
    pip 9.0.1 from /home/<username>/venv1/lib/python3.6/site-packages (python 3.6)

PIP is used to install Nikola plus extra optional features into the venv1 from the Python Package Index (`PyPI`_). The --upgrade argument ensures all specified packages to be the newest available version. 

.. _`PyPI`: https://pypi.org/project/Nikola/

::

    (venv1) username@host:~$ pip install --upgrade "Nikola[extras]"

The venv1 directory tree has now increased from 48 directories with 346 files, to 1314 directories with 9819 files. If Nikola had been installed without the extras ``pip install --upgrade Nikola`` then venv1 would be 321 directories with 4518 files.

..
    Comment: The following tables were created from the console output that occurred during 
    the pip install. 
    A python program was written to take the list and convert it to a reST table layout. 
    Can add to the table directive the option :widths: auto

.. table:: Nikola base packages from ``$ pip install --upgrade Nikola``
    :align: left
    
    +-----------------+-----------------+-----------------+-----------------+
    |Babel            |Markdown         |MarkupSafe       |Nikola           |
    +-----------------+-----------------+-----------------+-----------------+
    |Pillow           |PyRSS2Gen        |Pygments         |Yapsy            |
    +-----------------+-----------------+-----------------+-----------------+
    |blinker          |certifi          |chardet          |cloudpickle      |
    +-----------------+-----------------+-----------------+-----------------+
    |docutils         |doit             |idna             |logbook          |
    +-----------------+-----------------+-----------------+-----------------+
    |lxml             |mako             |natsort          |piexif           |
    +-----------------+-----------------+-----------------+-----------------+
    |pyinotify        |python-dateutil  |pytz             |requests         |
    +-----------------+-----------------+-----------------+-----------------+
    |setuptools       |six              |unidecode        |urllib3          |
    +-----------------+-----------------+-----------------+-----------------+


.. table:: Nikola[Extras] adds these packages to the base packages from ``$ pip install --upgrade "Nikola[extras]"``
    :align: left

    +-----------------+-----------------+-----------------+-----------------+
    |Jinja2           |PyYAML           |Send2Trash       |aiohttp          |
    +-----------------+-----------------+-----------------+-----------------+
    |argh             |async-timeout    |attrs            |backcall         |
    +-----------------+-----------------+-----------------+-----------------+
    |bleach           |decorator        |defusedxml       |entrypoints      |
    +-----------------+-----------------+-----------------+-----------------+
    |ghp-import2      |husl             |idna-ssl         |ipykernel        |
    +-----------------+-----------------+-----------------+-----------------+
    |ipython          |ipython-genutils |jedi             |jsonschema       |
    +-----------------+-----------------+-----------------+-----------------+
    |jupyter-client   |jupyter-core     |micawber         |mistune          |
    +-----------------+-----------------+-----------------+-----------------+
    |multidict        |nbconvert        |nbformat         |notebook         |
    +-----------------+-----------------+-----------------+-----------------+
    |pandocfilters    |parso            |pathtools        |pexpect          |
    +-----------------+-----------------+-----------------+-----------------+
    |phpserialize     |pickleshare      |prometheus-client|prompt-toolkit   |
    +-----------------+-----------------+-----------------+-----------------+
    |ptyprocess       |pygal            |pyphen           |pyrsistent       |
    +-----------------+-----------------+-----------------+-----------------+
    |pyzmq            |ruamel.yaml      |smartypants      |terminado        |
    +-----------------+-----------------+-----------------+-----------------+
    |testpath         |toml             |tornado          |traitlets        |
    +-----------------+-----------------+-----------------+-----------------+
    |typing-extensions|typogrify        |watchdog         |wcwidth          |
    +-----------------+-----------------+-----------------+-----------------+
    |webencodings     |yarl             |                 |                 |
    +-----------------+-----------------+-----------------+-----------------+



Starting Nikola
---------------

Check that Nikola retrieves its version number without errors.
::

    (venv1) username@host:~$ nikola version
    Nikola v8.0.2


Review the Nikola on-line help
::

    (venv1) username@host:~$ nikola help
    Nikola is a tool to create static websites and blogs. For full documentation and more information, please visit https://getnikola.com/
    
    Available commands:
      nikola auto                 builds and serves a site; automatically detects site changes, rebuilds, and optionally refreshes a browser
      nikola build                run tasks
      nikola check                check links and files in the generated site
      nikola clean                clean action / remove targets
      nikola console              start an interactive Python console with access to your site
      nikola default_config       Print the default Nikola configuration.
      nikola deploy               deploy the site
      nikola doit_auto            automatically execute tasks when a dependency changes
      nikola dumpdb               dump dependency DB
      nikola forget               clear successful run status from internal DB
      nikola github_deploy        deploy the site to GitHub Pages
      nikola help                 show help
      nikola ignore               ignore task (skip) on subsequent runs
      nikola import_wordpress     import a WordPress dump
      nikola info                 show info about a task
      nikola init                 create a Nikola site in the specified folder
      nikola list                 list tasks from dodo file
      nikola new_page             create a new page in the site
      nikola new_post             create a new blog post or site page
      nikola orphans              list all orphans
      nikola plugin               manage plugins
      nikola reset-dep            recompute and save the state of file dependencies without executing actions
      nikola rst2html             compile reStructuredText to HTML files
      nikola serve                start the test webserver
      nikola status               display site status
      nikola strace               use strace to list file_deps and targets
      nikola subtheme             given a swatch name from bootswatch.com or hackerthemes.com and a parent theme, creates a custom theme
      nikola tabcompletion        generate script for tab-completion
      nikola theme                manage themes
      nikola version              print the Nikola version number
    
      nikola help                 show help / reference
      nikola help <command>       show command usage
      nikola help <task-name>     show task usage


How to check if Nikola has plugins.
::

    (venv1) username@host:~$ nikola help plugin
    Purpose: manage plugins
    Usage:   nikola plugin [-u url] [--user] [-i name] [-r name] [--upgrade] [-l] [--list-installed]
    
    Options:
      -i ARG, --install=ARG     Install a plugin.  (config: install)
      -r ARG, --uninstall=ARG   Uninstall a plugin.  (config: uninstall)
      -l, --list                Show list of available plugins.  (config: list)
      -u ARG, --url=ARG         URL for the plugin repository (default: https://plugins.getnikola.com/v8/plugins.json)  (config: url)
      --user                    Install user-wide, available for all sites.  (config: user)
      --upgrade                 Upgrade all installed plugins.  (config: upgrade)
      --list-installed          List the installed plugins with their location.  (config: list_installed)

Nikola Plugin list of available plugins. Total of 96.
::

    (venv1) username@host:~$ nikola plugin --list
    Available Plugins:
    ------------------
    asciidoc
    babeldates
    bbcode
    book_figure
    category_prevnext
    commonmark
    contentful
    continuous_import
    datocms
    deploy_hooks
    emoji
    errorpages
    forms
    gallery_directive
    gallery_shortcode
    german_slugify
    graphviz
    helloworld
    hierarchical_pages
    html_roles
    iarchiver
    ical
    import_blogger
    import_feed
    import_goodreads
    import_gplus
    import_jekyll
    import_page
    import_tumblr
    import_twitpic
    irclogs
    issue_role
    jade
    jsonfeed
    kramdown
    latex
    latex_formula_renderer
    less
    link_figure
    localkatex
    localsearch
    markmin
    mediawiki
    medium
    meta_template
    microdata
    mincss
    misaka
    mistune
    mustache
    navstories
    notebook_shortcode
    odt
    opentimestamps
    orgmode
    pdoc
    ping
    pkgindex
    pkgindex_compiler
    pkgindex_scan
    pkgindex_zip
    planetoid
    postcast
    pretty_breadcrumbs
    projectpages
    publication_list
    pyplots
    recent_posts_json
    rest_html5
    rss_ogg
    rstdiff
    sass
    section_prevnext
    series
    sidebar
    similarity
    slides
    slimish
    speechsynthesizednetcast
    spell_check
    sphinx_roles
    static_comments
    static_tag_cloud
    subindexes
    tagcloud
    tags
    textile
    tx3_tag_cloud
    txt2tags
    upgrade_metadata
    upgrade_metadata_v8
    vcs
    webapp
    wiki
    windows_live_tiles
    wordpress_compiler
    
Nikola plugins that are installed and their location. Total of 67
::

    (venv1) username@host:~$ nikola plugin --list-installed
    Installed Plugins:
    ------------------
    auto                 at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/auto/
    chart                at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/shortcode/chart.py
    check                at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/check.py
    classify_archive     at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/archive.py
    classify_authors     at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/authors.py
    classify_categories  at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/categories.py
    classify_indexes     at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/indexes.py
    classify_page_index  at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/page_index.py
    classify_tags        at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/tags.py
    classify_taxonomies  at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/misc/taxonomies_classifier.py
    console              at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/console.py
    copy_assets          at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/copy_assets.py
    copy_files           at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/copy_files.py
    create_bundles       at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/bundles.py
    default_config       at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/default_config.py
    deploy               at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/deploy.py
    emoji                at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/shortcode/emoji/
    gist                 at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/shortcode/gist.py
    github_deploy        at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/github_deploy.py
    gzip                 at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/gzip.py
    html                 at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/html.py
    import_wordpress     at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/import_wordpress.py
    init                 at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/init.py
    ipynb                at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/ipynb.py
    jinja                at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/template/jinja.py
    listing_shortcode    at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/shortcode/listing.py
    mako                 at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/template/mako.py
    markdown             at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/markdown/
    mdx_gist             at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/markdown/mdx_gist.py
    mdx_nikola           at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/markdown/mdx_nikola.py
    mdx_podcast          at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/markdown/mdx_podcast.py
    new_page             at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/new_page.py
    new_post             at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/new_post.py
    orphans              at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/orphans.py
    pandoc               at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/pandoc.py
    php                  at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/php.py
    plugin               at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/plugin.py
    post_list            at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/shortcode/post_list.py
    redirect             at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/redirect.py
    render_galleries     at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/galleries.py
    render_listings      at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/listings.py
    render_pages         at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/pages.py
    render_posts         at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/posts.py
    render_sources       at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/sources.py
    render_taxonomies    at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/taxonomies.py
    rest                 at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/rest/
    rest_chart           at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/rest/chart.py
    rest_doc             at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/rest/doc.py
    rest_gist            at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/rest/gist.py
    rest_listing         at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/rest/listing.py
    rest_media           at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/rest/media.py
    rest_post_list       at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/rest/post_list.py
    rest_soundcloud      at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/rest/soundcloud.py
    rest_thumbnail       at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/rest/thumbnail.py
    rest_vimeo           at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/rest/vimeo.py
    rest_youtube         at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/compile/rest/youtube.py
    robots               at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/robots.py
    rst2html             at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/rst2html/
    scale_images         at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/scale_images.py
    scan_posts           at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/misc/scan_posts.py
    serve                at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/serve.py
    sitemap              at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/task/sitemap/
    status               at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/status.py
    subtheme             at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/subtheme.py
    theme                at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/theme.py
    thumbnail            at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/shortcode/thumbnail.py
    version              at /home/<username>/venv1/lib/python3.6/site-packages/nikola/plugins/command/version.py


Website Development and Testing
-------------------------------

After installing Nikola, you should create a site. A site is a collection of all assets needed to create your site: a configuration file, posts, pages, images, and all other files and customizations. This is the important data, so put it where you put that kind of thing.

To create a site, you need to run ``nikola init --demo <directory_name>``. A wizard will be launched, letting you configure your site easily. The ``--demo`` option is used to fill your site with some demo content. If you do not want this complex web-site, you can make a more simplistic web-site using the ``--quiet`` argument, ``nikola init --quiet <directory_name>``.

::

    (venv2) username@host:~$ nikola init --demo hampug_demo
    Creating Nikola Site
    ====================
    
    This is Nikola v8.0.2.  We will now ask you a few easy questions about your new site.
    If you do not want to answer and want to go with the defaults instead, simply restart with the `-q` parameter.
    --- Questions about the site ---
    Site title [My Nikola Site]: 
    Site author [Nikola Tesla]: 
    Site author's e-mail [n.tesla@example.com]: 
    Site description [This is a demo site for Nikola.]: 
    Site URL [https://example.com/]: 
    Enable pretty URLs (/page/ instead of /page.html) that don't need web server configuration? [Y/n] y
    --- Questions about languages and locales ---
    We will now ask you to provide the list of languages you want to use.
    Please list all the desired languages, comma-separated, using ISO 639-1 codes.  The first language will be used as the default.
    Type '?' (a question mark, sans quotes) to list available languages.
    Language(s) to use [en]: 
    
    Please choose the correct time zone for your blog. Nikola uses the tz database.
    You can find your time zone here:
    https://en.wikipedia.org/wiki/List_of_tz_database_time_zones
    
    Time zone [Pacific/Auckland]: 
        Current time in Pacific/Auckland: 12:00:53
    Use this time zone? [Y/n] 
    --- Questions about comments ---
    You can configure comments now.  Type '?' (a question mark, sans quotes) to list available comment systems.  If you do not want any comments, just leave the field blank.
    Comment system: 
    
    That's it, Nikola is now configured.  Make sure to edit conf.py to your liking.
    If you are looking for themes and addons, check out https://themes.getnikola.com/ and https://plugins.getnikola.com/.
    Have fun!
    [2019-05-02T00:01:06Z] INFO: init: A new site with example data has been created at hampug_demo.
    [2019-05-02T00:01:06Z] INFO: init: See README.txt in that folder for more information.
    

The hampug_demo directory is created and it contains 7 folders, a README.txt and the conf.py file. Note that there is no *output* folder. When the website is built it defaults to residing in a the folder *output*.
::

    (venv2) username@host:~/hampug_demo$ ls -l
    total 84
    -rw-rw-r-- 1 ian ian 53216 May  2 12:01 conf.py
    drwxrwxr-x 3 ian ian  4096 May  2 08:51 files
    drwxrwxr-x 3 ian ian  4096 May  2 08:51 galleries
    drwxrwxr-x 2 ian ian  4096 May  2 08:51 images
    drwxrwxr-x 3 ian ian  4096 May  2 08:51 listings
    drwxrwxr-x 2 ian ian  4096 May  2 08:51 pages
    drwxrwxr-x 2 ian ian  4096 May  2 08:51 posts
    -rw-rw-r-- 1 ian ian   309 May  2 08:50 README.txt
    drwxrwxr-x 2 ian ian  4096 May  2 08:51 templates

The pages folder contains all the webpages for the website as 14 x reStructuredText files with .rst extensions.
::

    (venv2) username@host:~/hampug_demo$ ls pages/
    1.rst               creating-a-theme.rst     internals.rst      path_handlers.rst  social_buttons.rst
    bootstrap-demo.rst  dr-nikolas-vendetta.rst  listings-demo.rst  quickref.rst       theming.rst
    charts.rst          extending.rst            manual.rst         quickstart.rst

The posts folder contains only one reST file.
::

    (venv2) username@host:~/hampug_demo$ ls posts/
    1.rst

The README.txt states::

    This folder contains the source used to generate a static site using Nikola.
    
    Installation and documentation at https://getnikola.com/
    
    Configuration file for the site is ``conf.py``.
    
    To build the site::
    
        nikola build
    
    To see it::
    
        nikola serve -b
    
    To check all available commands::
    
        nikola help


Note that the nikola command *auto* builds and serves a site; automatically detects site changes, rebuilds, and optionally refreshes a browser

Nikola **build** command.
::

    (venv2) username@host:~/hampug_demo$ nikola build
    Scanning posts........done!
    .  copy_files:output/favicon.ico
    .  copy_files:output/images/nikola.png
    .  render_listings:output/listings/index.html
    .  render_listings:output/listings/hello.py.html
    .  render_listings:output/listings/hello.py
    .  render_listings:output/listings/__pycache__/index.html
    .  render_taxonomies:output/archive.html
    .  render_taxonomies:output/categories/index.html
    .  render_posts:timeline_changes
    .  render_posts:cache/pages/path_handlers.html
    .  render_posts:cache/pages/dr-nikolas-vendetta.html
    .  render_posts:cache/pages/creating-a-theme.html
    .  render_posts:cache/pages/charts.html
    .  render_posts:cache/pages/social_buttons.html
    .  render_posts:cache/pages/listings-demo.html
    .  render_posts:cache/pages/1.html
    .  render_posts:cache/pages/bootstrap-demo.html
    .  render_posts:cache/pages/extending.html
    .  render_posts:cache/pages/internals.html
    .  render_posts:cache/pages/manual.html
    .  render_posts:cache/pages/quickref.html
    .  render_posts:cache/pages/quickstart.html
    .  render_posts:cache/posts/1.html
    .  render_posts:cache/pages/theming.html
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
    .  scale_images:output/images/illus_001.jpg
    .  scale_images:output/images/frontispiece.jpg
    .  render_sources:output/pages/path-handlers/index.rst
    .  render_sources:output/pages/dr-nikolas-vendetta/index.rst
    .  render_sources:output/pages/creating-a-theme/index.rst
    .  render_sources:output/pages/charts/index.rst
    .  render_sources:output/pages/social_buttons/index.rst
    .  render_sources:output/pages/listings-demo/index.rst
    .  render_sources:output/pages/about-nikola/index.rst
    .  render_sources:output/pages/bootstrap-demo/index.rst
    .  render_sources:output/pages/extending/index.rst
    .  render_sources:output/pages/internals/index.rst
    .  render_sources:output/pages/handbook/index.rst
    .  render_sources:output/pages/quickref/index.rst
    .  render_sources:output/pages/quickstart/index.rst
    .  render_sources:output/posts/welcome-to-nikola/index.rst
    .  render_sources:output/pages/theming/index.rst
    .  render_galleries:output/galleries
    .  render_galleries:output/galleries/demo
    .  render_galleries:output/galleries/index.html
    .  render_galleries:output/galleries/rss.xml
    .  render_galleries:output/galleries/demo/tesla4_lg.thumbnail.jpg
    .  render_galleries:output/galleries/demo/tesla4_lg.jpg
    .  render_galleries:output/galleries/demo/tesla_tower1_lg.thumbnail.jpg
    .  render_galleries:output/galleries/demo/tesla_tower1_lg.jpg
    .  render_galleries:output/galleries/demo/tesla_lightning1_lg.thumbnail.jpg
    .  render_galleries:output/galleries/demo/tesla_lightning1_lg.jpg
    .  render_galleries:output/galleries/demo/tesla_lightning2_lg.thumbnail.jpg
    .  render_galleries:output/galleries/demo/tesla_lightning2_lg.jpg
    .  render_galleries:output/galleries/demo/tesla_conducts_lg.thumbnail.jpg
    .  render_galleries:output/galleries/demo/tesla_conducts_lg.jpg
    .  render_galleries:cache/galleries/demo/index.html
    .  render_galleries:output/galleries/demo/index.html
    .  render_galleries:output/galleries/demo/rss.xml
    .  render_taxonomies:output/categories/blog/index.html
    .  render_taxonomies:output/categories/nikola/index.html
    .  render_taxonomies:output/2012/index.html
    .  render_taxonomies:output/index.html
    .  render_taxonomies:output/categories/python/index.html
    .  render_taxonomies:output/categories/demo/index.html
    .  render_taxonomies:output/categories/cat_nikola/index.html
    .  render_pages:output/pages/creating-a-theme/index.html
    .  render_taxonomies:output/categories/nikola.xml
    .  render_pages:output/pages/about-nikola/index.html
    .  render_taxonomies:output/categories/demo.xml
    .  render_pages:output/pages/internals/index.html
    .  render_pages:output/pages/quickref/index.html
    .  render_pages:output/pages/quickstart/index.html
    .  render_taxonomies:output/rss.xml
    .  render_pages:output/pages/dr-nikolas-vendetta/index.html
    .  render_pages:output/pages/handbook/index.html
    .  render_pages:output/pages/theming/index.html
    .  render_pages:output/pages/extending/index.html
    .  render_taxonomies:output/categories/python.xml
    .  render_pages:output/pages/bootstrap-demo/index.html
    .  render_pages:output/pages/listings-demo/index.html
    .  render_taxonomies:output/categories/cat_nikola.xml
    .  render_pages:output/pages/charts/index.html
    .  render_pages:output/pages/social_buttons/index.html
    .  render_pages:output/pages/path-handlers/index.html
    .  render_pages:output/posts/welcome-to-nikola/index.html
    .  render_taxonomies:output/categories/blog.xml
    .  create_bundles:output/assets/css/all-nocdn.css
    .  create_bundles:output/assets/css/all.css
    .  create_bundles:output/assets/js/all-nocdn.js
    .  create_bundles:output/assets/js
    .  sitemap:output/sitemap.xml
    .  sitemap:output/sitemapindex.xml
    .  robots_file:output/robots.txt

Note that the *output* folder has now been created. It contains all the html files to be provided by the webserver. Also created are a *cache* folder for the website and a __pycache__ folder from  running the conf.py which contains conf.cpython-36.pyc.
::

    (venv2) username@host:~/hampug_demo$ ls
    cache  conf.py  files  galleries  images  listings  output  pages  posts  __pycache__  README.txt  templates


Nikola **serve** command. The *-b* argument launches your web-browser.
::

    (venv2) username@host:~/hampug_demo$ nikola serve -b
    [2019-05-02T00:28:02Z] INFO: serve: Serving on http://127.0.0.1:8000/ ...
    [2019-05-02T00:28:02Z] INFO: serve: Opening http://127.0.0.1:8000/ in the default web browser...
    127.0.0.1 - - [02/May/2019 12:28:03] "GET / HTTP/1.1" 200 -
    127.0.0.1 - - [02/May/2019 12:28:03] "GET /assets/css/all-nocdn.css HTTP/1.1" 200 -
    127.0.0.1 - - [02/May/2019 12:28:03] "GET /assets/js/all-nocdn.js HTTP/1.1" 200 -
    127.0.0.1 - - [02/May/2019 12:28:04] "GET /posts/welcome-to-nikola/ HTTP/1.1" 200 -

You can compare the contents of the .rst files in the pages folder with their .html files in the output folder to gain an appreciation of how reStructuredText is converted to html.

This demo will have created *My Nikola Site*. It is recommended that checkout the **Read the manual** webpage, and also the other demo pages.


Common Nikola commands
----------------------

Running the nikola application
------------------------------

In creating a virtual environment the path for looking up the execution of bash commands is appended to include ``/home/<username>/venv1/bin/``. This can be determined with the ``$ echo $PATH`` command.
::

    $ echo $PATH
    /home/<username>/venv1/bin:
    /home/<username>/bin:
    /usr/local/sbin:
    /usr/local/bin:
    /usr/sbin:
    /usr/bin:
    /sbin:
    /bin:
    /usr/games:
    /usr/local/games:
    /snap/bin

In the virtual environment the ``$ pip install "nikola[Extras]"`` command was executed and as part of this installation of Nikola the python file "nikola" was copied to ``/home/<username>/venv1/bin/``. This nikola file is as follows

.. code:: python

    #!/home/<username>/venv1/bin/python3.6
    
    # -*- coding: utf-8 -*-
    import re
    import sys
    
    from nikola.__main__ import main
    
    if __name__ == '__main__':
        sys.argv[0] = re.sub(r'(-script\.pyw?|\.exe)?$', '', sys.argv[0])
        sys.exit(main())
    
The line of code ``from nikola.__main__ import main``, finds the file ``~/venv1/lib/python3.6/site-packages/nikola/__main__.py`` and executes loading of 22 x python modules. It also initializes a dictionary ``config = {}`` and loads the ``def main(args=None):`` function. The main() function is then executed with the line ``sys.exit(main())``. 

The ``main()`` function includes setting up a variable for the nikola configuration file with ``conf_filename = 'conf.py'``. This conf.py file resides in the root of your web-site development folders.
    

    
.. code:: python

    try:
        loader = importlib.machinery.SourceFileLoader("conf", conf_filename)
        conf = loader.load_module()
        config = conf.__dict__

    >>> import importlib
    >>> dir(importlib)
    ['_RELOADING', '__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__import__', '__loader__', '__name__', '__package__', '__path__', '__spec__', '_bootstrap', '_bootstrap_external', '_imp', '_r_long', '_w_long', 'abc', 'find_loader', 'import_module', 'invalidate_caches', 'machinery', 'reload', 'sys', 'types', 'util', 'warnings']
    
    >>> dir(importlib.machinery)
    ['BYTECODE_SUFFIXES', 'BuiltinImporter', 'DEBUG_BYTECODE_SUFFIXES', 'EXTENSION_SUFFIXES', 'ExtensionFileLoader', 'FileFinder', 'FrozenImporter', 'ModuleSpec', 'OPTIMIZED_BYTECODE_SUFFIXES', 'PathFinder', 'SOURCE_SUFFIXES', 'SourceFileLoader', 'SourcelessFileLoader', 'WindowsRegistryFinder', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', '_imp', 'all_suffixes']
    
    >>> dir(importlib.machinery.SourceFileLoader)
    ['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', '_cache_bytecode', 'create_module', 'exec_module', 'get_code', 'get_data', 'get_filename', 'get_source', 'is_package', 'load_module', 'path_mtime', 'path_stats', 'set_data', 'source_to_code']

Using Help for more information
::

    >>> help(importlib.machinery.SourceFileLoader)

    Help on class SourceFileLoader in module importlib._bootstrap_external:
    
    class SourceFileLoader(FileLoader, SourceLoader)
     |  Concrete implementation of SourceLoader using the file system.
     |  
     |  Method resolution order:
     |      SourceFileLoader
     |      FileLoader
     |      SourceLoader
     |      _LoaderBasics
     |      builtins.object
     |  
     |  Methods defined here:
     |  
     |  path_stats(self, path)
     |      Return the metadata for the path.
     |  
     |  set_data(self, path, data, *, _mode=438)
     |      Write bytes data to a file.


    >>> help(importlib.machinery.SourceFileLoader.load_module)

    Help on function load_module in module importlib._bootstrap_external:
    
    load_module(self, name=None, *args, **kwargs)
        Load a module from a file.
        
        This method is deprecated.  Use exec_module() instead.

    >>> help(importlib.machinery.SourceFileLoader.exec_module)

    Help on function exec_module in module importlib._bootstrap_external:
    
    exec_module(self, module)
        Execute the module.
 

TODO: What role does __init__.py in ``~/venv1/lib/python3.6/site-packages/nikola/`` pay?

Introducing conf.py
-------------------

The configuration file *conf.py* contains constants. These constants in the conf.py file are in uppercase. For example ``BLOG_AUTHOR = "Joe Blogs"``. Through editing this file and changing values assigned to these constants then you manage the look and operation of your web-site. This file is around 1400 lines in length. There are almost 200 constants that can have values applied to them in conf.py. In many cases the default value will match your website requirements, so you won't be needing to set all the constants. You will get to know the contents of conf.py file very well, but it's the only file you need to get to know.

The Nikola application has dictionaries with keys that are normally the same as the names of the constants in conf.py. However the keys are in lower-case. The values of the constants obtained from conf.py become values in dictionaries that Nikola uses to tailor the application.

It may be worthwhile to look through the list of the names of the constants you will find in conf.py.


.. csv-table:: Table of conf.py variables
   :widths: auto


    ADDITIONAL_METADATA,ARCHIVES_ARE_INDEXES,ARCHIVE_FILENAME,ARCHIVE_PATH
    ATOM_EXTENSION,ATOM_FILENAME_BASE,ATOM_PATH,AUTHOR_PAGES_ARE_INDEXES
    AUTHOR_PAGES_DESCRIPTIONS,AUTHOR_PATH,BASE_URL,BLOG_AUTHOR
    BLOG_DESCRIPTION,BLOG_EMAIL,BLOG_TITLE,BODY_END
    CACHE_FOLDER,CATEGORIES_INDEX_PATH,CATEGORY_ALLOW_HIERARCHIES,CATEGORY_DESCRIPTIONS
    CATEGORY_DESTPATH_AS_DEFAULT,CATEGORY_DESTPATH_FIRST_DIRECTORY_ONLY,CATEGORY_DESTPATH_NAMES,CATEGORY_DESTPATH_TRIM_PREFIX
    CATEGORY_OUTPUT_FLAT_HIERARCHY,CATEGORY_PAGES_ARE_INDEXES,CATEGORY_PAGES_FOLLOW_DESTPATH,CATEGORY_PATH
    CATEGORY_PREFIX,CATEGORY_PREFIX.,CATEGORY_TITLES,CATEGORY_TRANSLATIONS
    CATEGORY_TRANSLATIONS_ADD_DEFAULTS,CLOSURE_COMPILER_EXECUTABLE,CODE_COLOR_SCHEME,COMMENTS_IN_GALLERIES
    COMMENTS_IN_PAGES,COMMENT_SYSTEM,COMMENT_SYSTEM_ID,COMPILERS
    CONTENT_FOOTER,CONTENT_FOOTER_FORMATS,COPY_SOURCES,CREATE_ARCHIVE_NAVIGATION
    CREATE_DAILY_ARCHIVE,CREATE_FULL_ARCHIVES,CREATE_MONTHLY_ARCHIVE,CREATE_SINGLE_ARCHIVE
    DATE_FANCINESS,DATE_FORMAT,DEFAULT_LANG,DEMOTE_HEADERS
    DEPLOY_COMMANDS,DEPLOY_DRAFTS,DEPLOY_FUTURE,DISABLED_PLUGINS
    DISABLE_INDEXES,DISABLE_MAIN_ATOM_FEED,DISABLE_MAIN_RSS_FEED,ENABLE_AUTHOR_PAGES
    EXIF_WHITELIST,EXTRA_HEAD_DATA,EXTRA_IMAGE_EXTENSIONS,EXTRA_PLUGINS_DIRS
    EXTRA_THEMES_DIRS,FAVICONS,FEED_LENGTH,FEED_LINKS_APPEND_QUERY
    FEED_PLAIN,FEED_READ_MORE_LINK,FEED_TEASER,FEED_TEASERS
    FILES_FOLDERS,FILE_METADATA_REGEXP,FILE_METADATA_UNSLUGIFY_TITLES,FILTERS
    FORCE_ISO8601,FRONT_INDEX_HEADER,FUTURE_IS_NOW,GALLERY_FOLDERS
    GALLERY_SORT_BY_DATE,GENERATE_ATOM,GENERATE_RSS,GITHUB_COMMIT_SOURCE
    GITHUB_DEPLOY_BRANCH,GITHUB_REMOTE_NAME,GITHUB_SOURCE_BRANCH,GLOBAL_CONTEXT
    GLOBAL_CONTEXT_FILLER,GZIP_COMMAND,GZIP_EXTENSIONS,GZIP_FILES
    HEADER_PERMALINKS_FILE_BLACKLIST,HEADER_PERMALINKS_XPATH_LIST,HIDDEN_AUTHORS,HIDDEN_CATEGORIES
    HIDDEN_TAGS,HIDE_REST_DOCINFO,HTML,HTML_TIDY_EXECUTABLE
    HYPHENATE,IMAGE_FOLDERS,IMAGE_THUMBNAIL_FORMAT,IMAGE_THUMBNAIL_SIZE
    INDEXES_PAGES,INDEXES_PAGES_MAIN,INDEXES_PRETTY_PAGE_URL,INDEXES_STATIC
    INDEXES_TITLE,INDEX_DISPLAY_POST_COUNT,INDEX_FILE,INDEX_PATH
    INDEX_READ_MORE_LINK,INDEX_TEASERS,IPYNB_CONFIG,JPEGOPTIM_EXECUTABLE
    JS_DATE_FORMAT,KATEX_AUTO_RENDER,LANG,LICENSE
    LINK_CHECK_WHITELIST,LISTINGS_FOLDERS,LOCALES,LOGO_URL
    MARKDOWN_EXTENSIONS,MARKDOWN_EXTENSION_CONFIGS,MATHJAX_CONFIG,MAX_IMAGE_SIZE
    METADATA_FORMAT,METADATA_MAPPING,METADATA_VALUE_MAPPING,META_GENERATOR_TAG
    NAVIGATION_ALT_LINKS,NAVIGATION_LINKS,NEW_POST_DATE_PATH,NEW_POST_DATE_PATH_FORMAT
    ONE_FILE_POSTS,OPTIPNG_EXECUTABLE,OUTPUT_FOLDER,PAGES
    PAGE_INDEX,PANDOC_OPTIONS,POSTS,PRESERVE_EXIF_DATA
    PRESERVE_ICC_PROFILES,PRETTY_URLS,REDIRECTIONS,ROBOTS_EXCLUSIONS
    RSS_COPYRIGHT,RSS_COPYRIGHT_FORMATS,RSS_COPYRIGHT_PLAIN,RSS_EXTENSION
    RSS_FILENAME_BASE,RSS_LINK,RSS_PATH,SCHEDULE_ALL
    SCHEDULE_RULE,SEARCH_FORM,SHOW_BLOG_TITLE,SHOW_INDEX_PAGE_NAVIGATION
    SHOW_SOURCELINK,SHOW_UNTRANSLATED_POSTS,SITE_URL,SLUG_AUTHOR_PATH
    SLUG_TAG_PATH,SOCIAL_BUTTONS_CODE,STRIP_INDEXES,TAGLIST_MINIMUM_POSTS
    TAGS_INDEX_PATH,TAG_DESCRIPTIONS,TAG_PAGES_ARE_INDEXES,TAG_PATH
    TAG_TITLES,TAG_TRANSLATIONS,TAG_TRANSLATIONS_ADD_DEFAULTS,TEMPLATE_FILTERS
    THEME,THEME_COLOR,THEME_CONFIG,THUMBNAIL_SIZE
    TIMEZONE,TRANSLATIONS,TRANSLATIONS_PATTERN,TWITTER_CARD
    URL_TYPE,USE_BUNDLES,USE_CDN,USE_CDN_WARNING
    USE_FILENAME_AS_TITLE,USE_KATEX,USE_REST_DOCINFO_METADATA,USE_SLUGIFY
    USE_TAG_METADATA,WARN_ABOUT_TAG_METADATA,YUI_COMPRESSOR_EXECUTABLE,
    

.. csv-table:: Table of conf.py variables. Columns alphabetical.
   :widths: auto
   
    ADDITIONAL_METADATA,DATE_FORMAT,HTML,ROBOTS_EXCLUSIONS
    ARCHIVES_ARE_INDEXES,DEFAULT_LANG,HTML_TIDY_EXECUTABLE,RSS_COPYRIGHT
    ARCHIVE_FILENAME,DEMOTE_HEADERS,HYPHENATE,RSS_COPYRIGHT_FORMATS
    ARCHIVE_PATH,DEPLOY_COMMANDS,IMAGE_FOLDERS,RSS_COPYRIGHT_PLAIN
    ATOM_EXTENSION,DEPLOY_DRAFTS,IMAGE_THUMBNAIL_FORMAT,RSS_EXTENSION
    ATOM_FILENAME_BASE,DEPLOY_FUTURE,IMAGE_THUMBNAIL_SIZE,RSS_FILENAME_BASE
    ATOM_PATH,DISABLED_PLUGINS,INDEXES_PAGES,RSS_LINK
    AUTHOR_PAGES_ARE_INDEXES,DISABLE_INDEXES,INDEXES_PAGES_MAIN,RSS_PATH
    AUTHOR_PAGES_DESCRIPTIONS,DISABLE_MAIN_ATOM_FEED,INDEXES_PRETTY_PAGE_URL,SCHEDULE_ALL
    AUTHOR_PATH,DISABLE_MAIN_RSS_FEED,INDEXES_STATIC,SCHEDULE_RULE
    BASE_URL,ENABLE_AUTHOR_PAGES,INDEXES_TITLE,SEARCH_FORM
    BLOG_AUTHOR,EXIF_WHITELIST,INDEX_DISPLAY_POST_COUNT,SHOW_BLOG_TITLE
    BLOG_DESCRIPTION,EXTRA_HEAD_DATA,INDEX_FILE,SHOW_INDEX_PAGE_NAVIGATION
    BLOG_EMAIL,EXTRA_IMAGE_EXTENSIONS,INDEX_PATH,SHOW_SOURCELINK
    BLOG_TITLE,EXTRA_PLUGINS_DIRS,INDEX_READ_MORE_LINK,SHOW_UNTRANSLATED_POSTS
    BODY_END,EXTRA_THEMES_DIRS,INDEX_TEASERS,SITE_URL
    CACHE_FOLDER,FAVICONS,IPYNB_CONFIG,SLUG_AUTHOR_PATH
    CATEGORIES_INDEX_PATH,FEED_LENGTH,JPEGOPTIM_EXECUTABLE,SLUG_TAG_PATH
    CATEGORY_ALLOW_HIERARCHIES,FEED_LINKS_APPEND_QUERY,JS_DATE_FORMAT,SOCIAL_BUTTONS_CODE
    CATEGORY_DESCRIPTIONS,FEED_PLAIN,KATEX_AUTO_RENDER,STRIP_INDEXES
    CATEGORY_DESTPATH_AS_DEFAULT,FEED_READ_MORE_LINK,LANG,TAGLIST_MINIMUM_POSTS
    CATEGORY_DESTPATH_FIRST_DIRECTORY_ONLY,FEED_TEASER,LICENSE,TAGS_INDEX_PATH
    CATEGORY_DESTPATH_NAMES,FEED_TEASERS,LINK_CHECK_WHITELIST,TAG_DESCRIPTIONS
    CATEGORY_DESTPATH_TRIM_PREFIX,FILES_FOLDERS,LISTINGS_FOLDERS,TAG_PAGES_ARE_INDEXES
    CATEGORY_OUTPUT_FLAT_HIERARCHY,FILE_METADATA_REGEXP,LOCALES,TAG_PATH
    CATEGORY_PAGES_ARE_INDEXES,FILE_METADATA_UNSLUGIFY_TITLES,LOGO_URL,TAG_TITLES
    CATEGORY_PAGES_FOLLOW_DESTPATH,FILTERS,MARKDOWN_EXTENSIONS,TAG_TRANSLATIONS
    CATEGORY_PATH,FORCE_ISO8601,MARKDOWN_EXTENSION_CONFIGS,TAG_TRANSLATIONS_ADD_DEFAULTS
    CATEGORY_PREFIX,FRONT_INDEX_HEADER,MATHJAX_CONFIG,TEMPLATE_FILTERS
    CATEGORY_PREFIX.,FUTURE_IS_NOW,MAX_IMAGE_SIZE,THEME
    CATEGORY_TITLES,GALLERY_FOLDERS,METADATA_FORMAT,THEME_COLOR
    CATEGORY_TRANSLATIONS,GALLERY_SORT_BY_DATE,METADATA_MAPPING,THEME_CONFIG
    CATEGORY_TRANSLATIONS_ADD_DEFAULTS,GENERATE_ATOM,METADATA_VALUE_MAPPING,THUMBNAIL_SIZE
    CLOSURE_COMPILER_EXECUTABLE,GENERATE_RSS,META_GENERATOR_TAG,TIMEZONE
    CODE_COLOR_SCHEME,GITHUB_COMMIT_SOURCE,NAVIGATION_ALT_LINKS,TRANSLATIONS
    COMMENTS_IN_GALLERIES,GITHUB_DEPLOY_BRANCH,NAVIGATION_LINKS,TRANSLATIONS_PATTERN
    COMMENTS_IN_PAGES,GITHUB_REMOTE_NAME,NEW_POST_DATE_PATH,TWITTER_CARD
    COMMENT_SYSTEM,GITHUB_SOURCE_BRANCH,NEW_POST_DATE_PATH_FORMAT,URL_TYPE
    COMMENT_SYSTEM_ID,GLOBAL_CONTEXT,ONE_FILE_POSTS,USE_BUNDLES
    COMPILERS,GLOBAL_CONTEXT_FILLER,OPTIPNG_EXECUTABLE,USE_CDN
    CONTENT_FOOTER,GZIP_COMMAND,OUTPUT_FOLDER,USE_CDN_WARNING
    CONTENT_FOOTER_FORMATS,GZIP_EXTENSIONS,PAGES,USE_FILENAME_AS_TITLE
    COPY_SOURCES,GZIP_FILES,PAGE_INDEX,USE_KATEX
    CREATE_ARCHIVE_NAVIGATION,HEADER_PERMALINKS_FILE_BLACKLIST,PANDOC_OPTIONS,USE_REST_DOCINFO_METADATA
    CREATE_DAILY_ARCHIVE,HEADER_PERMALINKS_XPATH_LIST,POSTS,USE_SLUGIFY
    CREATE_FULL_ARCHIVES,HIDDEN_AUTHORS,PRESERVE_EXIF_DATA,USE_TAG_METADATA
    CREATE_MONTHLY_ARCHIVE,HIDDEN_CATEGORIES,PRESERVE_ICC_PROFILES,WARN_ABOUT_TAG_METADATA
    CREATE_SINGLE_ARCHIVE,HIDDEN_TAGS,PRETTY_URLS,YUI_COMPRESSOR_EXECUTABLE
    DATE_FANCINESS,HIDE_REST_DOCINFO,REDIRECTIONS,


Create a --quiet web-site
-------------------------

Create a web-site with the ``--quiet`` option. This may be more suitable than the ``--demo`` website as a template for modification and building your own website.

.. code:: bash

    (venv1) ian@X200:~$ nikola init --quiet hampug_quiet
    [2019-05-05T10:14:39Z] INFO: init: Created empty site at hampug_quiet.
    
    (venv1) ian@X200:~$ ls hampug_quiet -l
    total 72
    -rw-rw-r-- 1 ian ian 53216 May  5 22:14 conf.py
    drwxrwxr-x 2 ian ian  4096 May  5 22:14 files
    drwxrwxr-x 2 ian ian  4096 May  5 22:14 galleries
    drwxrwxr-x 2 ian ian  4096 May  5 22:14 listings
    drwxrwxr-x 2 ian ian  4096 May  5 22:14 pages
    drwxrwxr-x 2 ian ian  4096 May  5 22:14 posts
    
    cd hampug_quiet
    
    (venv1) ian@X200:~/hampug_quiet$ nikola auto
    [2019-05-05T10:17:42Z] INFO: auto: Rebuilding the site...
    Scanning posts........done!
    .  render_listings:output/listings/index.html
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
    .  render_posts:timeline_changes
    .  render_galleries:output/galleries
    .  render_galleries:output/galleries/index.html
    .  render_galleries:output/galleries/rss.xml
    .  render_taxonomies:output/archive.html
    .  render_taxonomies:output/index.html
    .  render_taxonomies:output/categories/index.html
    .  render_taxonomies:output/rss.xml
    .  create_bundles:output/assets/css/all-nocdn.css
    .  create_bundles:output/assets/css/all.css
    .  create_bundles:output/assets/js/all-nocdn.js
    .  create_bundles:output/assets/js/all.js
    .  sitemap:output/sitemap.xml
    .  sitemap:output/sitemapindex.xml
    .  robots_file:output/robots.txt
    [2019-05-05T10:17:46Z] INFO: auto: Serving on http://127.0.0.1:8000/ ...


Proceed to make your own website by using this ``--quiet`` generated website as your template. Edit the conf.py, created an images folder and adding your images, and creating your own web-pages in the pages folder.

Review and follow the directions on the Nikola website on `Creating a web-site - not a blog`_

.. _`Creating a web-site - not a blog`: https://getnikola.com/creating-a-site-not-a-blog-with-nikola.html

Nikola web-pages may be created from html, markdown and reStructuredText. Other options may be available, so to check use the command ``$ nikola new_page --available-formats``.

The Nikola preference is to create the pages using reStructuredText. There are tabs on this website to provide an introduction to reST and how to creating web-pages using reST.

The following screen-shots are of the home page of websites created using ``$ nikola init --demo hampug_demo`` and ``$ nikola init --quiet hampug_quiet``

.. figure:: /images/nikola_demo_website.png
    :alt: nikola_demo_1
    :align: center

    Nikola --demo website home page


.. figure:: /images/nikola_quiet_website.png
    :alt: nikola_demo_2
    :align: center

    Nikola --quiet website home page
 
    
`[Top] <#top>`_   

