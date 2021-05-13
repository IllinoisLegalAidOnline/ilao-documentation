========================
Online Intake Over SMS
========================

.. note:: The initial version of this was launched in May 2021 for eviction-related issues outside of Cook county. A Spanish version is coming soon.   A version for food stamps and unemployment, part of Smart Triage, is coming by June 30, 2021.

General Architecture
======================

This architecture applies to all of our SMS integrations.

Twilio Studio
--------------

The logical flow for the SMS is managed in Twilio Studio.  Each live version requires two phone numbers and two flows, one for development and one for production.  The production version should not be edited in Twilio studio but should be "deployed" by copying the development version and associating the production phone number with the newly deployed branch.

Twilio Functions
------------------
Twilio functions are used to:

* perform validation that is more complex than the split based on variables widget in Twilio studio

* interact with ILAO's API and other services
* any complex functionality

Twilio functions are stored in the ilao_service and are called using run function widgets in Twilio studio.

ILAO APIs
-----------
Online intake over SMS relies on ILAO's JSONAPI and other APIs for data synchronization.


Other Integrations
-------------------

.. toctree::
   :maxdepth: 2
   :caption: Contents:
   
   otis_sms_functions
   otis_sms_twilio_studio_workflow
   otis_sms_api_calls
   sms_eviction



Required APIs for Intake
===========================

* Zip code validation
* Race list
* Ethnicity list
* Income levels per household size
* Income type entities
* Callback types

Required APIs for Triage
===========================

* Guided navigation integration in phase 1
* Classifier integration in phase 2