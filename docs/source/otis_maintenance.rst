====================================
Maintaining and expanding OTIS SMS
====================================

Expanding for new legal issues
=====================================

To add a new legal issue to OTIS-based Guided Navigation over SMS:

* Create the Guided Navigation in LegalServer
* Create the case acceptance webform using the outcome fields used in the Guided Navigation
* Update the Case acceptance view to include the new legal issue
* In Twilio:

  * Update the gn-outcome-list asset in the guided-nav service.  For best results, delete all the existing data and copy and paste the REST export for every Rest export in the website view.

  * Save and deploy the asset.

  * In the OTIS flow:

    * Step 1: Add a number and label for the legal issue.

    .. image:: ../assets/twilio-legal-issue-start.png


    * Step 2: Update the legal-issue-split widget to:

      * add the number to the post-triage-start route; this will include it in Guided Navigation
      * if you moved eviction from 4 to another number, update the exit-to-eviction message

    .. image:: ../assets/twilio-split-legal-issue.png


  * In the Guided Navigation service, add a new case for the new term.

  .. code-block:: javascript

      case "3": //food stamps
      processid = "9f85caf4-ee31-11ea-9df9-0e8d40a13cd5"
      lsc_code = "73 Food Stamps";
      search_term = "snap";
      break;

  * Save and deploy the updated function
  * Test that the process id is returned. In a browser, open https://guided-nav-1608.twil.io/get-process-list?issue= and append the new number (1,2,3 etc). It should return json like the following:

   .. code-block:: json

     {"processid":"b6484ace-ed77-11ea-9836-0e8d40a13cd5",
     "lsc_code":"71 TANF",
     "search_term":"tanf"}

.. warning:: If you get anything other than JSON, you have an error. If you can not find it quickly, undo your changes and ask Gwen for help.


Demographic taxonomy terms
=============================

Taxonomy terms for gender, race, ethnicity, etc, that are used in the SMS application, are stored in functions rather than pulled from the website.

Any change needs to be made in both the relevant otis-load and otis-validate functions. Each demographic term has its own pair of functions (for example, otis-load-genders and otis-validate-genders).

.. code-block:: javascript


   if (event.langcode == null || event.langcode == 'en') {
     marital.push('Single','Married','Divorced','Separated','Widowed');
     marital.push('Other', 'Prefer not to respond');
   }
   else {
    marital.push('Soltero','Casado','Divorciado','Separado','Viudo');
    marital.push('Otros', 'Prefiero no contestar');
  }


.. todo:: Replace this with API calls to the website.


