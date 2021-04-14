========================
SMS Integration
========================

.. note:: This is not built but documentation to guide the build. This will be built out using Twilio Studio and ILAO API calls.

The English Twilio Studio flow is the OTIS master.

See `conceptual prototype <https://kywpl3.axshare.com/#g=1&p=home>`_.

The interface, including text segments, are stored in Twilio. API calls to required data sets are on the website and processed using functions in Twilio Studio.

Phase 1
==========

Phase 1 is a basic model that requires the user to choose from a limited set of legal problems. All other issues will be routed to the website.

Only legal issues offered over Guided Navigation can be triaged over SMS in our pilot and the initial rollout will be limited to:

* unemployment benefits
* food stamps and TANF

Phase 2
========
Phase 2 will add support for classifiers to support plain language triage

Phase 3
=========
Phase 3 will add support for legal issues beyond those in Phase 1


.. toctree::
   :maxdepth: 2
   :caption: Contents:

   otis_sms_functions
   otis_sms_twilio_studio_workflow
   otis_sms_api_calls
   sms_eviction


Functions
-------------
Available functions are in the ilao service. Twilio studio can pass parameters to functions. These are stored in the event object.



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