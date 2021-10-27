=====================
Presentation surveys
=====================

All community engagement surveys are hosted on JotForm.

Initial survey
=================
We use a single survey for capturing initial feedback. This survey captures:

* the survey attended
* the user's knowledge before/after
* presentation feedback
* recommend or not (Net Promoter Score)
* confidence level
* cell phone or email
* presenter or navigator



When sent over SMS:

* we ask the user to text the presenter's name. This is stored in the presenter field, which is not visible in the form.

When sent from a web-based/tablet presentation:

* we provide a url at the end of the presentation. This includes a src=video that causes additional questions to be asked.
* presenter will be set to video and not visible
* zip code question will appear and be required
* name or initials will appear and be required
* name of navigator will appear and be required


Followup surveys
====================

We have a separate follow up survey for each presentation.

.. todo:: Add field data

When sent over SMS:

* we use a REST-based API and Zapier to send the correct survey to the right people where we have an opt-ed in SMS number
* In the Google sheet used to send the data, the source column should be the presentation name's shorthand that then will map to the correct survey.

In any other medium:

* we will provide the correct url



