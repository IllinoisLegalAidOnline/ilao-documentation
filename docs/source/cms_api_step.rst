==========================
Content API:  Legal Step
==========================

Returns a specific Legal Step. The UUID of the specific Legal Step must be provided.

Function call
=================

Method: GET

Sample response
==================

.. code-block:: json

    [{
 	"name": "Make sure you are safe",
 	"identifier": "396fdcd8-3a61-11eb-adc1-0242ac120002",
 	"position": 1,
 	"howToDirections": [{
 		"position": 1,
 		"direction": "Domestic violence victims are most likely to be attacked when they leave the abuser and/or when they seek legal help. A safety plan[1] increase your safety and prepare you in advance for violence that may happen in the future. See [1] https://www.illinoislegalaid.org/node/30281",
 		"referenceUrls": [
 			"https://www.illinoislegalaid.org/node/30281"
 		]
 	}],
 	"howToTips": [{
 		"position": 2,
 		"tip": "You don't have control over your partner's violence, but you do have a choice about how to respond, and how best to get you and your loved ones to safety."
 	}]
 }]

Parameters
=============
* step_identifier:  uuid of the step. Required 
