============================
Content API:  Legal Question
============================

Returns a specific question and answer. The UUID of the question must be provided.

Function call
================

Method:  GET


Sample response
================

.. code-block:: json

   [{
	"question": [{
			"name": "How long does an Order of Protection last?",
			"acceptedAnswer": {
				"body": ["If you live with your abuser, you can ask for exclusive possession of the home. The abuser will have to leave and stay away from the home. If the abuser has a legal right to be in the home, the judge will need to decide whether it is more difficult for you or the abuser to leave.",
					"The judge may ask if you have another place to stay, your abuser has another place to stay, any children live with you, both of you work, or if your home is near your workplace or your children's school. ",
					"If the judge orders exclusive possession, call the police and ask that they escort you home. Tell the police officer that you have an Order of Protection and need the respondent removed from your home. The police will meet you at your home and tell the abuser they have to leave.",
					"The court can order that you or the abuser be able to go into the house without the police to get clothing, medicine, or other items you need."
				]
			},
			"identifier": "b06e8c24-38ab-11eb-adc1-0242ac120002",
			"language": "en"
		}

	]
  }]
  
Parameters
=============

* question_identifier:  uuid of the question to return.   



