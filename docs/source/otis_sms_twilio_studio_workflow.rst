=====================================
Get Legal Help text line  Workflow
=====================================

This documents the flow of the OTIS Master flow in Twilio Studio.


.. note::

  * Future enhancement will include scheduling a callback slot
  * Initial pilot is limited to unemployment, food stamps, and TANF
  * Future build out should include referral

Workflow Tree
=================

Initial message

Overview message

  Option to end => Exits
  Any other response => CONTINUE

First name

Last name

Zip code

  System:  Get region data for zip code (state, county, county FIPS)

  In Illinois,

    System:  Create initial OTIS user record in OTIS database

  Not in Illinois,

   Offer to retry Zip

     If user replies zip, re-ask zip code

     Otherwise, Link to LawHelp


Get Legal Issue (7 options)

  User replies More

    Show definitions

    Return to legal issue

  User replies 1 (Unemployment)

     Runs Guided Navigation

     CONTINUE to matches

  User replies 2 (Food stamps)

     Runs Guided Navigation

     CONTINUE to matches

  User replies 3 (TANF)

     Runs Guided Navigation

     CONTINUE to matches

  User replies 4 (Eviction)

     Exit to Eviction Help Illinois text line

  User replies 5

     User gets exit message to Get Legal Help

System runs matches code based on:

  * legal issue/guided navigation results
  * first name and last name
  * zip code

.. note::  If there are no matches, provide legal information and referrals.

Matches: Ask user if they want to continue to apply to the organizations

  User says no

    System: Save user data to OTIS database

    Exits to Legal content

  Users says yes CONTINUE

Household prompt

  Household adult

  Household children

  System: Saves household data to user's profile in OTIS database

    Throw error if either is not numeric

Get maiden names, if any

Get nicknames, if any

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

Income prompt

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

System:  Check program contact type.

  If client calls

    System: eTransfer case file to Legal Server

    System: user profile data sent to OTIS database

    System: update intake settings current count

    Show program's client call message

    Show program's disclaimer

    Show confirmation message

  If callback

    Ask user whether they prefer morning or afternoon callback

      If morning or afternoon, CONTINUE

      If neither, throw error and re-ask

    System: eTransfer case file to Legal Server

    System: user profile data sent to OTIS database

    System: update intake settings current count

    Show program's we call client message

    Show program's disclaimer

    Show confirmation message

END



