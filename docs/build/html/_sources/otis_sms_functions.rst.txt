=====================
Twilio Functions
=====================

This documents the functions stored in our Twilio function service "ilao."

All of our Twilio functions are stored in the ilao service in Twilio's functions.

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

Eviction intake settings
==========================
**Function name:**  eviction-intake-settings

**Parameters:**  event.flow_id which is the phone number associated with an executed flow.  This is used to direct requests to production or staging based on a phone number.

**Returns:** An object containing:

* id, the uuid for the intake settings
* callback_number
* node_id, the intake settings ID for the custom entity
* callback_type
* bypass, the bypass message
* disclaimer
* please_call, the please call message
* we_call, the we call the client message
* legalservername, the name specifically required by Legal Server for etransfer
* organization, the organization name from our website to display to the user


**Requires:**  Access to the :ref:`ilao-api` for intake settings.

Eviction legal issues
======================
**Function name:**  eviction-legal-issues

**Parameters:**  event.choice which is the number of the legal issue identified in the eviction studio flow.

**Returns:** An object containing:

* issue (which is the name of the issue)
* issue_id, which is the UUID of the associated legal issues taxonomy term.
* notes, which is a sentence to include in the notes on an etransfer.

**Requires:**  This is hand-coded but future iterations may use the taxonomy piece of the :ref:`ilao-api`.

Eviction content
==================
**Function name:**  eviction-content

**Parameters:**  event.legal_issue, which is an integer representing the user's selected legal issue.

**Returns:** A string which includes the titles and links of relevant content to return.

**Requires:**  This is hand-coded but future iterations may use the :ref:`ilao-api`.

.. note:: This function will be updated to accommodate language codes.

HUD housing counselors
========================

**Function name:**  hud-housing-counselors

**Parameters:**  event.zip, which is the zip code of the user.

**Returns:** An object containing:

* An array of options.  Each option contains:

  * name
  * address
  * city
  * phone
  * weburl
  * methods (counseling methods)
  * services (services offered)

* A total, which is a number reflecting the total number of options.

**Requires:**  Access to the JSON files containing housing data: https://files.consumerfinance.gov/a/assets/hud/jsons/[zipcode].json

.. note:: This function should be updated to return Spanish results when appropriate.

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

OTIS Validate Total Income
===============================

**Function name:**  otis-get-callback-times

**Parameters:**

+------------------------+---------------------------------------------------+
|   Key                  | Description                                       |
+========================+===================================================+
|  adults                | Required. Integer.                                |
+------------------------+---------------------------------------------------+
|  children              | Required. Integer.                                |
+------------------------+---------------------------------------------------+
|  Income types          | Key should be named income_[income type]. Value   |
|                        | should be integer                                 |
+------------------------+---------------------------------------------------+
|  standard              | Basic, ami, or fpl. Defaults to fpl if not        |
|                        | provided.                                         |
+------------------------+---------------------------------------------------+
|  max                   | Percentage max income to calculate. Number.       |
|                        | Defaults to 300 if not provided                   |
+------------------------+---------------------------------------------------+

**Requires:**  Income Limits asset

**Returns** An object with values for

+------------------------+---------------------------------------------------+
|   Key                  | Description                                       |
+========================+===================================================+
|  income                | Integer; total income                             |
+------------------------+---------------------------------------------------+
|  incomeFlag            | 0 if not over-income; 1 if over-income.           |
+------------------------+---------------------------------------------------+
|  maxIncome             | Calculated maximum income                         |
+------------------------+---------------------------------------------------+

.. note:: Unemployment benefits are computed at the passed value times 4.3 to convert weekly to monthly for calculating income.

**Status:**  Complete


OTIS Validate Payments
=========================

**Function name:**  otis-validate-payments

**Purpose**: Takes a string of input from the user and returns an array of numbers that represent which types of payments we need to collect income information for.

**Parameters:**  event.payments (the user's input to the do you have any of these payments question)

**Requires:**  Nothing

**Returns:** An array of payment types to ask for income information from the user.

**Status:**  Complete.

OTIS Validate Benefit Types
===============================

**Function name:**  otis-validate-payments

**Purpose**: Takes a string of input from the user and returns an array of numbers that represent which types of benefits we need to collect income information for.

**Parameters:**  event.payments (the user's input to the do you have any of these benefits question)

**Requires:**  Nothing

**Returns:** An array of benefit types to ask for income information from the user. These are numerical values of 1-5 that are used to route the user through income questions.


OTIS Validate Benefit Types
===============================

**Function name:**  otis-validate-payments

**Purpose**: Takes a string of input from the user and returns an array of numbers that represent which types of benefits we need to collect income information for.

**Parameters:**  event.payments (the user's input to the do you have any of these benefits question)

**Requires:**  Nothing

**Returns:** An array of benefit types to ask for income information from the user.

**Status:**  Complete.

OTIS Validate Money Input
============================
**Function name:**  otis-validate-money-input

**Purpose**: Takes a string of input from the user and returns the string if it is a number or 0 if it is not. This can then be used to route users to retry their input or move on to the next step.

**Parameters:**  event.amount (the user's input in response to a money question)

**Requires:**  Nothing

**Returns:** A number. -1 is returned if it is not a valid amount.

**Status:**  Should be updated to accommodate for dollar formatting ($,. within the data).

OTIS Validate Race
============================
**Function name:**  otis-validate-race

**Purpose**: Takes a string of input from the user and returns whether it is a valid selection or not. This can then be used to route users to retry their input or move on to the next step.

**Parameters:**  event.race (the user's input)

**Requires:**  Nothing; values are stored in the function as an array

**Returns:** A string, either the name of the race the user selected OR 0 if it is invalid.


OTIS Validate Ethnicity
============================
**Function name:**  otis-validate-ethnicity

**Purpose**: Takes a string of input from the user and returns whether it is a valid selection or not. This can then be used to route users to retry their input or move on to the next step.

**Parameters:**  event.ethnicity (the user's input)

**Requires:**  Nothing; values are stored in the function as an array

**Returns:** A string, either the name of the race the user selected OR -1 if it is invalid.

OTIS Validate Gender
======================

**Function name:**  otis-validate-gender

**Purpose**: Takes a string of input from the user and returns whether it is a valid selection or not. This can then be used to route users to retry their input or move on to the next step.  The returned strings align with Legal Server's supported genders.

**Parameters:**  event.gender (the user's input)

**Requires:**  Nothing; values are stored in the function as an array

**Returns:** A string, either the name of the gender the user selected OR -1 if it is invalid.

OTIS Validate Marital Status
===============================

**Function name:**  otis-validate-marital-status

**Purpose**: Takes a string of input from the user and returns whether it is a valid selection or not. This can then be used to route users to retry their input or move on to the next step.  The returned strings align with Legal Server's supported marital statuses.

**Parameters:**  event.maritalStatus (the user's input)

**Requires:**  Nothing; values are stored in the function as an array

**Returns:** A string, either the name of the marital status the user selected OR -1 if it is invalid.

OTIS Validate Preferred Language
==================================

**Function name:**  otis-validate-preferred-language

**Purpose**: Takes a string of input from the user and returns whether it is a valid selection or not. This can then be used to route users to retry their input or move on to the next step.  The returned strings align with Legal Server's supported languages.

**Parameters:**  event.language (the user's input)

**Requires:**  Nothing; values are stored in the function as an array

**Returns:** A string, either the name of the language the user selected OR -1 if it is invalid.

OTIS Validate Year
======================
**Function name:**  otis-validate-year

**Purpose**: Takes a string of input from the user and returns whether it is a valid year. This can then be used to route users to retry their input or move on to the next step.

If the user enters a 2 digit year, it is assumed to be 19xx if the string is greater than 10.

**Parameters:**  event.year (the user's input)

**Requires:** none

**Returns:** A number (either the 4 digit year or a 0 representing invalid data)

.. note:: Would be nice to not allow future years to be included.

OTIS Validate Day of Month
===============================
**Function name:**  otis-validate-day-of-month

**Purpose**: Takes a string of input from the user and returns whether it is a valid number between 1 and 31 for  months with 31 days 1 and 30 for days with 30 days, and between 1 - 29 days for February. This can then be used to route users to retry their input or move on to the next step.

**Parameters:**  event.day (the user's input), event.month (the user's previous input for the month)

**Requires:**  none

**Returns:** A number (either the day or a 0 representing invalid data)


OTIS Validate Month
===============================
**Function name:**  otis-validate-month

**Purpose**: Takes a string of input from the user and returns whether it is a valid month. This validates both numbers (1 - 12) and text input such as November, november, nov, or Nov. This can then be used to route users to retry their input or move on to the next step.

**Parameters:**  event.month (the user's input)

**Requires:**  none

**Returns:** A number (either the day or a 0 representing invalid data)


OTIS Calculate Age
===================

**Function name:**  otis-calculate-age

**Purpose**: Calculates an age based on a date of birth.

**Parameters:**  event.day, event.month, and event.year (provided by the user)

**Requires:**  none

**Returns:** A number


OTIS Poverty Estimate
=======================

**Function name:**  otis-poverty-estimate

**Purpose**: Gets the estimated over-income threshold for users based on household size.

**Parameters:**  event.children and event.adult. Both should be numbers.

**Requires:**  API call to get poverty income.

**Returns:** An object containing:

* income, which represents the total income
* household_size, which represents the number of adults and children in the household

.. note:: This is the function to determine whether a user passes the initial basic income screening similar to what appears on IllinoisLegalAid.org/get-legal-help.

OTIS validate total income
============================

**Function name:**  otis-validate-total-income

**Purpose**: Gets the estimated over-income threshold for users based on household size.

**Parameters:**

* event.children and event.adult. Both should be numbers.
* event.standard which is the income standard to use.  This defaults to the federal poverty level.
* event.max which is the maximum income percentage to use.  This defaults to 300.
* Wage frequency, which is the wage frequency

**Requires:**  API call to get poverty income.

**Returns:** An object containing:

* income, which is the total monthly income
* incomeFlag, which is 0 or 1.  1 represents overincome
* maxIncome, which is the calculated maximum income based on the selected standard and allowable percentage.

.. note:: This is the function to determine whether a user passes the income screening for a specific organization.

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

Create Triage User
==========================
**Function name:**  otis-create-triage-user

**Purpose**: Builds a data packet and leverages ILAO's Rest API to create a triage user record on ILAO's website.  This executes after we have validated the user's zip code.

**Parameters:**  Event object that contains base data; empty or missing values are set to null. Base data includes:


* referral_source, varies by application
* zip_code, user's provided zip code
* user_phone, phone number the user texted from
* county, the county associated with the zip code
* search, the incoming message texted by the user
* flow_id, the phone number the user texted to
* last_screen_viewed, set to sms-zip-code
* oas_triage_problem

These are hard-coded within the function:

* household_size, set to 1
* triage_status, set to Started
* oas_triage_problem uuid

.. note:: For eviction, the source is either eviction-spanish or eviction-english

**Requires:**  Authentication with ILAO's API

**Returns:** An object containing:

* id, which is the uuid associated with the newly created user.
* triage_id, which is the internal Drupal ID associated with the entity.


OTIS Update Triage User
==========================
**Function name:**  otis-update-triage-user

**Purpose**: Updates a triage user record on ILAO's website based on interactions with the SMS intake system.

**Parameters:**  Event object with data to update; UUID of existing triage user.

**Requires:**  Authentication with ILAO's REST OTIS API

**Returns:** Updated data packet

**Status:** Data packet based on event object generates; API integration not built.

Within Eviction SMS applications
---------------------------------

This function is called when:

* the user declines to proceed to intake

  * last screen viewed = sms-match-offered
  * intake_status = Offered
  * triage status = Program triage completed

* when the user chooses to proceed to intake

  * last screen viewed = sms-match-offered
  * intake_status = Started
  * triage status = Program triage completed
  * intake_organization = UUID of the intake settings associated with the intake
  * triage_problem = UUID of the determined legal issue from ILAO's legal issue taxonomy (in eviction, this is the eviction term).

* when the user has provided household size information

  * last screen viewed =  sms_household_size
  * event object contains household total, number of adults, and number of children

* after we have collected the date of birth and calculated the user's age

  * last_screen_viewed = sms_date_of_birth
  * event object contains age

* after preferred language is set and all demographics data has been collected

  * last_screen_viwed = sms_demographics
  * event object contains demographic data

* after all income has been collected and we've calculated total income and whether the user is over-income

* when the user reaches an endpoint (etransferred, bypassed, exited to content)

  * if the user is diverted,  intake status is set to Diverted and last screen viewed is set to sms_legal_issue_selector
  * if the user is etransferred, intake status is set to etransferred and last_screen_viewed is set to sms-confirmation
  * if the user in Cook County, last screen viewed is set to cook-county-exit
  * if the user is given counseling resources instead of intake, last screen viewed is set to sms-counselors-list
  * if the user has an unsupported legal issue, triage_status is set to Legal Issue and last screen viewed is set to sms-legal-issues






Get Matches
==========================

**Function name:**  otis-get-matches

**Purpose**:

**Parameters:**

**Requires:**

**Returns:**

**Status:** Not built

Load marital statuses
==========================
**Function name:**  otis-load-marital-statuses

**Purpose**: Returns list of marital statuses for user to select from.

**Parameters:** event.langcode (may be null)

**Requires:**  None

**Returns:** A string of marital statuses for display based on the language code provided.


Load languages
==========================
**Function name:**  otis-load-languages

**Purpose**: Returns list of languages for user to select from.

**Parameters:** event.langcode (may be null)

**Requires:**  None

**Returns:** A string of languages for display based on the language code provided.

Load genders
==========================
**Function name:**  otis-load-genders

**Purpose**: Returns list of genders for user to select from.

**Parameters:** event.langcode (may be null)

**Requires:**  None

**Returns:** A string of genders for display based on the language code provided.


Load ethnicities
==========================
**Function name:**  otis-load-ethnicity

**Purpose**: Returns list of ethnicity options for user to select from.

**Parameters:** event.langcode (may be null)

**Requires:**  None

**Returns:** A string of ethnicities for display based on the language code provided.


Load races
==========================
**Function name:**  otis-load-races

**Purpose**: Returns list of races for user to select from.

**Parameters:** event.langcode (may be null)

**Requires:**  None

**Returns:** A string of races for display based on the language code provided.


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


