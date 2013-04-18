.. _tutorial_locations:

Tutorial: Locations
===================

Locations are the most important objects in SubtleData.  They represent each installation you have access to.  With locations, you can interact with ordering, ticketing, menuing, payments, etc..  But it all feeds back to a location.  So let's see one!

Fetching a Location
-------------------

Querying a location's details are very simple.  You hit the location endpoint with the location ID you are interested in.  If we want to fetch location 959, we make a GET call to: ::

    https://api.subtledata.com/v1/locations/959?api_key=S0YrNTJY

Which will yield us: ::

	{
	  "revenue_centers": [
	    {
	      "default_center": false,
	      "revenue_center_id": 1958,
	      "name": "Unassigned Revenue"
	    }
	  ],
	  "receipt_number_instructions": null,
	  "employee_request_through_app": false,
	  "menu_ordering_available": true,
	  "payment_via_credit_card_available_message": null,
	  "postal_code": "78610",
	  "location_id": 959,
	  "app_specials": false,
	  "city": "Austin",
	  "location_name": "Dev Site Testing",
	  "tender_types": [],
	  "process_new_credit_cards": false,
	  "user_rating": "0",
	  "table_number_instructions": null,
	  "state": "TX",
	  "color_theme": null,
	  "latitude": 30.2625409,
	  "logo_url": "http://www.subtledata.com/I/Logo/?959",
	  "website_url": null,
	  "cross_streets": null,
	  "ordering_available_message": null,
	  "phone": "4156400650",
	  "terminals": [],
	  "location_picture_url": "http://www.subtledata.com/I/Results/?959",
	  "favorites_ordering_available": true,
	  "neighborhood_name": null,
	  "discount_types": [
	    {
	      "default_discount": false,
	      "discount_type_id": 700,
	      "name": "Employee"
	    },
	    {
	      "default_discount": false,
	      "discount_type_id": 701,
	      "name": "Two Dollar Tuesday"
	    }
	  ],
	  "longitude": -97.7448585,
	  "price_rating": 0,
	  "process_pre_authed_cards": false,
	  "address_line_2": null,
	  "address_line_1": "1 Congress St"
	}

This is obviously a lot of information.  But a lot of very useful information.  We have our location's address, lat/lon, discount types, name, etc..  Pretty much all of the info we would need to display details for a location.

Filtering Locations
-------------------

Now what about if you want to see locations near a point?  Well, fortunately, that's easy too.  You make a GET call with the latitude, longitude, and radius (in miles) that you want to see locations for: ::

    https://api.subtledata.com/v1/locations/filter/near?api_key=S0YrNTJY&latitude=30.26&longitude=-97.74&radius=10

This will give us a JSON list of all matching locations (which in this case is just the one): ::

	[
	  {
	    "revenue_centers": [
	      {
	        "default_center": false,
	        "revenue_center_id": 1958,
	        "name": "Unassigned Revenue"
	      }
	    ],
	    "receipt_number_instructions": null,
	    "employee_request_through_app": false,
	    "..." : "...",
	    "address_line_2": null,
	    "address_line_1": "1 Congress St"
	  }
	]

Next Steps
^^^^^^^^^^

So let's use our location!  Next up, you'll learn about ticketing: :ref:`tutorial_tickets`.