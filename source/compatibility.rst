.. _pos_compatibility:

POS Compatibility
=================
SubtleData's POS Plugin is compatible with more systems than any other POS integration in the world.  It integrates with:

* Micros 3700, 9700, Simphony, and E7
* Dinerware
* POSitouch
* Quest Concessions
* Revel Systems
* InfoGenesis
* SalesVu
* Squirrel

Compatibility Matrix
--------------------
Due to the different nature of each point of sale system, not all of our calls are functional across all systems and some may function slightly differently.  For instance, Dinerware has the capability to display a custom name on each ticket whereas Micros 3700 does not.  Dinerware requires no additional setup to be compatible with our credit card processing capabilities while Micros requires a Transaction Services License.

You can find a table of the capabilities of each system below.

===================== ========= ===== ========= ========= =====
Feature               Dinerware M3700 MSimphony POSitouch Quest
--------------------- --------- ----- --------- --------- -----
Get Ticket Details    X         X     X         X         X
Open Ticket           X         X     X         X         X
Pay Ticket with CC    X         X     X         X         X
Pay Ticket Externally           X     X         X         X
===================== ========= ===== ========= ========= =====

Micros 3700 Details
-------------------
The Micros 3700 is a very common system at restaurants.  We have full compatibility with our API.  In order to process payments, your client location will need to purchase and set up a Transaction Services License (TSL) from their Micros dealer.  This process can take up to 10 business days so you should start now if you need these capabilties.

Dinerware Details
-----------------
No additional setup is required for full Dinerware compatibility

Next Steps
^^^^^^^^^^

Next, you'll learn about connecting to the POS in :ref:`location_setup`.