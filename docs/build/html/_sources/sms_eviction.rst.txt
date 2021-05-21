======================
Eviction SMS Flow
======================

.. note::

  * Eviction SMS is available in both English and Spanish.  The flow is the same for both.
  * In Legal Server, Eviction SMS cases can be identified with ILAOEvict-[triageid]
  * In our OTIS database, Eviction SMS cases can be identified by the last-screen-viewed having an sms prefix or by the referral source (Eviction-English or Eviction-Spanish)


Workflow Tree
=================

Initial message

Overview message
  Option to end => Exits
  Any other response => CONTINUE

First name

Zip code
System:  Get region data for zip code (state, county, county FIPS)

  In Illinois,
    System:  Create initial OTIS user record in OTIS database
    In Cook County, hand to Eviction Help Illinois
    Outside Cook County, CONTINUE

  Not in Illinois, offer to retry Zip
    Link to LawHelp

System:  Get intake settings for organization based on zip code
Get Legal Issue (7 options)

  User replies More
    Show definitions
    Return to legal issue

  User replies 1
    User is asked if they have a summons
      If Yes,

        System: update case notes for etransfer
        CONTINUE to landlord name

      If No, User is asked if they've received written notice
      If neither of these, user is re-asked question

         If yes,

           System: update case notes for etransfer
           CONTINUE to landlord name

         If no, user is asked if the landlord has threatened to evict
         If neither of these, user is re-asked question

           If yes,
             System: update case notes for etransfer
             CONTINUE to landlord name

           If no, EXIT to legal content
           If neither of these, user is re-asked question

     Get landlord name
       System: update case notes for etransfer

     CONTINUE to matches

  User replies 2

     CONTINUE to matches if in LOLLA service area
       System: update case notes for etransfer

     CONTINUE to bypass if in PSLS services area

       System : Save user's data as bypass
       Exit application

  User replies 3
     System: update case notes for etransfer
     CONTINUE to matches

  User replies 4

     User is asked if the utilities were shut off because the tenant didn't pay the bills

        If yes, EXIT to legal content
        If no,

         System: Update case notes for transfer
         CONTINUE to matches

  User replies 5 or 6,

    System: Save user's data
    Show nearest housing counselor
    Option to show all

      Loops through results

    Exits to Legal content


  User replies 7, user gets exit message to Get Legal Help

  User replies More, user sees help text


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

Get last name

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
    Show program's client call message
    Show program's disclaimer
    Show confirmation message

  If callback

    Ask user whether they prefer morning or afternoon callback

      If morning or afternoon, CONTINUE
      If neither, throw error and re-ask

    System: eTransfer case file to Legal Server
    System: user profile data sent to OTIS database
    Show program's we call client message
    Show program's disclaimer
    Show confirmation message

END

