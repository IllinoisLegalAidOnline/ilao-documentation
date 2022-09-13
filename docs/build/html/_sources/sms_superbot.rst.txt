=============================
SMS Short Code Architecture
=============================

Subflow: Otis Get Location
============================

Purpose: Determines whether the user is in Illinois or not.

Parameters: none
Returns:

first_name
location (from pilot-validate-zipcode function)


Subflow: OTISGuided Navigation
================================

Purpose: Executes a specific Guided Navigation segment

Parameters: process_id
Returns:

* Status
* Profile (the completed Guided Navigation profile)
* Notes
* rest_export
* lsc_code
* content_url

Subflow: Get Legal Issue
==========================

Purpose: Validates input from the user and gets the correct process id

Parameters: keyword

Returns: status (success, failed)
If success, returns:

* process_id
* lsc_code
* search_term
* content_url
* rest_export





Subflow: Run household information
===================================


Subflow: OTIS income intake
===========================

Purpose: Gathers income information and validates income eligilibty

Parameters: Organization match

Returns:

* total_income
* income_private_disability
* income_investments
* income_tanf
* income_veterans_amount
* income_unemployment
* income_ssi
* income_social_security
* income_alimony
* income_child_support
* income_workers_comp
* income_pension
* income_investments
* income_other_income
* income_wages
* income_self_employment
* wage_frequency


Subflow: OTIS demographics
============================

Purpose: Asks and validates demographic information

Parameters: None

Returns:

* marital_status
* preferred_language
* race
* ethnicity
* marital_status

Subflow:






