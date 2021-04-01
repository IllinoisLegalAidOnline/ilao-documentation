=====================
OTIS SMS Functions
=====================

This documents the functions stored in our Twilio function service "ilao."

All of our Twilio functions are stored in the ilao service in Twilio's functions.

Function standards
======================
All of our OTIS functions are prefixed with the name otis.  All function names are written in the word-word-word format.

All passed in parameters are contained in the event object.

OTIS Get Confirmation
======================

**Function name:**  otis-get-confirmation

**Parameters:**  event.intakeSettingsId and event.callbackType

**Requires:**  ILAO API call to get the return message based on the intake settings id and callback type.

**Status:**  This is a placeholder function right now.  It returns either the "we call" or "you call" message" as a JSON object.

OTIS Get Callback Days
========================

**Function name:**  otis-get-callback-days

**Parameters:**  event.intakeSettingsId 

**Requires:**  ILAO API call to get the next [x] days of available intake appointments.

**Status:**  This is a placeholder function right now. It returns a JSON object of days for the user to pick from.  Currently, it is using an array of days and a string of days to output.  This needs to be revised to return a key value pair that can be rendered while still having useful info for the system.

OTIS Get First Callback Time
===============================

**Function name:**  otis-get-first-callback-time

**Parameters:**  event.intakeSettingsId 

**Requires:**  ILAO API call to get the range of available hours and the first available date.

**Status:**  This is a placeholder function right now. It returns a JSON object of days for the user to pick from.  It currently returns hard-coded text of:

* intro ('Callback times are between x and y');
* first ('The first available is [x]);
* callback-date: Stores the actual date in mm/dd/yyyy format.

OTIS Get Callback Times
===============================

**Function name:**  otis-get-callback-times

**Parameters:**  event.intakeSettingsId, event.callbackDate

**Requires:**  ILAO API call to get the range of callback slots for a specific date and intake settings pairing.

**Status:**  This is a placeholder function right now. It returns a JSON object of times for the user to pick from.  It currently returns hard-coded text of:

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
|  adults                | Required.  Integer.                               |
+------------------------+---------------------------------------------------+
|  children              | Required.  Integer.                               |
+------------------------+---------------------------------------------------+
|  Income types          | Key should be named income_[income type].  Value  |
|                        | should be integer                                 |
+------------------------+---------------------------------------------------+
|  standard              | Basic, ami, or fpl.  Defaults to fpl if not       |
|                        | provided.                                         |
+------------------------+---------------------------------------------------+
|  max                   | Percentage max income to calculate.  Number.      |
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

**Returns:** An array of benefit types to ask for income information from the user.

**Status:**  Complete. 

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

**Purpose**: Takes a string of input from the user and returns the string if it is a number or 0 if it is not.  This can then be used to route users to retry their input or move on to the next step.

**Parameters:**  event.amount (the user's input in response to a money question)

**Requires:**  Nothing

**Returns:** A number.

**Status:**  Should be updated to accommodate for dollar formatting ($,. within the data).

OTIS Validate Race
============================
**Function name:**  otis-validate-race

**Purpose**: Takes a string of input from the user and returns whether it is a valid selection or not.  This can then be used to route users to retry their input or move on to the next step.

**Parameters:**  event.race (the user's input)

**Requires:**  TBD (should validate against supported race selections)

**Returns:** A number.

**Status:**  Currently does not support text processing, only numeric entries.

OTIS Validate Ethnicity
============================
**Function name:**  otis-validate-ethnicity

**Purpose**: Takes a string of input from the user and returns whether it is a valid selection or not.  This can then be used to route users to retry their input or move on to the next step.

**Parameters:**  event.ethnicity (the user's input)

**Requires:**  TBD (should validate against supported ethnicity selections)

**Returns:** A number.

**Status:**  Currently does not support text processing, only numeric entries.

OTIS Validate Year
======================
**Function name:**  otis-validate-year

**Purpose**: Takes a string of input from the user and returns whether it is a valid year.  This can then be used to route users to retry their input or move on to the next step.

If the user enters a 2 digit year, it is assumed to be 19xx if the string is greater than 10.

**Parameters:**  event.year (the user's input)

**Requires:** none

**Returns:** A number (either the 4 digit year or a 0 representing invalid data)

**Status:**  Complete

OTIS Validate Day of Month
===============================
**Function name:**  otis-validate-day-of-month

**Purpose**: Takes a string of input from the user and returns whether it is a valid number between 1 and 31.  This can then be used to route users to retry their input or move on to the next step.

**Parameters:**  event.day (the user's input)

**Requires:**  none

**Returns:** A number (either the day or a 0 representing invalid data)

**Status:**  Support for per-month validation would be nice.

OTIS Validate Month
===============================
**Function name:**  otis-validate-day-of-month

**Purpose**: Takes a string of input from the user and returns whether it is a valid month.  This validates both numbers (1 - 12) and text input such as November, november, nov, or Nov.  This can then be used to route users to retry their input or move on to the next step.

**Parameters:**  event.day (the user's input)

**Requires:**  none

**Returns:** A number (either the day or a 0 representing invalid data)

**Status:**  Support for per-month validation would be nice.

OTIS Name Processor
======================

OTIS Poverty Estimate
=======================

**Function name:**  otis-poverty-estimate

**Purpose**: Gets the estimated over-income threshold for users based on household size.

**Parameters:**  event.children and event.adult.  Both should be numbers.

**Requires:**  API call to get poverty income.

**Returns:** A number representing the maximum income to continue.

**Status:**  Support for per-month validation would be nice.


OTIS Zipcode Validate
=======================

**Function name:**  otis-poverty-estimate

**Purpose**: Determines whether a provided zip code is in Illinois or not

**Parameters:**  event.zip

**Requires:**  API call to get region information based on zip code.

**Returns:** A string representing the state.

**Status:** Relies on a JSON object in our static assets (/illinois-regions) that contains the IL regional taxonomy data.

Create Triage User
==========================
**Function name:**  otis-create-triage-user

**Purpose**: Builds a data packet and leverages ILAO's Rest API to create a triage user record on ILAO's website

**Parameters:**  Event object that contains base data; empty or missing values are set to null.  

**Requires:**  Authentication with ILAO's REST OTIS API

**Returns:** UUID representing the triage user.

**Status:** Data packet generates; API integration not built.

OTIS Update Triage User
==========================
**Function name:**  otis-update-triage-user

**Purpose**: Updates a triage user record on ILAO's website based on interactions with the SMS intake system.

**Parameters:**  Event object with data to update; UUID of existing triage user.

**Requires:**  Authentication with ILAO's REST OTIS API

**Returns:** Updated data packet

**Status:** Data packet based on event object generates; API integration not built.

Get Matches
==========================

**Function name:**  otis-get-matches

**Purpose**: 

**Parameters:**  

**Requires:**  

**Returns:** 

**Status:** 

Load marital statuses
==========================
**Function name:**  otis-load-marital-statuses

**Purpose**: Returns list of marital statuses for user to select from. 

**Parameters:** event.langcode (may be null)

**Requires:**  None

**Returns:** A string of marital statuses for display

**Status:** Built for English. Separate array for Spanish exists for translation and will be returned when the langcode = es.

Load languages
==========================
**Function name:**  otis-load-languages

**Purpose**: Returns list of languages for user to select from. 

**Parameters:** event.langcode (may be null)

**Requires:**  None

**Returns:** A string of languages for display

**Status:** Built for English. Separate array for Spanish exists for translation and will be returned when the langcode = es.

Load genders
==========================
**Function name:**  otis-load-genders

**Purpose**: Returns list of genders for user to select from. 

**Parameters:** event.langcode (may be null)

**Requires:**  None

**Returns:** A string of genders for display

**Status:** Built for English. Separate array for Spanish exists for translation and will be returned when the langcode = es.

Load ethnicities
==========================
**Function name:**  otis-load-ethnicity

**Purpose**: Returns list of ethnicity options for user to select from. 

**Parameters:** event.langcode (may be null)

**Requires:**  None

**Returns:** A string of ethnicities for display

**Status:** Built for English. Separate array for Spanish exists for translation and will be returned when the langcode = es.

Load races
==========================
**Function name:**  otis-load-races

**Purpose**: Returns list of races for user to select from. 

**Parameters:** event.langcode (may be null)

**Requires:**  None

**Returns:** A string of races for display

**Status:** Built for English. Separate array for Spanish exists for translation and will be returned when the langcode = es.
