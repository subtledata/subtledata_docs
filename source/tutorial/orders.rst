.. _tutorial_orders:

Tutorial: Orders
===================

Orders contain items and modifiers which the user wants prepared for them at their location on their ticket.  Ordering can be used for all kinds of fascinating things.  For instance, SubtleData demonstrated at the 2013 SXSW festival a mobile ordering app where you could order beers through a web application.  They would simply show up right at your table.

.. tip:: The code for the SXSW mobile ordering app is open source.  You can find it on `GitHub`_.

.. _GitHub: https://github.com/subtledata/sxsw_ordering

Order Process
-------------

The ordering process consists of two steps.  First, you must place items into "staging" and then you must place the actual order.  Each ticket has one staged order at any given time.  Then, you must place the order.  Placing the order will send the items to the appropriate printers and such.  Think of staging as the server touching buttons to add items on a POS and placing the order as them tapping on *Save*.

Retrieve the Menu
-----------------

Before we can order items, we need to know which items are available to order!  So let's fetch our location's menu: ::
    
    https://api.subtledata.com/v1/locations/959/menu?api_key=S0YrNTJY

This will give us an easy to parse set of categories with items in them: ::

	[
	  {
	    "items" : [
	      {
	        "name" : "Bud Ice",
	        "price" : 2.5,
	        "description" : null,
	        "revenue_center_id" : 1958,
	        "item_id" : 215730,
	        "item_images" : null
	      },
	      {
	        "name" : "Bud Light Bottle",
	        "price" : 2.25,
	        "description" : null,
	        "revenue_center_id" : 1958,
	        "item_id" : 215727,
	        "item_images" : null
	      }
	    ],
	    "has_items" : true,
	    "instructional_text" : null,
	    "category_images" : null,
	    "category_id" : 6792,
	    "has_subcategories" : false,
	    "category_name" : "Bottle Beer"
	  },
	  {
	    "items" : [
	      {
	        "name" : "Alice White Chard (Bottle)",
	        "price" : 11,
	        "description" : null,
	        "revenue_center_id" : 1958,
	        "item_id" : 215808,
	        "item_images" : null
	      },
	      {
	        "name" : "Alice White Shiraz (Bottle)",
	        "price" : 10.5,
	        "description" : null,
	        "revenue_center_id" : 1958,
	        "item_id" : 215601,
	        "item_images" : null
	      }
	    ],
	    "has_items" : true,
	    "instructional_text" : null,
	    "category_images" : null,
	    "category_id" : 6793,
	    "has_subcategories" : false,
	    "category_name" : "Bottle Wine"
	  },
	  {
	     "...": "..."  
	  }
	]

Stage Items for Ordering
------------------------
Coming Soon

Place The Staged Order
----------------------


Order Modifiers
---------------

Order modifiers are not currently available but are on the roadmap for SubtleJSON.

Next Steps
^^^^^^^^^^

Now that we have some items on our order, it's time to settle our bill: :ref:`tutorial_payments`.