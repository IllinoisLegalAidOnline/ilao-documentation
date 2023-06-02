==========================
Legal Server Signup
==========================


The Legal Server implementation anticipates having 2 pieces:

* An iFrame from our website to subscribe the user
* An API post to update the subscribed users data

IFrame Form
===============

ILAO will provide an iFrame url to partners for inclusion in their instance of LegalServer. The form will include:

* List of published Legal Flows
* List of steps for a selected How-to
* A field ot collect the client's mobile-number
* Language preference of the client
* Client's zip code
* Opt in field
* Hidden organization ID as a query parameter

When submitted this will create a nextStepsUserEntity with:

* Automatically generated ID
* NID of the Selected flow
* NID of the Selected legal step


API Post
==============
ILAO will work with partners to implement an API block that will post back to ILAO. This API call will post:

* The user's mobile phone number
* The uuid from legal server


Once posted, the website will:

* Update the NextStepsUser entity with the uuid based on the phone number where the uuid is empty
* Query the otis_triage_user table to check for the uuid; if found will add the triage user id to the NextStepsUser entity

