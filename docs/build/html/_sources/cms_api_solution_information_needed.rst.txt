==========================================
Content API:  Solution Information Needed
==========================================


Returns the eligibility rules for a specific legal solution. 

Function call
================
Method:  GET

Sample Response
=================
.. code-block:: json
  
 [
 	"Petitioner's address",
 	"Petitioner's alternate address for safety (optional)",
 	"Respondent's address",
 	"Physical description of Respondent",
 	"Respondent's employer",
 	"Details about any other Orders of Protection or other court cases involving the Petitioner or the Respondent.",
 	"Details about the abuse and when it took place.",
 	"Details about personal property that Petitioner wants back."
 ]

Parameters
=============
* solution_identifier:  uuid of the solution.
