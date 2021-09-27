====================================
Updating Twilio for new legal issue
====================================

Step 1: Update the Get process function
=========================================

Open the get-process-list function in the guided-nav function under Functions->Services in Twilio.  There is a case function that contains each of the legal issues supported by the application.

.. note:: For best results, copy the code to a text editor first in case you need to undo your changes.

.. code-block:: javascript

     case "1": //unemployment
     processid = "9fa873d0-55b8-11eb-939c-0e8d40a13cd5";
     lsc_code = "76 Unemployment Compensation";
     search_term = "afa23f49-7a9d-4caf-b9ac-63da005dc20a";
     content_url = "https://www.illinoislegalaid.org/legal-information/unemployment-benefits";
     rest_export = "https://www.illinoislegalaid.org/rest/unemployment-cases";
     break;

For each legal issue there is:

* A case with a number. This matches the number from the SMS widget that asks user to select their problem. Adding a new one should be added after the last one with the next sequential number.
* processid: this is the unique process id from Legal Server
* lsc_code: this should be the string that matches Legal Server's problem code list
* content_url: this should be a landing page for sending a user when they exit the system for a legal topic.
* rest_export: this is the url for the rest export of the related case acceptance view for the legal issue.


To add a new issue:
* Add a new case statement with the new information
* Save and deploy the updated function
* Test that the process id is returned. In a browser, open https://guided-nav-1608.twil.io/get-process-list?issue= and append the new number (1,2,3 etc). It should return json like the following:

   .. code-block:: json

     {"processid":"9fa873d0-55b8-11eb-939c-0e8d40a13cd5",
     "lsc_code":"76 Unemployment Compensation",
     "search_term":"afa23f49-7a9d-4caf-b9ac-63da005dc20a",
     "content_url": "https://www.illinoislegalaid.org/legal-information/unemployment-benefits",
     "rest_export":"https://www.illinoislegalaid.org/rest/unemployment-cases"}

.. warning:: If you get anything other than JSON, you have an error. If you can not find it quickly, undo your changes and ask Gwen for help.


Step 2: Update the Studio Flow
================================
* In the OTIS flow:

    * Step 1: Add a number and label for the legal issue. This should match the number added in step 1. Eviction should be moved down a number as needed.

    .. image:: ../assets/twilio-legal-issue-start.png


    * Step 2: Update the legal-issue-split widget to:

      * add the number to the post-triage-start route; this will include it in Guided Navigation
      * if you moved eviction from 4 to another number, update the exit-to-eviction message.

    .. image:: ../assets/twilio-split-legal-issue.png
