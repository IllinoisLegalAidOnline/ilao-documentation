====================================
Content API:  Legal Questions List
====================================


Returns list of questions from the legal question content type. The list will be limited if optional parameters are included.


Function call
===============

Method: GET


Sample response
===============

.. code-block:: json

   [{
	"questions": [{
			"name": "How long does an Order of Protection last?",
			"identifier": "b06e8c24-38ab-11eb-adc1-0242ac120002",
			"language": "en"
		},
		{
			"name": "What if my abuser lives with me?",
			"identifier": "b06e8c24-38ab-11eb-adc1-0242ac120002",
			"language": "en"
		},
		{
			"name": "What if I have pets?",
			"identifier": "b06e8c24-38ab-11eb-adc1-0242ac120002",
			"language": "en"
		}

	]
  }]
  

Parameters
============

* language. The 2 digit ISO code for supported languages
* coverage area:

   * administrativeArea (one of County, City, Postal code)
   * locality: the value of the administrativeArea to return

