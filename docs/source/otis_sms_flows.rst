====================
Flows and Subflows
====================

Primary flow
=============
Users applying over SMS enter a primary flow that controls a series of subflows. The primary flow is aptly named "Superbot" with the version number and the date it went live. The Superbot flow is greatly simplified with the use of subflows. The flow is visually structured in 3 columns starting at the top right and moving first down and then to the top of the column to the left of the current column. 

Each time Superbot starts a subflow, variables that are needed for that subflow are passed to the subflow as parameters from the run subflow function. The language variable is passed into every subflow to allow the system to respond to the user in the correct language.

Adding parameters to a subflow
.. image:: ../assets/otis-subflow-parameters.png

Setting variables for the subflow
..image:: ../assets/otis-subflow-variables.png

Subflows
=========

NOTE: documentation on each subflow is coming soon.

* **OTIS get legal issue:**
* **OTIS get location:**
* **OTIS household:**
* **OTIS Guided Navigation:**
* **OTIS matches:**
* **OTIS Guided Navigation:** If the matched/chosen organization has qualifiers to determine if the applicant is a good match, the OTIS Guided Navigation flow is run again to run the particular qualifier guided navigation path
* **OTIS Intake:**
* **OTIS contact information:**
* **OTIS appointment scheduler:**
