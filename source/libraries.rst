.. _libraries:

Native Libraries
================

SubtleLIBS are native client libraries for SubtleJSON.  They are all open source under the MIT license and available on `GitHub`_.

.. _GitHub: https://github.com/subtledata

Availability
------------

SubtleLIBS are currently available in:

* Python
* Objectve-C
* Java
* Javascript

And coming soon:

* Ruby
* PHP

Basic vs. Express Versions
--------------------------

SubtleLIBS come in two varietes:  Basic and Express.  Basic libraries are dynamically generated from our API's specications.  They access our JSON API directly.  It's easy to think of our basic libraries as a simple driver on a database.  They map 1:1 with the JSON calls and require you to enter all variables each time, such as your API key.

Our express libraries are more advanced.  They are custom designed for speed and simplicity.  They are more like an ORM around the database driver mentioned above.  While a basic SubtleLIB call will make one JSON request, express SubtleLIBs might make dozens or hundreds, making your code that much faster and easier.

.. tip:: The basic and express libraries for each language are hosted in the same repository on GitHub.  Check their individual documentation for more information.

Roadmap
-------

Currently, basic libraries are available for all of the languages listed above.  An express library is available for Python.  You can install it with: ::

    pip install subtledata

Enjoy!