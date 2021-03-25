======================
OTIS SMS API
======================

This documents our integration between the website and SMS to provide the needed functionality between ILAO's database, LegalServer, and Twilio for online intake.

Create triage user
=====================
Within Twilio, we have the ILAO service for functions.  The `/otis-create-triage-user <https://ilao-8092.twil.io/otis-create-triage-user>`_ function creates a data packet based on ILAO's OTIS Rest API to create a triage user record in our database.  The API returns the UUID of the newly created triage user entity.

The triage user is initially created after the user identifies their legal issue (OTIS-master).  At this point we have:

* Zip code, county, state
* Legal problem
* Search term (initial triggering input)
* Mobile phone
* Opt-in
* Timestamps
* Triage status of started
* Source
* Last screen viewed



Update triage user
=====================
The `/otis-update-triage-user <https://ilao-8092.twil.io/otis-update-triage-user>`_ function creates a data packet based on ILAO's OTIS Rest API to update an existing triage user based on the UUID.  

It ignores any parameters that are not part of the ILAO OTIS Rest API.

Within the OTIS Master, triage user records are updated:

* When the user is exited for being over-income on the initial income question
  * Household size is stored
  * Over-income status is stored

* When the user accepts or rejects a match

* After the user provides household size details 
* After the user provides a valid DOB
* After demographic questions
* After total income is calculated and overincome flags set
* After contact information is set
* After callback selections
* At end for any remaining data

Notes:

* Need a better overincome exit after route-income-resources





Post to legal server
=======================

Relies on the otis-send-to-legal-server and otis-legal-server-failure functions


Get intake settings
======================

TBD
