.. _tutorial_basics:

Tutorial: Basics
================

HTTP REST
---------

SubtleJSON uses the GET/POST/PUT/DELETE HTTP calls in a standard fashion as characterized by the `RESTful`_ standard.

.. _RESTful: http://en.wikipedia.org/wiki/REST

*GET* calls are used to fetch information.  They will not change anything in the database.  For instance, getting a location's details uses a GET call.

*POST* calls are used to complete an action or create an object.  Adding a new user or creating a ticket uses a POST call.

*PUT* calls are used to append objects to existing objects.  For instance, adding items to an order or payments to a ticket.

*DELETE* calls are used for deleting objects.

.. note:: All SubtleJSON calls are made over HTTPS and inherently secure.  Make sure you do not ever call the API without using HTTPS as this may expose your API key.

HTTP Headers
------------

.. warning:: When doing POST/PUT calls, it is very important to set the **Content-Type** header to **application/json**.  This is an easy mistake to make but is absolutely necessary for proper function of the API.

JSON
--------

SubtleJSON, not surprisingly, uses the JSON data format.  JSON stands for Javascript Standard Object Notation.  Most programming languages have easy to use JSON parsing and unparsing libraries.  If you are not familiar with the format, you can learn about it on `Wikipedia`_;

.. _Wikipedia: http://en.wikipedia.org/wiki/JSON

URL Parameters vs. Body Parameters
----------------------------------
All of our REST methods use only what are called URL parameters.  These are variables that come after the ``?`` in a URL.  Each one is separated by an ``&``.  For instance, as you will read below, your API key is passed into our API via a URL parameter.

POST and PUT calls also require what are called "body parameters".  In our case, the body of the request is always JSON and includes other information necessary for more complex calls such as opening tickets and making payments.

API Key
-------
Once you have signed up for your SubtleData account, you can create an application and link it to locations.  You can have many applications.  Each one will have their own API keys to access locations belonging to them.  You can also cross-link locations so that they are available to several or all of your applications.  When using SubtleJSON, you will want to append your *web* API key as a URL parameter to each call like this: ::

    https://api.subtledata.com/v1/locations/959?api_key=@@@@

.. danger:: Be careful with your API key!  If anyone were to obtain it, they would have full access to all of your locations.  Make sure it is kept safe.

Interactive Documentation
-------------------------

Once you have familiarized yourself with REST and JSON and obtained your SubtleData web key, you can head directly to our `Interactive Documentation`_.  There, you can enter your API key and immediately start using all of SubtleJSON's endpoints.  Many GET calls have simple to use forms that will allow you to quickly experiment with our API and see immediate results.  POST/PUT calls require an HTTP JSON body which you can also create on the site.

.. tip:: If you tap on "Model Schema" next to the final object presented in the form for a POST/PUT call, you can see what the format should be and copy it into the form for easy editing.

.. _Interactive Documentation: http://developers.subtledata.com/api/

Local IDs vs. SubtleData IDs
----------------------------

Almost all objects in the SubtleData world have two IDs.  An ID unique to the SubtleData environment and a local ID that is only unique on the point of sale at that location (ie. it is only unique when combined with the location's ID).  A good example are tables at a location.  They have a table number (say table 50) that identifies them at that location (servers/hosts will know it) but also a unique ID to SubtleData (table 33820).  Both IDs are important and will be used in different ways throughout our API ecosystem.

The easy way to tell them apart is that all local IDs are prepended with a `pos_`.  These IDs are always local on the POS.  All other IDs are SubtleData ID numbers.

Next Steps
^^^^^^^^^^

Next, check out: :ref:`tutorial_users`.