=================================
Content API:  Legal Form
=================================

Returns information for a specific Legal Form. The form UUID must be provided.

Function call
==============

Method: GET

Sample response
===================

.. code-block:: json

   [
   {
		"formName": "Emergency Order of Protection",
		"identifier": "2d839738-3a3a-11eb-adc1-0242ac120002",
		"filledOutWith": [{
			"name": "Order of Protection",
			"url": "https://www.illinoislegalaid.org/legal-information/order-protection",
			"formPrepProgramType": "HotDocs"
		}],
		"formUse": "An EOP is only valid for 14 to 21 days"
	}
  ]

Parameters
==============
* form_identifier:  uuid of the form.