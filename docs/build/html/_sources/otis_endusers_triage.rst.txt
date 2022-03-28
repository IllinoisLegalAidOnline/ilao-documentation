========================
Triage
========================

The first piece of Get Legal Help is a triage system designed to route the user to resources. To do this, we ask users to:

* Provide their legal problem. This can be accomplished by picking from our legal issues taxonomy OR typing in a keyword.
* Provide their zip code.
* Indicate whether they are looking for a lawyer, forms, or legal information.
* If the user indicates they are looking for a lawyer:

  * They are required to provide a household size.
  * Once the household size is provided, an income level question will be required. The amount used is an approximation of 300% of the federal poverty level, rounded to the nearest thousand. This is used to determine the initial set of referral resources.
  * The user may indicate if they self-identify as a member of any specific population. The list of populations is maintained in our `intake populations taxonomy <https://www.illinoislegalaid.org/admin/structure/taxonomy/manage/intake_populations/overview>`_.

* The user is required to accept terms & conditions.

.. image::  ../assets/otis-glh-form.png
   :width: 50%
   :alt: Mobile view of Get Legal Help page.

When the user submits the form, the system:

Step 1: Evaluates the term entered by the user. If the term:

  * Is an exact match to lowest level legal issues taxonomy term, the system moves to step 2.
  * Is an exact match to a higher level legal issues taxonomy term, the user is provided a form based on the legal issues; once that has been completed, the system moves to step 2.
  * If neither of these are true, the user is taken to the top of our taxonomy tree to drill down to a lowest level legal issue before continuing to step 2.

Step 2:  Evaluates the type of help; if the user is seeking a lawyer, the system evaluates available resources as follows:

 * Users who have indicated "Yes" to the income questions are directed to referrals unless there is an OTIS organization that is free to everyone service or a service where income limits are waived for specific populations.
 * The system checks for available OTIS partners first (ahead of referrals). This requires looking for:

   * an intake setting with a service area that matches the user's location
   * an intake setting that matches the user's legal issue
   * an intake setting that is published
   * an intake setting that has either no capacity limit or has not yet reached that limit
   * an intake setting that is either available to everyone or matches any selected populations the user identifies with
   * a triage rule that matches the service of the intake setting
   * a triage rule that matches the user's legal issue
   * a triage rule that is published

Step 3a:  When there is 1 or more OTIS matches, the system prioritizes based on:
  * Free to everyone and free to eligible persons services are prioritized ahead of low cost services.
  * Services that match the user's population selections, if the user has selected those.
  * When the last intake was completed. Matches will be ordered by reverse last intake completed date so that organizations that have gone longer will get preferred. If a direct organization parameter was included in the URL, that organization will be prioritized first regardless of last referral.

Step 3b:  When there are no matches, the user is provided referrals.

When a user is diverted from Step 3a and there are multiple organizations, the user will be routed back to the next organization until there are no organizations they could apply to.


.. todo:: We are in the process of implementing Guided Navigation into the website and streamlining triage for legal issues that use Guided Navigation to allow us to eliminate the round robin in 3A and offer the user choices in those legal issues.

Guided Navigation Implementation on Website
==============================================

Initially, we are running a hybrid webform/Guided Navigation solution.

To determine if Guided Navigation should be used over webforms:

* The system checks to see if the Legal Issues taxonomy has a Rest export and Guided Navigation process ID for the term or its first parent.

* If there are no matches, the system defaults to webforms or referrals.



