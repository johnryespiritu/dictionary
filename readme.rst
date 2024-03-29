==========
dictionary
==========

.. image :: https://github.com/soupless/dictionary/actions/workflows/tests.yml/badge.svg?style=flat
    :target: https://github.com/soupless/dictionary/actions/workflows/tests.yml

.. image :: https://img.shields.io/badge/license-MIT-blue.svg?style=flat
    :alt: MIT License
    :target: http://choosealicense.com/licenses/mit/

| 
| A package that allows you to create and use a dictionary saved as a JSON file.

What does the dictionary file look like?
----------------------------------------

A deserialized, typehinted contents of the JSON file is:

.. code-block :: python3

    {
        "title": str,
        "author": str,
        "description": str,
        "revision_date": str,
        "contents": {
            "<keyword>": {
                "definitions": list[str],
                "references": list[str]
            },
            ...
        }
    }

The ``<keyword>`` could be any string, and here, those are called keywords.

After processing the file, the ``Dictionary`` class only takes the ``contents`` and all other keys are properties.


Usage
-----

This package is compatible from Python 3.8 to Python 3.10.

To install, run

.. code-block :: console

    pip install https://github.com/soupless/dictionary.git

As of now, it is useful only if it was used through an interactive shell. To use the dictionary, import ``Dictionary`` from ``dictionary.main``.

Note that deleting a key and its value through the ``pop`` method or using the ``del`` keyword won't work to avoid data deletion. If one needs to delete the key, use the ``remove`` method. However, it is possible to delete the keys of a key of the dictionary, like ``del Dictionary(path)[keyword]['references']`` as the type of the value of the dictionary keys is ``dict`` and the deletion methods are not overridden. Please keep this in mind.

Methods
-------

+--------------------+------------------------------------+
|     Method Name    |             Description            |
+====================+====================================+
|      ``save``      | Saves the current copy of the      |
|                    | dictionary to the associated file. |
+--------------------+------------------------------------+
| ``information_on`` | Returns information of a           |
|                    | keyword from the dictionary, if it |
|                    | exists.                            |
+--------------------+------------------------------------+
|     ``search``     | Searches the contents of the       |
|                    | current copy of the dictionary for |
|                    | a keyword presented, considering   |
|                    | case sensitivity.                  |
+--------------------+------------------------------------+
|       ``add``      | Adds content to the dictionary. If |
|                    | the keyword is found, a definition |
|                    | or a reference can be added.       |
+--------------------+------------------------------------+
|     ``remove``     | Removes content from the current   |
|                    | copy of the dictionary.            |
+--------------------+------------------------------------+
|    ``edit_meta``   | Edits the metadata of the          |
|                    | dictionary.                        |
+--------------------+------------------------------------+

Enums
-----

+--------------------+------------------------------------+
|      Enum Name     |             Description            |
+====================+====================================+
|   ``SearchMode``   | Used in the ``search`` method      |
|                    | to specify the search mode.        |
|                    | Possible values are ``Exact``,     |
|                    | ``SubStr``, and ``Approx``.        |
+--------------------+------------------------------------+
|    ``InfoType``    | Used in the ``information_on``     |
|                    | method to specify the type of      |
|                    | information. Possible values are   |
|                    | ``Definitions`` and ``References``.|
+--------------------+------------------------------------+
|     ``MDType``    | Used in the ``edit_meta`` method   |
|                    | to specify which metadata field to |
|                    | edit. Possible values are          |
|                    | ``Title``, ``Author``, and         |
|                    | ``Description``.                   |
+--------------------+------------------------------------+


Properties
----------

+--------------------+-------------------------------------+
|      Property      |             Description             |
+====================+=====================================+
|      ``path``      | The path of the file associated.    |
+--------------------+-------------------------------------+
|      ``title``     | The title of the dictionary.        |
+--------------------+-------------------------------------+
|     ``author``     | The author of the dictionary.       |
+--------------------+-------------------------------------+
|   ``description``  | The description of the dictionary.  |
+--------------------+-------------------------------------+
|  ``revision_date`` | The date of the last revision of    |
|                    | the dictionary.                     |
+--------------------+-------------------------------------+
|     ``edited``     | An indicator whether the dictionary |
|                    | is edited after it was initialized. |
+--------------------+-------------------------------------+

License
-------

.. code-block ::

    MIT License
    
    Copyright (c) 2022 soupless
    
    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:
    
    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.
