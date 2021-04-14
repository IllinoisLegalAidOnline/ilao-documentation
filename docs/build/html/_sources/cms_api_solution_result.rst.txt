===================================
Content API:  Solution Result
===================================


Returns the result for a solution.

Function call
================

Method: GET

Sample response
=================

.. code-block:: json

   [{
		"body": [
			"When a judge signs an Order of Protection, it makes it illegal for the Respondent to do or not do certain things. A judge may require the Respondent to:"
		],
		"list": [{
			"itemListOrder": "Unordered",
			"itemListElements": [{
					"item": "Stop abusive acts,"
				},
				{
					"item": "Stay away from the victim and other people protected by the order,"
				},
				{
					"item": "Not contact the victim via telephone calls, mail, email, written notes, or third parties,"
				},
				{
					"item": "Stay away from the victim's home, school, or work,"
				}
			]
		}]
	}
   ]


Parameters
==============

* solution_identifier:  uuid of the solution; required.
