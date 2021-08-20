=====================================
Get Legal Help text line workflow
=====================================

This documents the flow of the OTIS Main flow in Twilio Studio.


.. note::

  * Initial pilot is limited to unemployment, food stamps, and TANF

Prescreening
===============

Initial message

Overview message

  Option to end => Exits
  Any other response => CONTINUE

First name


Zip code

  System:  Get region data for zip code (state, county, county FIPS, city)

  In Illinois,

    System:  Create initial OTIS user record in OTIS database

  Not in Illinois,

   Offer to retry Zip

     If user replies zip, re-ask zip code

     Otherwise, Link to LawHelp


Get Legal Issue (5 options)

  User replies 1 (Unemployment)

  User replies 2 (Food stamps)

  User replies 3 (TANF)

.. note:: In all 3 of the above, the next step is to do an income pre-screen.  For this, the system asks for the number of adults and number of children

   * System: Saves household data to user's profile in OTIS database
   * Throw error if either is not numeric
   * Get the basic income level  approximately 300% of FPL)
   * Ask user if there income is more than this. If they:

     * Reply Yes, they are exited to Get Legal Help
     * Reply No, they continue to Guided Navigation-based triage

  User replies 4 (Eviction)

     Exit to Eviction Help Illinois text line

  User replies 5

     User gets exit message to Get Legal Help

Guided Navigation Triage
==========================

If a user makes it through the pre-screen, the system gets:

* Process ID from Legal Server for the appropriate starting Guided Navigation
* LSC problem code for the selected problem
* Default search term

.. note:: These values are contained in Twilio's Guided Navigation service in the get-process-list function.

The system then loops through the Guided Navigation process as follows:

* Gets the current form from Legal Server
* If the current form has a value false in the "is_complete" field, the form is displayed to the user
* If the current form has a value true in the "is_complete" field, Twilio moves to evaluation.
* Twilio sends the response back to Legal Server


Guided Navigation Evaluation
==============================

The final response from Legal Server's Guided Navigation is an outcome field. This field matches against case acceptance values from webforms on our website. The system then:

* Returns the intake settings id for any matches on the legal problem
* Runs another filter that filters this list on location
* Returns any and all matches.

Matches
=========

* If no matches are found, the user is sent to Get Legal Help
* If 1 match is found, the user is offered the opportunity to apply to that organization
* If multiple organizations are found, the user is offered the opportunity to pick one to continue to apply to.

.. note:: If the user says no, the system saves the user's data to OTIS database and exists the system.

Intake
=========
Get last name

Get maiden names, if any

Get nicknames, if any

Get date of birth
-------------------
Get birth month

  System: Validate birth month based on name/abbreviation or numeric input

  Ask user to retry if invalid

Get birth day

  System: Vaidate birth day as numeric and within the month's allowable range

  Ask user to retry if invalid

Get birth year

  System: Validate birthd year as numeric.  If user provided a 2 digit, assume 19xx if greater than 10.

Ask user to confirm birthdate

  If confirmed,

    System:  Calculate age and save to user's profile in OTIS database

    CONTINIUE

  If not confirmed, go back to birth month

Start demographics
---------------------

Get race

  System:  Validate selection; if invalid, ask to retry

  If race = hispanic/latino, set ethnicity to Hispanic

  Otherwise, Get ethnicity

  Get ethnicity
    System: Validate selection; if invalid, ask to retry

Get gender
  System:  Validate selection; if invalid, ask to retry

Get marital status
   System:  Validate selection; if invalid, ask to retry

Get preferred language
  System:  Validate selection; if invalid, ask to retry

System:  Save demographic data to user's profile in OTIS database

Start income questions
------------------------

Ask wages/salary
  Yes

    Ask frequency

      User replies 1,2,3,4
        Get amount

        Validate and throw error if needed, else CONTINUE

      User replies anything else
        Throw error and allow them to correct

  No
    CONTINUE

  Not sure
    Show help

  Anything else
    Re-ask wages/salary question

Ask farming/self employment
  Yes
    Get amount
      Validate and throw error if needed, else CONTINUE

  No
    CONTINUE

  Anything else
    Show help
    Re-ask farming/self-employment

Ask benefits question (Yes, no, choices)

  Yes

    Ask for choice; then System: Create list of choices to loop through
    CONTINUE

  No

    CONTINUE to other payments

  Numeric choices

    System:  Create list of choices to loop through.
    CONTINUE to For each benefit type selected

  Invalid data

    Show error message
    Re-as question

For each benefit type selected:

  Ask amount
  Validate amount

    Ask user to retry if not numeric

  CONTINUE to next benefit type or when complete, to ask other payment question

Ask other payments question (Yes, no, choices)

  Yes

    Ask for choice; then System: Create list of choices to loop through
    CONTINUE

  No
    CONTINUE to other income

  Numeric choices

    System:  Create list of choices to loop through.
    CONTINUE to For each other payment type selected

  Invalid data

    Show error message
    Re-as question


For each other payment type selected:

  Ask amount
  Validate amount

    Ask user to retry if not numeric

  CONTINUE

Ask if user has other income

  Any response other than no

    Get amount
    Validate amount
    Re ask if invalid
    CONTINUE

  No

    CONTINUE

System: Calculate total income and compare to allowable income based on 80% of AMI.

  If user is over-income

    System: Save total income

    System: Update user profile as overincome to OTIS database

    Inform user we can't complete intake

    Exit to legal information

  If user is not over-income

    System: Save total income

    System: Update user profile with income information

    CONTINUE

Get Contact Information
=========================

Ask if current number is best to reach at

  YES
    CONTINUE

  NO
    Ask for valid number

    Validate number

      Valid => CONTINUE

      Invalid => Repeat

Get email address

Get street address

Get city

Ask user to confirm their contact information

  YES
    CONTINUE

  NO
    Re-ask contact questions starting with phone number

Process contact type
======================

  If client calls

    System: eTransfer case file to Legal Server

    System: user profile data sent to OTIS database

    System: update intake settings current count

    Show program's client call message

    Show program's disclaimer

    Show confirmation message

  If callback

    Ask user if the first available slot will work for them

    If they say no, provide list of days to pick from

    If user picks a day, provide list of available time slots

    If user declines a callback, revert to please call

    System: eTransfer case file to Legal Server

    System: user profile data sent to OTIS database

    System: update intake settings current count

    Show program's we call client message

    Show program's disclaimer

    Show confirmation message

END



