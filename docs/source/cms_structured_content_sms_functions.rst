=============================================
Twilio service: Structured content functions
=============================================

The ilao-structured-content service contains all the calls to our API to deliver structured content over SMS.

.. note:: Our API relies heavily on the uuid (unique identiifer of each node and paragraphs block). Because of the way we nested paragraph entities within structured content, there are a lot of nested uuid's and entities within each node.

Get Legal Problem List
========================
Returns all legal problems from the website.

Returns an array of objects. Each object in the array contains:

* id = uuid of the legal problem
* title
* description
* array of subtypes

.. code-block:: json

   [
     {
       "id":"9cff9122-2e2e-404a-b909-bf58955c40a6",
       "title":"Unemployed",
       "description":"Information on getting a job, getting unemployment insurance (ui)   benefits, and other help for people out of work.",
      "subtype":[
            "Lost my job"
          ]
    },
    {
      "id":"7ee8c266-b4c2-454b-9a49-705833ae8eda",
      "title":"I lost my job",
      "description":"Solutions to help you get money after you lose your job.",
      "subtype":[
      "And I need money"
      ]
    }]


.. todo:: Need to update to better segment problems based on legal topic.

Get Legal Problem
===================

Requires UUID of the problem to get.

Returns an object of metadata about the problem. This includes:

* id (uuid of the problem)
* nid
* langcode
* problem (node title)
* description
* array of subtypes
* array of citations; this is the uuid of the citations paragraph objects.
* array of uuids of legal questions attached to the problem
* array of uuids of of the introduction paragraph object
* array of uuids of attached solutions.
* array of uuids of related resources


.. code-block:: json

   {"id":"2c155241-4ece-429e-a415-6f674da0ed63",
    "nid":172936,
    "langcode":"en",
    "problem":"I have a cannabis arrest or conviction",
    "description":"Solutions to help if you have a cannabis record.",
    "subtype":[],
    "citation_field":"paragraph--citation",
    "citations":["8ec7f4ac-3a3a-42df-8152-68dba03b91e9"],
    "faq_field":"node--legal_question",
    "legal_questions":
       ["36f0044c-58e5-47af-9958-6f081b4eb307",
     "0bfcc9fb-a36a-4673-a3e8-6033eb348242",
     "584f63b0-ec2f-4bbf-a9c8-63e565722267",
     "be65dca1-d433-4048-840f-f7b6f6ee0b18",
     "7b6034c7-4ba0-4a06-8602-66cc6526a290",
     "e8558af5-96c4-4083-a5f0-ac9b0c7c0f2b"],
    "introduction_field":"paragraph--structured_text_block",
    "introduction":["52b0a757-ae7b-4e63-9d76-70fd97d5766f"],
    "legal_solutions_field":"node--legal_solution",
    "legal_solutions":
    ["a910a290-5112-4206-94fb-f2e67cb74394",
    "bef01ed0-efb6-4d52-94bf-aeaf3e42dd72",
    "ff995076-d7f3-43fb-97b3-4a3a341f37f3"],
    "related_resources_field":"node--legal_content",
    "related_resources":["3982b436-2b51-45f8-a469-79ae7a175a48"]}


.. todo:: Citations, solutions, and related resources should return better data than just the uuid.

Get Legal Problem Introduction
===============================

Requires the UUID of a specific Legal Problem node.

Returns an object containing:

* Segment count (number of segments in the response)
* Array of segments

Dependencies
--------------
Requires the parse-paragraphs-into-structure function to put the paragraphs that make up the introduction together and in the proper order.


Get Solution List for Problem
===============================

Requires a legal problem UUID

Returns an array of solutions. Each solution object includes:

* id (the UUID of the solution)
* title of the solution
* description of the solution

.. code-block:: JSON

   [
   {"id":"b2349f43-cac0-4653-8f01-1d36b266362c",
   "title":"Catch up on rent",
   "description":"One way to avoid an eviction is to catch up on your rent."},
   {"id":"e2575a13-3da5-4e3f-90c3-bf158dbb1279",
   "title":"Negotiate a settlement",
   "description":"To avoid being evicted, you can try to negotiate a settlement with your landlord."},
   {"id":"c1b23431-953e-43ab-b0e4-dfd84453a456",
   "title":"Challenge the eviction notice","description":"You can challenge the service of the notice."},
   {"id":"158672a4-02be-4e63-8872-f370ff78cbc7",
   "title":"Challenge the eviction notice",
   "description":"You can challenge the service of the notice."},
   {"id":"62113f64-39e8-4849-ab7a-925a4bbf57fc",
   "title":"Challenge the eviction notice ",
   "description":"You can challenge the service of the notice."},
   {"id":"ea941419-5cea-44a2-83ab-66fc1ec3aca1",
   "title":"Ask the judge to dismiss because the summons wasn't served properly",
   "description":"If you were never properly served the summons, you can ask the judge to dismiss the case."},
   {"id":"658128a7-65cd-444c-8096-8f0dd266f5e4",
   "title":"Participate in the eviction case",
   "description":"Guides you through the options and steps to participate in the case when you are being evicted"},
   {"id":"d6f2f0c9-34f1-4ef7-bbac-4cfa18b057a0",
   "title":"Do nothing",
   "description":"You can choose to ignore the eviction process. This will not stop the eviciton."}
   ]


Get Legal Solution
====================

Requires a specific UUID for a legal solution

Returns an object containing metadata about the solution:

* id (uuid of the solution)
* nid (node id of the solution)
* langcode
* solution (title of the node)
* description
* legal_difficulty
* array of UUID's of legal questions attached to the solution
* how_to_count (number of how to's in the solution)
* array of how_tos


.. todo:: Can we return question titles? Also how_tos array should include title and uuid.

Get Legal Solution Eligibility
=================================

Requires a specific UUID for a legal solution

Returns an object contaiining:

* Segment count (number of segments in the response)
* Array of segments

Dependencies
--------------
Requires the parse-paragraphs-into-structure function to put the paragraphs that make up the introduction together and in the proper order.

.. code-block:: JSON

   {"segment_count":10,
   "segments":
   ["You must have:\n\n",
   "* An arrest as an adult, \n* For possession or dealing 30 grams or less,\n* Before June 25, 2019.\n",
   "The arrest must have:",
   "* Occurred at least 1 year ago,\n* Not resulted in charges,\n* Resulted in charges that were dismissed or vacated,\n* Resulted in charges but you were acquitted, or \n* Resulted in charges, you were given supervision or qualified probation, and \nyou completed it.\n",
   "This does not include arrests outside sections 4 and 5 of the Cannabis Control Act, like",
   "* Delivery on school grounds,\n* Cannabis trafficking, or \n* Possession of cannabis plants.\n","You must not have:",
   "* Given weed to someone under 18 who was at least 3 years younger than you, or\n\n \n* Been arrested for a violent crime in the same case as the weed charges. This \nincludes:\n* Any felony where force or threat of force was used,\n* Any offense involving sexual conduct,\n* Child pornography or revenge pornography,\n* Domestic battery or stalking,\n* Violating an Order of Protection, \n* Any misdemeanor that results in death or major injury, and\n* Involuntary manslaughter or reckless homicide.\n",
   "If all of this is true, the police will automatically remove your record based on when you were arrested.","The process above only applies to police records. If a court case was started, there will also be court records. These will not be automatically expunged. You must file a request to expunge them with the circuit clerk.\n\n"]
   }


Get Legal How-to
==================

Requires a specific UUID for a Legal How-to node

Returns an object containing metadata for the how-to including:

* id (UUID of the Legal How-to)
* nid (node ID of the how to)
* language code
* howto (title of the how to)
* description
* steps_number
* array of steps. Each step object includes:

  * nid of the step
  * id (UUID of the step)
  * step title
  * order


.. code-block:: JSON

   {"id":"faba2f2c-bd13-4474-90a6-160d6605680e",
   "nid":166921,
   "langcode":"en",
   "howto":"How to apply for unemployment benefits from IDES",
   "description":"Explains how to apply for unemployment benefits if you have lost your job. Includes how to continue receiving them every two weeks.",
   "steps":[
   {"nid":166886,
   "id":"5e640607-35a5-4d8b-a2f9-d3b5e40710f0",
   "title":"Prepare and gather information for unemployment application",
   "order":1},
   {"nid":166896,"
   id":"b741a4d5-f4c5-4370-83d1-b76f6a2f6938",
   "title":"Fill out and submit your unemployment application",
   "order":2},
    ]}


.. todo:: Review for when we have multiple step sections.


Get Legal Step
===============

Requires a specific UUID for a Legal Step

Returns an object that includes:

* Title of the step
* Whether the step has forms (true or false)
* the step text blocks. Each step text block includes:

  * a label (Direction or Tip or blank). A label will be blank if it is not the first paragraph section in a direction or tip.
  * text of the segment
  * optionally, a text list of form node IDs when has_forms is true.


.. code-block:: JSON

   {"title":"Prepare for your SNAP appeal hearing",
   "has_forms":false,
   "steps":[
   {"label":"Direction",
   "text":"Prepare for your hearing"},
   {"label":"",
   "text":"You should begin preparing for your Supplemental Nutrition Assistance Program (SNAP) benefits appeal hearing as soon as you file your notice of appeal. It would be helpful to write down:\n\n * The problem or issue you are appealing; * The important events in the order that they happened; * Why you think DHS is wrong; and * Any incorrect information DHS used to decide your case.\n\n"},
   {"label":"",
   "text":"If there are witnesses who can help your case, bring them to the hearing. You should also bring any paperwork that would help you. Witnesses are most helpful when you do not agree with DHS about something that was said or happened and your witness was there."},{"label":"","text":"If you are appealing a decision DHS made because you did not give DHS information it requested, you can give DHS the information during the appeal. DHS must reconsider your eligibility based on the new information. A denied application or canceled case can be reopened. If you are told you have to file a new application, tell the supervisor that rule PM 01-07-08 allows you to turn in new documents any time during the appeal."},
   {"label":"",
   "text":"You may present other information or verifications to DHS at any time during the appeal process. DHS has to reconsider your eligibility based on the new information. A denied application or canceled case can be reopened. If you are told you have to file a new application, tell the supervisor that rule PM 01-07-08 allows you to turn in new documents any time."},
   {"label":"Tip: ",
   "text":"If necessary, you can ask for your hearing to be pushed back to a later date. This is called a continuance. You do not have to show \"good cause\" or a valid reason for the first continuance. If you request another continuance, then you must show good cause. An example of a good cause is a family emergency. \n\n"}
   ]}

Get Legal Forms for Step
===========================

Requires a comma-delimited list of node IDs of Legal Forms

Returns an object with 2 arrays:

* Blank forms ("blank") is an object containing an array of form objects. For each unique url, there is an array element with an object that contains:

  * The url to the blank form
  * The label from the form prep program
  * An array of forms (title of the legal form node)

Blank forms are usually a 1 form per url but if a specific url creates 2 or more forms, the forms will be grouped together.

* Easy forms is an object containing an array of form objects. For each unique url, there is an array element with an object that contains:

  * The url to the blank form
  * The label from the form prep program
  * An array of forms (title of the legal form node)

Easy Forms usually produce multiple forms in a single package. Each Easy form url will be grouped together, using the first group label from the form prep program element and then each Legal Form node title will be added to the array of forms.

.. code-block:: JSON

   {"blank":[
   {"url":"https://ilcourtsaudio.blob.core.windows.net/antilles-resources/resources/c1b07890-c843-44d9-ac3c-2107c9253e11/CXP%20Instructions.pdf",
   "label":"How to Vacate & Expunge Eligible Cannabis Convictions",
   "forms":["How to Vacate & Expunge Eligible Cannabis Convictions"]
   },
   {
   "url":"https://ilcourtsaudio.blob.core.windows.net/antilles-resources/resources/8562a938-0296-4236-9030-3217460e8b5c/CXP%20Motion%20to%20Vacate%20and%20Expunge.pdf",
   "label":"Motion to Vacate & Expunge Eligible Cannabis Convictions",
   "forms":["Motion to Vacate & Expunge Eligible Cannabis Convictions"]
   },
      {
      "url":"https://ilcourtsaudio.blob.core.windows.net/antilles-resources/resources/0c788d57-5951-47d9-9946-dfc36b7d1d50/CXP%20Order%20Granting%20or%20Denying%20Motion.pdf",
      "label":"Order granting or denying motion to vacate and expunge eligible cannabis convictions ",
      "forms":["Order Granting or Denying Motion to Vacate & Expunge Eligible Cannabis Convictions"]
      }
      ],
   "easyforms":[
   {"url":"www.illinoislegalaid.org/node/173941",
   "label":"Cannabis expungement",
   "forms":[
   "How to Vacate & Expunge Eligible Cannabis Convictions",
   "Motion to Vacate & Expunge Eligible Cannabis Convictions",
   "Notice of Court Date for Motion to Vacate & Expunge Eligible Cannabis Convictions",
   "Order Granting or Denying Motion to Vacate & Expunge Eligible Cannabis Convictions",
   "Additional Cannabis Convictions",
   "Additional Notice of Court Date for Motion to Vacate & Expunge Eligible Cannabis Convictions"]}
   ]}

Get Legal Question
====================
Requires a UUID for a specific legal question.

Returns an object:

* id (uuid of the question)
* nid (node id of the question)
* langcode
* title
* description
* answer, which is an object containing:

  * segment_count
  * array of segments

.. code-block:: JSON

   {"id":"0bfcc9fb-a36a-4673-a3e8-6033eb348242",
   "nid":172616,
   "langcode":"en",
   "title":"What is cannabis expungement?",
   "description":"Explains what cannabis expungement is.",
   "answer":
     {"segment_count":1,
      "segments":
       [ "Part of the law that legalized weed (also known as cannabis or marijuana) created ways to clear criminal records for weed. This is called expungement. There are different ways to have your record expunged, depending on what type of record you have.\n\n"]
     }
   }

