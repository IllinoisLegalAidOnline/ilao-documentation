==========================================
Content API:  Solution Eligibility Rules
==========================================

Returns the eligibility rules for a specific legal solution. The UUID of the solution must be provided.

Function call
=================

Method:  GET

Sample response
================

.. code-block:: json

   [{
 		"body": [
 			"One of the following must be true:"
 		],
 		"list": [{
 			"itemListOrder": "Ascending",
 			"itemListElements": [{
 					"item": "Petitioner lives in Illinois",
 					"position": 1
 				},
 				{
 					"item": "Abuse happened in Illinois, or",
 					"position": 2
 				},
 				{
 					"item": "Petitioner is staying in Illinois to avoid abuse",
 					"position": 3
 				}
 			]
 		}]
 	},
 	{
 		"body": [
 			"There must have been abuse by the Respondent. Abuse includes physical abuse, harassment, intimidation of a dependent, interference with personal liberty, and willful deprivation."
 		]
 	},
 ]

Parameters
================
* solution_identifier:  UUID of the solution.