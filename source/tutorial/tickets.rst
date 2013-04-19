.. _tutorial_tickets:

Tutorial: Tickets
===================

Tickets are the basis of restaurant and hospitality bills.  They contain all of the items a person has ordered, sum up the amounts owed, and reconsile end payments.  SubtleData's ticketing system not only allows you to read ticket information, but also open tickets, order items, and settle payments.  The capabilities of the ticketing API are vast and take some time to master, but once you do, you control the entire point of sale experience.

POS IDs vs. SubtleData IDs
--------------------------

Tickets have two identifiers.  The first is entirely unique and is it's SubtleData ID (called `ticket_id` in the JSON).  This ID is unique to a ticket across locations but it is unknwown to the restaurant and not present on the POS or receipt.  The second is an ID unique to the point of sale system at the location in question.  This is the POS ticket ID.  It is present on receipts at the location and can be used to link to a receipt without having opened the ticket in question.  Understanding this concept and difference is important.  As a rule of thumb, if you are opening tickets or looking at open tickets remotely, you should be using the `ticket_id`.  If you are asking users to interact with their receipt, you shoudld be using `pos_ticket_id`.

Retrieving a Ticket with a Receipt ID
-------------------------------------

Our first step is not to actually create a ticket, but to fetch one.  Specifically, let's say we want to fetch an open (unpaid) ticket by the ticket identifier that is present on the receipt (its "pos_ticket_id"). Let's ping our POS ticket ID endpoint with a GET request: ::

    http://0.0.0.0:5005/v1/locations/448/tickets/pos/55384?api_key=S0YrNTJY

This will return our ticket details: ::

	{
	  "employee_id" : 6606,
	  "ticket_open" : true,
	  "user_id" : null,
	  "items" : [
	    {
	      "item_modifiers" : [
	        {
	          "name" : "Bare",
	          "modifier_id" : 13656,
	          "instructions" : null
	        }
	      ],
	      "name" : "Big Boy Burger",
	      "available_for_order" : true,
	      "ticket_item_id" : 384653,
	      "price" : 5.25,
	      "voided" : false,
	      "item_id" : 143128,
	      "instructions" : null,
	      "quantity" : 1
	    },
	    {
	      "item_modifiers" : null,
	      "name" : "Jack Daniel",
	      "available_for_order" : true,
	      "ticket_item_id" : 384677,
	      "price" : 3.5,
	      "voided" : false,
	      "item_id" : 143086,
	      "instructions" : null,
	      "quantity" : 1
	    },
	    {
	      "item_modifiers" : null,
	      "name" : "Jack Daniel",
	      "available_for_order" : true,
	      "ticket_item_id" : 384964,
	      "price" : 3.5,
	      "voided" : false,
	      "item_id" : 143086,
	      "instructions" : null,
	      "quantity" : 1
	    },
	    {
	      "item_modifiers" : null,
	      "name" : "Ariel Cabernet",
	      "available_for_order" : true,
	      "ticket_item_id" : 386432,
	      "price" : 3,
	      "voided" : false,
	      "item_id" : 143263,
	      "instructions" : null,
	      "quantity" : 1
	    },
	    {
	      "item_modifiers" : null,
	      "name" : "Leep Lizard Wings - 30",
	      "available_for_order" : true,
	      "ticket_item_id" : 386433,
	      "price" : 14.75,
	      "voided" : false,
	      "item_id" : 143057,
	      "instructions" : null,
	      "quantity" : 1
	    },
	    {
	      "item_modifiers" : null,
	      "name" : "Woodridge Chard",
	      "available_for_order" : true,
	      "ticket_item_id" : 389469,
	      "price" : 3,
	      "voided" : false,
	      "item_id" : 143253,
	      "instructions" : null,
	      "quantity" : 1
	    }
	  ],
	  "tax" : 0,
	  "discount" : 0,
	  "pos_ticket_id" : 55384,
	  "remaining_balance" : 33,
	  "table_name" : "Bar 3",
	  "ticket_id" : 38216,
	  "connected_users" : [
	    
	  ],
	  "table_id" : 15634,
	  "total" : 33,
	  "subtotal" : 33,
	  "service_charge" : 0,
	  "payments" : [
	    
	  ]
	}

That's it!  Closed tickets will even include payment information as well as information about the users who participated in the ticket.

Retrieving a Ticket with a Ticket ID
-------------------------------------

Frequently, we just want to fetch the ticket in question and we have its unique SubtleData ID.  Similar to above, you hit a GET endpoint, but you don't need to specify that it is a POS ID: ::

	http://0.0.0.0:5005/v1/locations/448/tickets/38216?api_key=S0YrNTJY

.. tip:: This will return the same results as above.

Retrieving Open Tickets for a Table
-----------------------------------

Oftentimes you know a table number and want to get open tickets at the table.  This is fortunately easy as well.  First, let's look up our location's tables: ::


    https://api.subtledata.com/v1/locations/959/tables?api_key=S0YrNTJY

This will give us our list: ::

	[
	  {
	    "pos_table_id": 50,
	    "table_open": false,
	    "subtledata_id": 43143,
	    "name": "Bar 1",
	    "revenue_center_id": 1958
	  },
	  {
	    "pos_table_id": 51,
	    "table_open": true,
	    "subtledata_id": 43144,
	    "name": "Bar 2",
	    "revenue_center_id": 1958
	  },
	  {
	    "pos_table_id": 52,
	    "table_open": true,
	    "subtledata_id": 43145,
	    "name": "Bar 3",
	    "revenue_center_id": 1958
	  },
	  {
	    "pos_table_id": 53,
	    "table_open": true,
	    "subtledata_id": 43146,
	    "name": "Bar 4",
	    "revenue_center_id": 1958
	  },
	  {
	    "pos_table_id": 54,
	    "table_open": true,
	    "subtledata_id": 43147,
	    "name": "Bar 5",
	    "revenue_center_id": 1958
	  },
	  {
	    "pos_table_id": 55,
	    "table_open": true,
	    "subtledata_id": 43148,
	    "name": "Tom Perkins",
	    "revenue_center_id": 1958
	  },
	  {
	    "pos_table_id": 56,
	    "table_open": true,
	    "subtledata_id": 43149,
	    "name": "Tony",
	    "revenue_center_id": 1958
	  }
	]

Next, we sort through our list to find the table in question using it's POS ID.  Let's say we are looking for open tickets at table 50.  We see that its subtledata_id is 43143.  So let's fetch its details: ::

	{
	  "pos_table_id" : 50,
	  "open_tickets" : [
	    {
	      "employee_id" : 6606,
          "...": "..."
	      "ticket_id" : 38216,
	      "connected_users" : [
	        
	      ],
	      "table_id" : 43143,
	      "total" : 33,
	      "subtotal" : 33,
	      "service_charge" : 0,
	      "payments" : [
	        
	      ]
	    }
	  ],
	  "subtledata_id" : 43143,
	  "name" : "Bar 1",
	  "revenue_center_id" : 1958
	}

The `open tickets` field will contain the open tickets for the table in question.  You can then easily manipulate the tickets via any of the other ticket/menu/payment calls via their ticket_id.

Open a Ticket
-------------

Now that we know what tickets look like and how to fetch them, let's do something more complex.  Let's create a ticket.  To do this, we will need a few pieces of information.

* The type of ticket being opened (only `dine-in` is supported at the moment)
* The details of the user opening the ticket *including device ID*
* The SubtleData location and table IDs where we are opening the ticket
* The revenue center to which the ticket should be attributed

.. hint:: The revenue center ID can be found in the location's details.

Let's say we are opening a ticket with our user from earlier.  His user ID was 3372 and his device_id was 3680.  There are our first two pieces of information.

Next, we want to open a new ticket at location 959 and table 50, where the SubtleData ID is 43143.  From our location information call, we can see that our only revenue center has an ID of 1958.  We now have all the information we need!  So we make a POST call to our tickets endpoint: ::

    https://api.subtledata.com/v1/locations/959/tickets?api_key=S0YrNTJY&ticket_type=dine-in

With our ticket information: ::

	{
	  "user_id" : 3372,
	  "device_id" : 3680,
	  "table_id" : 43143,
	  "revenue_center_id" : 1958
	}

We will get back our new ticket's information, including its all important `ticket_id`: ::

	{
	    "result": "SUCCESS",
	    "success": true,
	    "ticket_id": 88929
	}

We can now manipulate the ticket in any way we would like.

Next Steps
^^^^^^^^^^

And that is how you interact with tickets!  Now, let's make some orders: :ref:`tutorial_tickets`.