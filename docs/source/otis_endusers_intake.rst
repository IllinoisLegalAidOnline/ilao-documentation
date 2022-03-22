============================
Intake
============================

When a user successfully completes a program's triage rules, they are provided the matching organization and may begin intake.

.. todo:: Once Guided Navigation is fully implemented, users will be able to chose where to apply to.

Intake process
================

The intake process generally:


* Collects client information including:

  * Name
  * Alias
  * Nicknames
  * Date of birth
  * Demographics information, based on organization preferences, including:

    * Race
    * Ethnicity
    * Gender
    * Marital Status
    * Preferred language

* Collects household size, broken into number of adults and children. Each organization may have their own definition of who to count.
* Collects income information. Some organizations may:

  * Not collect any income information
  * Waive income limits for some populations

* Contact information, including:

  * Phone type
  * Phone number
  * Opt-in for SMS
  * Email address
  * Address

If the user passes validation (see below):

* If the intake settings is set to "We call you," the user is given a list of appointment times.

  * These times are based on the intake settings, the service maximum limit, and the number of slots already filled.
  * The number of slots the user can pick is limited to the lesser of 3 or the number indicated by the program.
  * The user may opt to call the program instead

* If the intake settings is set to "You call us," the user is given a list of times they can call the program.

.. todo:: Currently this shows the callback slots; we will be replacing this to use Office hours instead.



Validation
============

Most partners have income limits.

* For programs with no income limits, the system will not check income
* For programs that waive income limits for some populations, the system will ignore income limits if the user indicated that they are a member of the population.
* For programs that have applicable income limits:

  * The system pulls the income standard to use and the maximum percentage from the intake settings or location_services.
  * The system pulls the income limits from the relevant Income standard entity.
  * The system calculates the user's monthly income based on the collected income information.
  * The system calculates the user's maximum income based on the income standard and household size
  * The system determines if the user is over income (monthly income exceeds maximum income) or not.

If the user is over-income, the user is diverted to referrals.

If the user is not over-income, they continue to the appointment and confirmation piece.



E-Transfer
============

When the user gets to the final intake confirmation screen, their information is sent to the statewide online intake server.

The e-transfer leverages Legal Server' intake API.

.. code-block:: json

   { "firstName": "Test",
    "middleName": "",
    "lastName": "Test",
    "eTransferOrganization": "Land Of Lincoln Legal Assistance Foundation",
    "aliasFirst": "",
    "aliasLast": "",
    "addressHome": {
        "address1": "120 Main Street ",
        "city": "Belleville",
        "state": "IL",
        "zip": "62220",
        "county": "17163"
    },
    "phoneHome": "315555555",
    "phoneHomeNote": "",
    "dateOfBirth": "1989-11-17",
    "email": "test@gmail.com ",
    "maritalStatus": "Separated",
    "race": "Other",
    "ethnicity": "",
    "gender": "Female",
    "language": "en",
    "citizenshipStatus": "",
    "immigrationStatus": "",
    "veteran": "",
    "disabled": "",
    "note": "Select the one that best fits your case:I want a divorce because I am being abused by my spouse. Or I want a divorce because my kids are being abused or in danger.; Do you have a safe phone number we can call you at?:Yes;; We call client; Callback Times:Wednesday, Jun 30, 2021, 12:00pm - 1:00pm;",
    "numberOfAdults": "1",
    "numberOfChildren": "1",
    "callbackType": "Callback",
    "callbackDayTime": "Callback Times:Wednesday, Jun 30, 2021, 12:00pm - 1:00pm",
    "externalID": "ILAOWeb-35825811",
    "incomes": [{"amount":"1100","frequency":12, "type":"Employment"}],
    "adverse_parties": {},
    "program": "",
    "customField": {},
    "jsonPayloadItem": {},
    "legalProblemCode": "32 Divorce/ Separation/ Annulment"
    }

.. note:: In 2022 - 2023, we will begin to leverage the program, adverse_parties, customField, and jsonPayloadItem fields.


