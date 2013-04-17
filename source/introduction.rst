.. _introduction:

Introduction
============

The SubtleData system allows web and mobile applications to access the capabilities of point of sale systems at restaurant and hospitality providers.  You can utilize these capabilities for all kinds of applications.  For instance, you could:

* Display a restaurant's menu dynamically on a mobile device
* Show a user their ticket totals and item level details
* Pay for a user's ticket via their mobile phone
* Let a user order directly from their seat or online
* Discount a user's ticket remotely
* Track a user's dinners over multiple locations

And so much more.

SubtleJSON makes this incredibly easy by:

* Following RESTful standards
* Using logical, easy to read endpoints
* Presenting clear, direct JSON result documents
* Providing a dynamic and live interactive terminal

SubtleData consists of three parts:

* The SubtleData POS Plugin
* The SubtleData Website
* The SubtleJSON API

The SubtleData POS Plugin
-------------------------
Our POS Plugin is a windows application that sits on the back office computer serving the point of sale system at a location (ie. a restaurant or hospitality provider).  It connects with SubtleData's systems and constantly keeps the two in sync, allowing you to access data residing on the POS from your application.  Installation and setup of the POS Plugin is covered later in this tutorial.

The SubtleData Website
----------------------
The SubtleData website is where you manage your locations, set up your applications, get your applications' secret keys, and otherwise manage your relationship with SubtleData.

The SubtleJSON API
------------------
The SubtleJSON API is where rubber meets road.  You use your secret keys obtained from our website to access the data we have synced with the POS Plugin.  You can also act upon this data in many ways such as creating tickets and ordering items.

Next Steps
^^^^^^^^^^

Next, learn about our :ref:`pos_compatibility`.