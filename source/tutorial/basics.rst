.. _tutorial_basics:

Tutorial: Basics
================

HTTP Calls
----------

SubtleJSON uses the GET/POST/PUT/DELETE HTTP calls in a standard fashion.

.. warning:: When doing POST/PUT calls, it is very important to set the **Content-Type** header to **application/json**.  This is an easy mistake to make but is absolutely necessary for proper function of the API.

Local IDs vs. SubtleData IDs
----------------------------

Almost all objects in the SubtleData world have two IDs.  An ID unique to the SubtleData environment and a local ID that is only unique on the point of sale at that location (ie. it is only unique when combined with the location's ID).  A good example are tables at a location.  They have a table number (say table 50) that identifies them at that location (servers/hosts will know it) but also a unique ID to SubtleData (table 33820).  Both IDs are important and will be used in different ways throughout our API ecosystem.

The easy way to tell them apart is that all local IDs are prepended with a `pos_`.  These IDs are always local on the POS.  All other IDs are SubtleData ID numbers.
