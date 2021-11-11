=====================
Presentation surveys
=====================

All community engagement surveys are hosted on JotForm.

.. warning:: Due to access restrictions, the associated spreadsheet integrations can not live in team drive. They are shared as needed with staff. These spreadsheets are:

* Community Navigator Followup Surveys
* CN Presentation Initial Survey Responses

Initial survey
=================
We use a single survey for capturing initial feedback. This survey is named "CN Presentation Initial Survey" in JotForm.


This survey captures:

* the presentation attended
* the user's knowledge before/after presentation
* presentation information feedback
* presenter rating
* recommend or not (Net Promoter Score)
* confidence level explaining rights
* confidence level practicing rights
* how presentation could be better
* cell phone
* presenter or navigator


When sent over SMS
------------------------

* we ask the user to text the presenter's name. This is stored in the presenter field, which is not visible in the form.

When sent from a web-based/tablet presentation:

* we provide a url at the end of the presentation. This includes a src=video that causes additional questions to be asked.
* presenter will be set to video and not visible
* zip code question will appear and be required
* name or initials will appear and be required
* name of navigator will appear and be required
* cell phone or email must be required

.. todo:: The web-based/tablet fields need to be added.

When submitted
-----------------

The submission date, presentation, and cell phone number will be automatically copied to a Google sheet on ILAO's team drive. A follow up date field will show the date 4 weeks from the submission date. This date can then be used to send out follow-up surveys.

.. note::
   * If a user checks multiple presentations attended, we need to manually copy the row and separate the presentations.
   * We will need to copy and paste the follow up date field to new rows.


Followup surveys
====================

We have a separate follow up survey for each presentation. These surveys are named "CN [presentation name] Follow-up Survey"

These surveys capture:

* the user’s current knowledge of rights learned in presentation
* did user recommend presentation - yes/no/why/why not
* did user explain rights to anyone - yes/no/why/why not
* used magic words learned in presentation - yes/no/why/why not
* referred anyone to Illinois Legal Aid Online - yes/no/why/why not
* any information missing from the presentation

.. note:: A hidden src (source) field is stored to track which presentation was watched [may not need this]


Setting up a new followup survey
----------------------------------
To set up a new followup survey for new presentations:

* Copy an existing followup survey
* Update the survey with presentation-specific questions
* Create a new short.io link for the survey:

  * Log into short.io
  * Create a new link with a url of go.illinoislegalaid.org/kyr-[source]
  * Update the followup survey spreadsheet (Community Navigator Followup Surveys) to include the source in the source sheet


Sending out followup surveys
------------------------------

We use Twilio's REST-based API and Zapier to send the correct survey to the right people where we have an opt-ed in SMS number

To send followup surveys:

* Check the intial survey response spreadsheet for any responses that are 4 weeks old and have cell phone numbers
* Copy each cell phone number into the followup survey spreadsheet in the raw phone field, stripped of all characters except numbers
* Add the source to the followup survey spreadsheet
* Save the row
* This will trigger Zapier within 10 minutes to send the phone number and source via API to Twilio to send the survey

.. warning:: There is a limit to the number of requests Zapier will handle at once. Add the data in batches no larger than 50 rows and wait about 30 minutes between batches.


How the SMS flow works
=========================

All surveys are contained in the A2J Survey Studio Flow.

Incoming texts
------------------

When an incoming text is received, it responds with a link to the short.io link go.illinoislegalaid.org/kyr that links to our survey. It passes the incoming text message as the presenter parameter.

Incoming API requests
-----------------------
When an incoming API request is received, it responds with a link to the short.io link go.illinoislegalaid.org/kyr-[source] where source is included in the API request and should represent the survey to send.

For example, source = 'police' should send the police encounter follow up survey.


Translations
=============

At this time, the surveys are English only.

.. todo:: Add Spanish translations and update Twilio, Zapier to send correct language.




