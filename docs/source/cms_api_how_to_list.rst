===========================
Content API:  How To List
===========================


Returns a list of how-to structured content. A solution identifier UUID may be included which will limit the results to those how-to's embedded in that solution.

Function call
===============

Method:  GET

Sample response
=================

.. code-block:: json

   [{
		"name": "Getting an order of protection",
		"description": "An Order of Protection can help protect you or a loved one from abuse. This article explains how to get one",
		"identifier": "9ea16654-38cb-11eb-adc1-0242ac120002",
		"language": "en"
	},
	{
		"name": "Changing or renewing an order of protection",
		"description": "The person who asked for an Order of Protection can ask the judge to change, end, or renew it.",
		"identifier": "9ea16654-38cb-11eb-adc1-0242ac120002",
		"language": "en"
	}
  ]

Parameters
============

* solution_identifier:  uuid of the solution; when provided will limit the list of how-tos to those tied to a solution.
