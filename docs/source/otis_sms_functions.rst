.. _twilio_functions:

=====================
Twilio Functions
=====================

This documents the functions stored in our Twilio function service "ilao."

All of our Twilio functions are stored in the ilao service in Twilio's functions.

Guided navigation functions used in our Twilio SMS are documented in :ref:`guided_nav_functions` documentation.

Function standards
======================
All function names are written in the word-word-word format.


All passed in parameters are contained in the event object.

OAuth get token
==================
**Function name:**  oauth-get-token

**Parameters:**  none

**Returns:** an access token

**Requires:**  A consumer for our API account and a user account to call.

.. note:: The following functions rely on the OAuth token:

* otis-create-triage-user
* otis-triage-user
* eviction-intake-settings
* otis-get-matches
* eviction-matches

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   otis_global_functions
   otis_eviction_functions
   otis_triage_intake_functions
   otis_guided_nav_functions
   otis_website_data_integration_functions



OTIS get confirmation
======================

**Function name:**  otis-get-confirmation

**Parameters:**  event.intakeSettingsId and event.callbackType

**Requires:**  ILAO API call to get the return message based on the intake settings id and callback type.

**Status:**  This is a placeholder function right now. It returns either the "we call" or "you call" message" as a JSON object.

OTIS Get Callback Days
========================

**Function name:**  otis-get-callback-days

**Parameters:**  event.intakeSettingsId

**Requires:**  ILAO API call to get the next [x] days of available intake appointments.

**Status:**  This is a placeholder function right now. It returns a JSON object of days for the user to pick from. Currently, it is using an array of days and a string of days to output. This needs to be revised to return a key value pair that can be rendered while still having useful info for the system.

OTIS Get First Callback Time
===============================

**Function name:**  otis-get-first-callback-time

**Parameters:**  event.intakeSettingsId

**Requires:**  ILAO API call to get the range of available hours and the first available date.

**Status:**  This is a placeholder function right now. It returns a JSON object of days for the user to pick from. It currently returns hard-coded text of:

* intro ('Callback times are between x and y');
* first ('The first available is [x]);
* callback-date: Stores the actual date in mm/dd/yyyy format.

OTIS Get Callback Times
===============================

**Function name:**  otis-get-callback-times

**Parameters:**  event.intakeSettingsId, event.callbackDate

**Requires:**  ILAO API call to get the range of callback slots for a specific date and intake settings pairing.

**Status:**  This is a placeholder function right now. It returns a JSON object of times for the user to pick from. It currently returns hard-coded text of:

* timeArray of available times
* times - string of times to display to user


OTIS Get Callback Type
===============================

**Function name:**  otis-get-callback-times

**Parameters:**  event.intakeSettingsId

**Requires:**  ILAO API call to get the callback type for a specific intake settings

**Status:**  This is a placeholder function right now. It returns a string of either "clientCalls" or "weCallClient"

OTIS Zipcode Validate
=======================

**Function name:**  otis-zipcode-validate

**Purpose**: Determines whether a provided zip code is in Illinois or not based on the Illinois regions asset, which is a JSON file from ILAO's region taxonomy and includes the zipcode, city, county, state, fips ID, and county UUID.

**Parameters:**  event.zip

**Requires:**  API call to get region information based on zip code.

**Returns:** An object (location) that contains:

* zip_code (the zip provided by the user)
* county
* state
* fips id for the county (required by Legal Server)


**Status:** Relies on a JSON object in our static assets (/illinois-regions) that contains the IL regional taxonomy data.









Increase intake counter
==========================

**Function name:**  otis-increase-intake-counter

**Purpose**:  Updates the current count for an intake setings id when a case is successfully transferred to Legal Server.

**Parameters:** event.current_count & event.uuid

**Requires:** JSON API for online intake

**Returns:** Nothing

**Status:** In development.

Get Matches
==========================

**Function name:**  otis-get-matches

**Purpose**:

**Parameters:**

**Requires:**

**Returns:**

**Status:** Not built

Conflict check
================
**Function name:**  otis-conflict-check

**Purpose**: Queries the Legal Server conflict check API for a specific organization to evaluate whether a user has a potential conflict.

**Parameters:** event.firstName, event.lastName

**Requires:**  A username, password, and url for each organization we need to run a conflict check on

**Returns:** An object of score (lowest, low, high, highest)


Send to Legal Server
======================

**Function name:**  otis-load-races

**Purpose**: Builds the data package to etransfer to LegalServer

**Parameters:** event object which contains the data for the eTransfer.

+-----------------------+---------------------+------------------------------------------+
| Event property        | LS property         | Description                              |
+=======================+=====================+==========================================+
| flow_id               |                     | Phone number the user texted to.  Used to|
|                       |                     | route between production/test environs   |
+-----------------------+---------------------+------------------------------------------+
| flowPrefix            | externalId          | Combined in the format of flow prefix-   |
+-----------------------+                     +                                          +
| triage_id             |                     | triage_id to crete a unique id           |
+-----------------------+---------------------+------------------------------------------+
| firstName             | firstName           | User's first name                        |
+-----------------------+---------------------+------------------------------------------+
| middleName            | middleName          | Not captured in SMS                      |
+-----------------------+---------------------+------------------------------------------+
| lastName              | lastName            | User's last name                         |
+-----------------------+---------------------+------------------------------------------+
| eTransferOrganization |eTransferOrganization| LegalServer-specific string for org.     |
|                       |                     | Is stored in website LS configuration    |
+-----------------------+---------------------+------------------------------------------+
| nickname              | aliasFirst          | Any entered nickname                     |
+-----------------------+---------------------+------------------------------------------+
| maiden                | aliasLast           | Any entered maiden name                  |
+-----------------------+---------------------+------------------------------------------+
| street                | addressHome.address1| addressHome is an Object containing the  |
+-----------------------+---------------------+                                          +
| city                  | addressHome.city    | street address, city, state, zip and     |
+-----------------------+---------------------+                                          +
| state                 | addressHome.state   | countyFIPS code provided by the user.    |
+-----------------------+---------------------+------------------------------------------+
| user_phone            | phoneHome           | Either the number the user texted from or|
+-----------------------+---------------------+                                          +
|                       |                     | a provided number, removed of any +1     |
+-----------------------+---------------------+------------------------------------------+
| month                 | dateOfBirth         | Date of birth provided by user.  A 0 is  |
+-----------------------+---------------------+                                          +
| day                   |                     | added for any month or day of less than  |
+-----------------------+---------------------+                                          +
| year                  |                     | 10                                       |
+-----------------------+---------------------+------------------------------------------+
| email                 | email               | User provided email addresss             |
+-----------------------+---------------------+------------------------------------------+
| maritalStatus         | maritalStatus       | User selected marital status             |
+-----------------------+---------------------+------------------------------------------+
| ethnicity             | ethicity            | User selected ethnicity; is set to blank |
|                       |                     | if user selects prefer not to respond.   |
+-----------------------+---------------------+------------------------------------------+
| gender                | gender              | User selected gender.                    |
+-----------------------+---------------------+------------------------------------------+
| language              | language            | User selected preferred language         |
+-----------------------+---------------------+------------------------------------------+
| notes                 | notes               | System-generated notes through triage.   |
+-----------------------+---------------------+------------------------------------------+
| household_adults      | numberOfAdults      | User provided number of adults           |
+-----------------------+---------------------+------------------------------------------+
| household_children    | numberOfChildren    | User provided number of children         |
+-----------------------+---------------------+------------------------------------------+
| callbackType          | callbackType        | Client calls or Callback                 |
+-----------------------+---------------------+------------------------------------------+
| callbackDayTime       | callbackDayTime     | Morning or afternoon for callbacks; empty|
|                       |                     | for client calls                         |
+-----------------------+---------------------+------------------------------------------+
| income_[type]         | income              | income is an object that has multiple    |
|                       |                     | objects for each provided income.  Each  |
|                       |                     |                                          |
|                       |                     | item contains a type, amount, & frequency|
+-----------------------+---------------------+------------------------------------------+
| legalProblemCode      | legalProblemCode    | Legal Server problem code                |
+-----------------------+---------------------+------------------------------------------+


Flow prefixes
---------------

  * For eviction, this is ILAOEvict.

.. note:: Some translation is done on fields such as gender, race, to accommodate differences between ILAO's taxonomy terms and Legal Server's supported terms.

Incomes
---------
The following income types are collected and supported:

* Private disability (Disability)
* Investment income (Trust, Interest, or Dividends)
* TANF
* Veterans' benefits
* Unemployment (Unemployment Compensation)
* SSI
* Social Security
* Alimony
* Child Support
* Workers' Compensation
* Pension/401K income [Pension/Retirement (Not Soc. Sec.)]
* Other income (Other)
* Wages/salaries (Employment)
* Self employment (Employment)


Except for unemployment and wages/salary, all income types have a frequency of 12 (monthly). Unemployment has a frequency of 52 (weekly).  Wages have a frequency of 12, 24, 26, or 52 depending on what the user selected.



**Requires:**  API Key for LegalServer instance

**Returns:** Object from Legal Server.  This object contains either an error or the global unique ID.


