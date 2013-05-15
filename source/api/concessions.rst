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
Here is an example POST body for an example credit card payment: ::

	{
	  "user_id": 2248,
	  "terminal_id": 631,
	  "revenue_center_id":1659,
	  "device_id": 2033,
	  "items":[
	    {"item_id":184395, "quantity":1}
	  ],
	  "payments":[
	    {
	      "tender_type_id": 1,
	      "name_on_card": "Bob Smith",
	      "card_number": "4443332221110001",
	      "expiration_month":"04",
	      "expiration_year":"2015",
	      "billing_zip":"22222",
	      "amount_before_tip":12.05,
	      "tip_amount": 0
	    }
	  ]
	}


Cash Payment
-------------------------------------
Here is an POST body for an example cash payment (note the tender_type_id of 5). ::

	{
	  "user_id": 2248,
	  "terminal_id": 631,
	  "revenue_center_id":1659,
	  "device_id": 2033,
	  "items":[
	    {"item_id":184395, "quantity":1}
	  ],
	  "payments":[
	    {
	      "tender_type_id": 5,
	      "amount_before_tip":12.05,
	      "tip_amount": 0
	    }
	  ]
	}