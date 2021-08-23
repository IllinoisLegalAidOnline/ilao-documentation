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




