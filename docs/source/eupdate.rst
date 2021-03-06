=======================
Automated eUpdate
=======================

The automated eUpdate compiles information from the website into a Mailchimp template that is then sent to targeted groups.

Who Gets the eUpdate
=======================

Any registered user of IllinoisLegalAid.org can get the eUpdate.  When creating an account:

* Legal aid members default newsletter settings to select the eUpdate every Tuesday morning
* All others membership types default newsletter settings to select the eUpdate every month.

.. note:: Users may unselect the defaults before saving their account.

What is in the eUpdate
===========================
The weekly version includes content from the current date minus 7 days
The monthly version includes content from the current date minus 30 days


The content includes:

* Legal content, portal main pages, tools, toolboxes, and ADRM content that has a last revised date within the selected timeframe
* The next 3 upcoming calendar events
* The 3 most recently updated published job postings

Sending
===========
The eUpdate is scheduled to send at:

* 9am Tuesdays for weekly subscribers.
* 9am on the 1st of the month for weekly subscribers.

Because the scheduled task system runs once per hour, it may be delayed and run anytime between 9am and 10am.

Tracking
==========
Links within the eUpdate are tracked using:

* campaign = date the eUpdate is sent
* source = eUpdate
* medium = email

These can be tracked in Google Analytics.  Mailchimp also tracks data.


Testing
===========
There is a check group in the master segment that is made up of Gwen and various members of the QED42 team.  This is the default send-to on all non-production instances to prevent accidentally sending from these machines to all users.

.. note:: Mailchimp campaigns sent to the check group may be safely deleted from Mailchimp.


Technical Integration
=======================
The mailchimp block that appears on the user registration/profile page is tied to the Master list within Mailchimp. When a user creates an account on the website:

* They are added to the master list
* They are added to the segment that matches their role
* If they sign up for specific communications, they are added to groups within website communications:

  * if they sign up for the monthly newsletter, they are added to the Newsletter segment
  * if they sign up for the weekly eUpdate, they are added to the weekly eUpdate segment
  * if they sign up for the monthly eupdate, they are added to the monthly eUpdate segment
  * if they sign up for the blog alerts, they are added to the blog segment
  
.. note:: There are also signup forms for anonymous users for the newsletter and the blog alerts.


.. todo:: Need to verify that editing my profile to unsubscribe in website in fact changes my settings in Mailchimp.


  




