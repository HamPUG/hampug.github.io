.. _top:

6. Deploying to PythonAnywhere
==============================

Manual Method
-------------

When the website is placed on PythonAnywhere it will be off the directory structure ``/var/www/static/``

Normally Nikola will produce the website off a folder named *output*. In conf.py this is set with::

    OUTPUT_FOLDER = 'output'

As PythonAnywhere defaults to having the website off *static* then Nikola can be set to generate the website on your PC off the folder *static* as follows::

    OUTPUT_FOLDER = 'static'

By setting a terminal session to the Nikola top level folder, which the static folder is off, then *tar* may be used to create an archive of the website as follows::

    $ tar -czvf website.tar.gz static

Where the switches mean::

    -c: Create an archive.
    -z: Compress the archive with gzip.
    -v: Display progress in the terminal while creating the archive, also known as “verbose” mode. 
    -f: Allows you to specify the filename of the archive.

    -x: Extract files from an archive


The created archive is::

    username@host:~/hampug$ ls -sh website*
    1.4M website.tar.gz

In the following screenshots, the files are extracted from the archive and *static* folder becomes the top level directory::

    /var/www $ tar -xvzf website.tar.gz

Login to the pythonanywhere.com account. The following screen shots show the actions taken to upload and install the website. Click on any image to enlarge it.

.. thumbnail:: /images/website/ws1.png
    :alt: ws1
    :align: left

    Login to pythonanywhere.com account
    
.. thumbnail:: /images/website/ws2.png
    :alt: ws2
    :align: left

    Click on Files
    
.. thumbnail:: /images/website/ws3.png
    :alt: ws3
    :align: left

    Click on directories to reach top level with home tmp and var
    
.. thumbnail:: /images/website/ws4.png
    :alt: ws4
    :align: left

    Click on upload and select website tar file for uploading

.. thumbnail:: /images/website/ws5.png
    :alt: ws5
    :align: left

    website.tar.gz has uploaded to /var/www/. Click on *Consoles*
    
.. thumbnail:: /images/website/ws6.png
    :alt: ws6
    :align: left

    Open a bash console
    
.. thumbnail:: /images/website/ws7.png
    :alt: ws7
    :align: left

    Use tar to extract the archive.

.. thumbnail:: /images/website/ws8.png
    :alt: ws8
    :align: left

    Extraction creates the *static* folder

.. thumbnail:: /images/website/ws9.png
    :alt: ws9
    :align: left

    Under /var/www/ there is now the *static* folder with the website files.

.. thumbnail:: /images/website/ws10.png
    :alt: ws10
    :align: left

    Using Files a display of /var/www/static/ folders and files

.. thumbnail:: /images/website/ws11.png
    :alt: ws11
    :align: left

    Click on Web

.. thumbnail:: /images/website/ws12.png
    :alt: ws12
    :align: left

    Reload the hampug1.pythonanywhere.com web service

.. thumbnail:: /images/website/ws13.png
    :alt: ws13
    :align: left

    The Website home page is now on-line.
    
`[Top] <#top>`_    

