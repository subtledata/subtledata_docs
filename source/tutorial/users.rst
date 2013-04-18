.. _tutorial_users:

Tutorial: Users
===============
Users represent individual end-user accounts on our system at SubtleData.  You are free to use it as your primary authentication and user database or use your own and obfuscate.  Either way, you need to be familiar with our User objects.

Users have the following attributes:

* User ID
* Username
* Password
* Cell Phone
* Email
* Device IDs

**Please Note:** Getting user information requires a valid Device ID.  You should make sure to store at least one so that you can later access the user's details.

Creating a User
^^^^^^^^^^^^^^^

Creating a user is as simple as a single POST call.  We will POST to our create user endpoint: ::
   
    https://api.subtledata.com/v1/users?api_key=@@@@@

With our user's data in the POST body: ::

	{
		"first_name": "Jon",
		"last_name": "Doe",
		"middle_name": "Deer",
		"dob": "01/01/1980",
		"email_address": "jdoe@gmail.com",
		"cell_phone": "string",
		"password": "helloTh3r3",
		"user_name": "jdoe",
		"device_uuid": "1234-5678-9123"
	}

We will get back a response showing our user's creation: ::

	{
	  "user_guid": "d7c64f26-52a6-4315-b051-03681e653127",
	  "user_id": 3372,
	  "device_id": 3680
	}

**Again, please keep the user_id and device_id as they are very important identifiers.**

Getting a User
^^^^^^^^^^^^^^

Fetching a user is as simple as querying their user ID: ::

    https://api.subtledata.com/v1/users/3372?api_key=S0YrNTJY

Which will give us: ::

	{
	  "first_name": "Jon",
	  "last_name": "Doe",
	  "middle_name": "Deer",
	  "dob": "01/01/1980",
	  "email_address": "jdoe@gmail.com",
	  "last_known_lon": 0,
	  "last_known_lat": 0,
	  "user_id": 3372,
	  "cell_phone": "string",
	  "user_name": "jdoe"
	}

Authenticating a User
^^^^^^^^^^^^^^^^^^^^^

To authenticate a user, make a POST to our authentication endpoint: ::

    https://api.subtledata.com/v1/users/authenticate?api_key=S0YrNTJY

Which will return a success or failure status and some user details: ::

	{
	    "user_id": 3372,
	    "result": "SUCCESS",
	    "success": true,
	    "device_id": 3680
	}

If you pass the same device_uuid, then you will get the same device_id back.  Otherwise, they will be different.

Next Steps
^^^^^^^^^^

Now, let's play with some locations in our next step :ref:`tutorial_locations`.