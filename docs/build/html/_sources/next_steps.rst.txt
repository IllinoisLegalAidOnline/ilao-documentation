=======================
NextSteps Flows
=======================

"NextSteps" is designed to provide additional support to individuals along their legal journey. In phase 1, we are focusing on making the tool available to caseworkers at OTIS partner organizations to subscribe clients to these next steps. As they provide advice, they can use a component in LegalServer to assign a client to a completed step and subscribe them to follow up messages.

Phase 2 envisions expanding it to website visitors and users of our ILAOHelps! SMS text line and an expansion to web notifications and email processing.

Next Steps build on the work done with COPE content to define step-by-step legal processes (How-tos) associated with a specific DIY Legal Solution and its options. This adds a content type designed to deliver interactive follow-up messages initially over SMS.

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   next_steps_content_type
   next_steps_entity_type
   next_steps_signup_form
   next_steps_sms_delivery
   next_steps_tracking


Interim Process
====================

Because the NextSteps Flows were designed to work with the Legal How-to that we are revising and have paused, these are the interim steps for creating a Next Step flow:

* Find the best Legal Content of type "How-to" to use as the primary source of legal information.
* Create a legal step for each process step in the How-to. For this you need to:

  * Enter the step title; this should align with the process step title.
  * Add a disambiguation tag for the specific legal issue to tell different steps apart.
  * Remove the Step information
  * Tag to Illinois
  * Remove the Negate jurisdiction field
  * Ignore all other fields
  * Leave unpublished


* Create a legal how-to to act as a dummy how-to. for this you need to:

  * Create a title; this title should match or be similar to the Legal content how-to
  * Add a content description and meta description
  * Tag to a legal category, primary legal category, and navigation term
  * Set legal position
  * Add steps
  * Set to "unpublished"


* Create the next step flow. Because the legal steps contain no information, we can not include steps in the "Include" fields.

Follow the information on creating a next step flows to create the actual flow.


