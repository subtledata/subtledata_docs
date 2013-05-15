.. _concession_calls:

Concession Tickets
===================

Concession tickets are unique in that the order is completed entirely within a single API call.  Items and payments are included in the same call.

System Compatibility
--------------------------
Concession style ticket calls are available on the Micros Simphony and 9700 systems.  We are integrating new systems constantly.  Please reach out if you have a system you would like to see us implement.

Items
-------------------------------------

Items are passed in the request body as a list of item_ids and quantities.  An example item is: ::

	{"item_id":12345, "quantity":2}

Endpoint
-------------------------------------
The Concession Ticket ordering endpoint is available using the POST HTTP method at: ::

    https://api.subtledata.com/v1/concessions/<int:location_id>/order

You should use the proper location_id and append your api_key as usual.


Credit Card Payment
-------------------------------------


Cash Payment
-------------------------------------
