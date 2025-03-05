.. _top:

reStructuredText Directives
===========================

Directives are a general-purpose extension mechanism, a way of adding support 
for new constructs without adding new syntax. For a description of all 
standard directives, see `reStructuredText Directives`__. 

__ http://docutils.sourceforge.net/docs/ref/rst/directives.html


Inline Directives
-----------------

This sentence contains :strong:`strong text` with inline use of strong instead of using **two** asterisks.
    
This sentence contains :emphasis:`emphasis text` with inline use of emphasis instead of using *single* asterisks.

This sentence contains :literal:`literal text` with inline use of literal instead of using ``two`` graves.
::

    This sentence contains :strong:`strong text` with inline use of strong instead of using **two** asterisks.
        
    This sentence contains :emphasis:`emphasis text` with inline use of emphasis instead of using *single* asterisks.

    This sentence contains :literal:`literal text` with inline use of literal instead of using ``two`` graves.


Directives
----------

Default-role
------------

This sentence uses single graves and the `default role` in the sentence results in emphasis. The default role will be set to subscript. 

.. default-role:: subscript

The `default role` has been set to subscript. Now reset the default role

.. default-role::

The `default role` of single graves is now back to emphasis.

::

    .. default-role:: subscript
    
    The `default role` has been set to subscript. Now reset the default role
    
    .. default-role::
    
    The `default role` of single graves is now back to emphasis.


Replace
-------

Replace text and in this case apply inline sub-scripting to the replacement text.

The chemical formula for pure water is |H2O|.

.. |H2O| replace:: H\ :sub:`2`\ O

::

    The chemical formula for pure water is |H2O|.

    .. |H2O| replace:: H\ :sub:`2`\ O

Math
----

In order to display mathematical equations on a page the Nikola meta-data must
have enabled maths with: ``.. has_math: True``

Mathematical Equations may be display as inline or by using the directive

Inline mathematics are produced using the reST math role or the LaTeX backslash-parentheses delimiters:

Euler’s formula is :math:`e^{ix} = \cos x + i\sin x`

The area of a circle is :math:`A_\text{c} = (\pi/4) d^2`.

Directive use examples:

.. math::

    α_t(i) = P(O_1, O_2, … O_t, q_t = S_i λ)

.. math::

   \int \frac{dx}{1+ax}=\frac{1}{a}\ln(1+ax)+C

The above is as follows:
::

    Inline mathematics are produced using the reST math role or the LaTeX backslash-parentheses delimiters:

    Euler’s formula is :math:`e^{ix} = \cos x + i\sin x`

    The area of a circle is :math:`A_\text{c} = (\pi/4) d^2`.

    Directive use examples:

    .. math::
        α_t(i) = P(O_1, O_2, … O_t, q_t = S_i λ)

    .. math::

       \int \frac{dx}{1+ax}=\frac{1}{a}\ln(1+ax)+C


Code
----

.. code:: python

   print("A literal block directive explicitly marked as python code")

The code directive has been included in docutils since version 0.9 and now 
replaces Nikola's code-block directive. To ease the transition, two aliases 
for code directive are provided: code-block and sourcecode:

.. code-block:: python
    :number-lines:

    for i in range(10):
        print(i, i**2)

.. sourcecode:: html
    :number-lines:

    <p>A <strong>paragraph</strong> of html</p>

The above is as follows:
::

    .. code:: python

        print("A literal block directive explicitly marked as python code")
    
    .. code-block:: python
        :number-lines:

        for i in range(10):
            print(i, i**2)

    .. sourcecode:: html
        :number-lines:
    
        <p>A <strong>paragraph</strong> of html</p>


Images and Figures
------------------

.. image:: /images/clinton_obama.jpg
       :width: 400 px
       :alt: For blind people this, just letting you know this is a photo of Clinton and Obama
       :align: right
     
..  
    :scale: 100 % - With Nikola v8.3.1 this erropr occurs...
    This code is giving: System Message: WARNING/2 (<string>, line 157) Cannot scale image! 
    Could not get size from "/images/clinton_obama.jpg": 
    [Errno 2] No such file or directory: '/images/clinton_obama.jpg'



An image is normally a photograph that has been saved as a file of a type like, jpg, png, etc. The text will wrap around the image. In this case the image is aligned to the right, so the text will be displayed down the left hand side of the image. 

This image has had its width set to 400 pixels and with a scale of 100% then it will display at a width of 400 pixels. If the width had been set to 800 pixels and a scale of 50% then the same sized image would be displayed. 

No height has been specified so the image keeps its original aspect ratio. 

The directive is ``.. image:: /images/clinton_obama.jpg``. Under Nikola an *images* folder has been dedicated to store all images::

    .. image:: /images/clinton_obama.jpg
           :width: 400 px
           :alt: Blind people. This is a photo of Clinton and Obama.
           :align: right

With Nikola V8.3.1 the reST comand (above) delivers a warning during the build phase if *scale* is used and embeds a warning message in the html. 

An image can also be displayed by embedding html in the reST document::

    .. raw:: html

        <img alt="For blind people this, just letting you know this is a photo of Clinton and Obama using html" 
            class="align-right" 
            src="../images/clinton_obama.jpg" 
            style="width: 400.0px;">    
               
..
    The following would display the same size image
    /scale/ not working with nikola v8.3.1...    
    
    .. image:: /images/clinton_obama.jpg
           :width: 800 px
           :scale: 50 %
           :alt: Blind people. This is a photo of Clinton and Obama
           :align: right


reStructuredText Extensions
===========================

Thumbnail
---------

Thumbnail allows an image to be clicked on and it will expand to a full page display. To include an image placed in the images folder (or other folders defined by IMAGE_FOLDERS), use the thumbnail directive, like this::

    .. thumbnail:: /images/clinton_obama.jpg
        :alt: Hill and Bazza
        :align: center
        :width: 100 px

Which produces an image like this, that can be clicked on to fill the browser window:

..
    .. thumbnail:: /images/clinton_obama.jpg
        :scale: 50 %
        :alt: Hill and Bazza
        
    With Nikola v8.3.1 there seems to be an issue using the reST image feature. It can be done with::

    .. raw:: html

        <a class="reference external image-reference" href="../images/clinton_obama.jpg">
        <img alt="Hill and Bazza" src="../images/clinton_obama.thumbnail.jpg">
   
    .. raw:: html

    <a class="reference external image-reference"; 
        href="../images/clinton_obama.jpg";>
    <img alt="Hill and Barry"; 
        src="../images/clinton_obama.thumbnail.jpg";
        class="align-left";
        title= "Hill and Bazzer.">


.. thumbnail:: /images/clinton_obama.jpg
        :alt: Hill and Barry
        :align: center
        :width: 100 px

.. 
    .. class:: center  - didn't work

.. raw:: html

    <center>Clinton and Obama at CNN.</center>
       
.. 
    html of a thumbnail with link...
       
    .. raw:: html
    
        <center> A thumbnail link </center>
        
        <figure class="align-center">
            <a class="reference external image-reference" href="../images/clinton_obama.jpg">
                <img alt="Hill and Barry" 
                    src="../images/clinton_obama.thumbnail.jpg"
                    style="width: 100.0px">
            </a>
            <figcaption>
                <p>Clinton and Obama at CNN.</p>
            </figcaption>
        </figure>   


A small thumbnail will be placed in the page, and it will be linked to the bigger version of the image when clicked, using baguetteBox by default. 

All options supported by the reST image directive are supported (except target). Providing alt is recommended, as this is the image caption which a blind person using text to speech would hear. If a body element is provided, the thumbnail will mimic the behavior of the figure directive instead.

The html generated for the above thumbnail is::

    <a class="reference external image-reference" href="../images/clinton_obama.jpg">
    <img alt="Hill and Barry" class="align-center" src="../images/clinton_obama.thumbnail.jpg" style="width: 100px;"></a>

    <center>Clinton and Obama at CNN.</center>


Figure Directive
----------------

A figure directive is similar to image, but allows a caption to insert underneath it.

.. figure:: /images/clinton_obama.jpg
    :alt: Hill and Bazza
    :align: center
    :width: 200 px
    
    Hillary Clinton and Barack Obama during an election debate at a CNN studio.


`[Top] <#top>`_


.. 
    According to: https://docutils.sourceforge.io/docs/ref/rst/directives.html#image
    the following options are recognized: alt, height, width, scale, align, target, class, and name.
    However with nikola v8.3.1 :scale: has an error.
    
    For more information see: https://docutils.sourceforge.io/rst.html
    
    List of files: https://docutils.sourceforge.io/docs/ref/rst/
    
  
       
