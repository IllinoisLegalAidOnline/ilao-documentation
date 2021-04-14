====================================
Content API: Legal Problems List
====================================

Returns a list of legal problem content from the website. This is a simple list of:

* name
* description
* identifier
* language

Function call
=================

Method: GET


Sample Output
==================

.. code-block:: json

    [{
 		"name": "Being a victim of domestic violence",
 		"description": "Legal problem of being a victim of DV",
 		"identifier": "a6a6eb74-38c3-11eb-adc1-0242ac120002",
 		"language": "en"

 	},
 	{
 		"name": "Being evicted",
 		"description": "Legal problem of being evicted",
 		"identifier": "a6a6eb74-38c3-11eb-adc1-0242ac120002",
 		"language": "en"
 	}
 ]
 
Parameters
=================
The following parameters are optionally allowed:

* lifeAreaAffected - the term name from our life area taxonomy
* legalCodeValue - a value from a supported coding system
* legalCodingSystem - either NSMI and LSC problem codes 
* language based on the 2 character ISO language codes 