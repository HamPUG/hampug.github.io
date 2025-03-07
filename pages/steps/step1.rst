.. _top:

1. Open an Account at PythonAnywhere
====================================

Introduction
------------

If you don't have an account at pythonanywhere.com then connect to https://www.pythonanywhere.com/pricing/ and at this stage you might prefer to select *Create a Beginner Account* which is free.

In creating a Beginner account you are prompted to supply a *Username*. Note that when you create a web-site your Username will be part of your internet URL. Therefore you may wish to pick a Username that relates to the intended content of your web-site. For example if you plan to create a web-site about *flowers* then provide the Username of *flowers* and your future website URL will be ``http://flowers.pythonanywhere.com``

In the documentation below <username> will be used to refer to the Username that you selected when you created the account. In code examples taken from this site the Username will be `hampug1`.

Upon logging into your account you will notice that the main options to select from are: **Dashboard, Consoles, Files, Web, Tasks, Databases**.

You may initially wish to have a look around. Right-click on **Console** select *Open a new tab* and launch a console. Also right-click on **Files** and select *Open a new tab* to have a GUI that displays all your files. Using the Console you can make used of *ls* and *cd* commands to take a look around at what files and folders are supplied with your account. Alternatively use the Files GUI browser page to look around.

From your console, using ls and cd bash commands you should find you have a top directory ``https://www.pythonanywhere.com/user/<username>/files/`` which includes the folders:

- ``/home/``
- ``/tmp/``
- ``/var/``

Off ``/var/`` folder you will see a ``/www/`` folder. At this stage it will probably be an empty directory. This will later be used for you web-site.

Off your ``/home/`` folder you should have a folder <username>. i.e. Whatever you provided as the Username when you created the account.

If you were to use the PythonAnywhere wizard to create a django, web2py, flask or bottle web-site, then a wsgi.py file will be placed into /var/www/. The file will have a name like, ``<username>_pythonanywhere_com_wsgi.py``. This file effectively points to where you will create your python framework web-site. For example, off: ``/home/<username>/<my_website>/``


Create a manual WSGI based web-site
-----------------------------------

To aid with your understanding, it may be worthwhile to first create a web-site using the pythonanywhere web-site wizard, before creating a static web-site.

From the list of options, Dashboard, Consoles, Files, Web, Tasks, Databases, Right-click on **Web** and *Open a new tab*. In the new browser window there is now the option to *Add a new web app*. Click on this to start the wizard. When provided with the choices of frameworks (django, web2py, flask, bottle and manual) click on **manually** create a web-site. 

In another tab on your browser enter the URL ``http://<username>.pythonanywhere.com``, where <username> is the name you supplied when creating your account. Your web-site should now be displaying:

.. image:: /images/pythonanywhere_hello_world.png


If you go back to your pythonanywhere **Files** or **Console** browser tabs, you should see that a file has been created in ``/var/www/`` which is ``<username>_pythonanywhere_com_wsgi.py``. Double click on this file to open the *web server gateway interface* file and review its contents. The lines of python code in this file that are executed are:

.. code:: python

    HELLO_WORLD = """<html>
    <head>
        <title>PythonAnywhere hosted web application</title>
    </head>
    <body>
    <h1>Hello, World!</h1>
    <p>
        This is the default welcome page for a
        <a href="https://www.pythonanywhere.com/">PythonAnywhere</a>
        hosted web application.
    </p>
    <p>
        Find out more about how to configure your own web application
        by visiting the <a href="https://www.pythonanywhere.com/web_app_setup/">web app setup</a> page
    </p>
    </body>
    </html>"""

    def application(environ, start_response):
        if environ.get('PATH_INFO') == '/':
            status = '200 OK'
            content = HELLO_WORLD
        else:
            status = '404 NOT FOUND'
            content = 'Page not found.'
        response_headers = [('Content-Type', 'text/html'), ('Content-Length', str(len(content)))]
        start_response(status, response_headers)
        yield content.encode('utf8')
    
This provides the html that is served up as the home page of your web-site. The following is also provided, but is commented out awaiting your action:

.. code:: python

    # +++++++++++ CUSTOM WSGI +++++++++++
    # If you have a WSGI file that you want to serve using PythonAnywhere, perhaps
    # in your home directory under version control, then use something like this:
    #
    #import sys
    #
    #path = '/home/hampug1/path/to/my/app
    #if path not in sys.path:
    #    sys.path.append(path)
    #
    #from my_wsgi_file import application  # noqa

Thus if I were to create a folder called `website` off my `home/hampug1/` folder and into it I place a WSGI.py file called *launch.py* which includes the function *application*, then I would uncomment and edit the above as follows:

.. code:: python

    path = '/home/hampug1/website/'
    if path not in sys.path:
        sys.path.append(path)
    #
    from launch import application  # noqa

Note regarding *# noqa*: A lint or linter is a program that supports verifying code quality. The # noqa at the end of the line stands for *No Quality Assurance* and is to warn the linter not to raise any warning. For python see `PEP8`_.

.. _PEP8: https://www.python.org/dev/peps/pep-0008/

Additional Information: By adding into my launch.py file as I build the *content* of the home page:

.. code:: python

    content += "</p><p>Length of environ dictionary:{}</p>".format(len(environ))
    for key, value in environ.items():
        content += "<p>" + key + ":" + str(value) + "</p>"

My home page displays the following breakdown of *environ*::

    /var/www/static/ 
    Length of environ dictionary:34
    QUERY_STRING:
    REQUEST_METHOD:GET
    CONTENT_TYPE:
    CONTENT_LENGTH:
    REQUEST_URI:/
    PATH_INFO:/
    DOCUMENT_ROOT:/usr/local/openresty/nginx/html
    SERVER_PROTOCOL:HTTP/1.1
    REMOTE_ADDR:10.0.0.162
    REMOTE_PORT:50514
    SERVER_PORT:80
    SERVER_NAME:hampug1.pythonanywhere.com
    SCRIPT_NAME:
    HTTP_HOST:hampug1.pythonanywhere.com
    HTTP_X_REAL_IP:121.99.140.160
    HTTP_X_FORWARDED_FOR:121.99.140.160
    HTTP_CONNECTION:close
    HTTP_USER_AGENT:Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:66.0) Gecko/20100101 Firefox/66.0
    HTTP_ACCEPT:text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
    HTTP_ACCEPT_LANGUAGE:en,en-US;q=0.5
    HTTP_ACCEPT_ENCODING:gzip, deflate
    HTTP_COOKIE:_ga=GA1.2.978166663.1556102146; _gid=GA1.2.573815141.1556255488; session_id_hampug=121.99.140.160-92da0afe-da9d-4e2d-9ecf-b56c6e06ade0
    HTTP_UPGRADE_INSECURE_REQUESTS:1
    HTTP_CACHE_CONTROL:max-age=0
    wsgi.input:
    wsgi.file_wrapper:
    wsgi.version:(1, 0)
    wsgi.errors:
    wsgi.run_once:False
    wsgi.multithread:False
    wsgi.multiprocess:False
    wsgi.url_scheme:http
    uwsgi.version:b'2.0.17.1'
    uwsgi.node:b'glenn-liveweb8'

In summary, this how a python framework creates a web-site on PythonAnywhere. However our aim is a bit different in that we use a python based static web-site generator, Nikola, to build a static site that is hosted on PythonAnywhere.


Create a Static web-site as a Demonstration
-------------------------------------------

As mentioned previously PythonAnywhere use Nginx. By default Nginx looks for a static web-site before looking for a python file for a WSGI web-site. Nginx expects a static web-site to have a home page of *index.html*. Thus the path and file for where Nginx expects to find the static web-site home page is: ``/var/www/static/index.html``

You need to use a console or files tab on you browser to create a static folder. For example:

.. code:: bash

    / $ cd /
    / $ cd var
    /var $ cd www
    /var/www $ mkdir static
    /var/www $ cd static
    /var/www/static $ touch index.html
    /var/www/static $ ls -l
   
    -rw-rw-r-- 1 hampug1 registered_users     0 Apr 26 23:49 index.html

If you use the `Files` browser tab and locate the new index.html file, you can paste into it a test home page like this:

.. code:: html

    <!DOCTYPE html>
    <html>
      <head>
        <title>PythonAnywhere static web-site</title>
      </head>
      <body>
        <h1>Hello, World!</h1>
        <p>
          This is the default index.html page.
        </p>
      </body>
    </html>"""

You now need to click on the PythonAnywhere **Web** option and then click on `Reload hampug1.pythonanywhere.com`. After this open a browser tab and enter http://hampug1.pythonanywhere.com/ and it will display your static web-site home page.

Summary: Now that you know that you are able to create a static web-site on PythonAnywhere its time to create web-pages using reStructuredText and use Nikola to make the static web-site.


`[Top] <#top>`_
