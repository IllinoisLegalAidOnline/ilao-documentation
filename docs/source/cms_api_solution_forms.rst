==========================================
Content API:  Legal Solution Forms Needed
==========================================


Returns the list of legal forms needed from a specific solution. The solution's UUID must be provided.

Function call
===============

Method: GET

Sample response
=================
.. code-block:: json

   [{
		"formName": "Petition for Order of Protection",
		"identifier": "2d839738-3a3a-11eb-adc1-0242ac120002",
		"filledOutWith": [{
				"name": "Order of Protection",
				"url": "https://www.illinoislegalaid.org/legal-information/order-protection",
				"formPrepProgramType": "HotDocs"
			},
			{
				"name": "Petition for Order of Protection",
				"url": "https://www.illinoislegalaid.org/legal-information/order-protection.pdf",
				"formPrepProgramType": "PDF"
			}
		]
	},
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
============

* solution_identifier:  uuid of the solution.
