=================================
Structured Content Types
=================================

Content Types
===============

Legal Problem
----------------
The primary content type for structured content is the Legal Problem. 

+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Title (name)    | Title field       | 1; required    | Name of the legal problem   |
+-----------------+-------------------+----------------+-----------------------------+
| Description     | Text area         | 1,required     | Content description         |
+-----------------+-------------------+----------------+-----------------------------+
| Meta            | Text area         | 1, required    | Current meta description    |
| Description     |                   |                |                             |  
+-----------------+-------------------+----------------+-----------------------------+
| Disambiguation  | Text area (plain) | 1              | A short description of the  |
| Description     |                   |                | item used to disambiguate   |
|                 |                   |                | from other, similar items   |
+-----------------+-------------------+----------------+-----------------------------+
| Identifier      | Hidden            |                | Node UUID                   |
+-----------------+-------------------+----------------+-----------------------------+
| Legal issues    | Term reference    | unlimited,     | Current legal issues field  |
|                 |                   | required       |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Primary legal   | Term reference    | 1, required    | Current primary legal       |
| category        |                   |                | category                    |
+-----------------+-------------------+----------------+-----------------------------+
| Stage           | Text field        | 1              | The stage of the legal      |
|                 |                   |                | problem, if applicable. For |
|                 |                   |                | example, pre-filing, post-  |
|                 |                   |                | filing/pre-trial, trial, etc|
+-----------------+-------------------+----------------+-----------------------------+
| Subtype         | Text field        | unlimited      | A more specific type of the |
|                 |                   |                | legal problem. For example, |
|                 |                   |                | 'being evicted from public  |
|                 |                   |                | housing' under the problem  |
|                 |                   |                | "being evicted"             |
+-----------------+-------------------+----------------+-----------------------------+
| LegalCode       | Paragraphs: Legal | unlimited      | Legal code from standard    |
|                 |                   | required       | coding systems              |
+-----------------+-------------------+----------------+-----------------------------+
| LifeAreaAffected| Term reference    | unlimited      | The area of a person's life |
|                 | to Life Areas     | required       | that is affected by the     |
|                 |                   |                | legal problem.              |
+-----------------+-------------------+----------------+-----------------------------+
|Possible solution| Entity reference  | unlimited      | Entity reference to Legal   |
|                 |                   | required       | Solution nodes              |
+-----------------+-------------------+----------------+-----------------------------+ 
| Primary         | Entity reference  | 1              | Entity reference to legal   |
| prevention      |                   |                | solution nodes              |
+-----------------+-------------------+----------------+-----------------------------+ 
| Secondary       | Entity reference  | 1              | Entity reference to legal   |
| prevention      |                   |                | solution nodes              |
+-----------------+-------------------+----------------+-----------------------------+ 
| FAQ             | Entity reference  | unlimited      | Entity reference to         |
|                 |                   |                | Legal Question              |
+-----------------+-------------------+----------------+-----------------------------+ 
| RelatedResources| Entity reference  | unlimited      | Entity reference to legal   |
|                 |                   |                | content types               |
+-----------------+-------------------+----------------+-----------------------------+ 
| RelatedProblems | Entity reference  | unlimited      | Entity reference to Legal   |
|                 |                   |                | Problem                     |
+-----------------+-------------------+----------------+-----------------------------+
| Citations       | Paragraphs        | unlimited      | Citation block              |
+-----------------+-------------------+----------------+-----------------------------+ 
| Image           | Image             | 1              | Image to associate with node|
+-----------------+-------------------+----------------+-----------------------------+ 
| Language        | Hidden            | 1              | Language of the node        |
+-----------------+-------------------+----------------+-----------------------------+ 
| url             | Hidden            | 1              | Website url for the node    |
+-----------------+-------------------+----------------+-----------------------------+
| legal position  | List              | 1, required    | Current field_legal_position|
+-----------------+-------------------+----------------+-----------------------------+ 
| content managem | Term reference    | unlimited      | Current content management  |
| ent tags        |                   |                | tags                        |
+-----------------+-------------------+----------------+-----------------------------+
| request         | Boolean           | 1, default to  | Should translation be       |
| to be translated|                   | No             | requested                   |
+-----------------+-------------------+----------------+-----------------------------+
| mark translation| Boolean           | 1, default to  | Existing field              |
| as outdated     |                   | No             | mark as outdated            |
+-----------------+-------------------+----------------+-----------------------------+

.. note:: 
   
   The related resources will automatically pull the name, last modified (last internal revision date), last reviewed (last expert review date), url, and content format as additionalType in exporting the schema.

Legal Solution
----------------

+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Title (body)    | Title field       | 1              | Solution title              |
+-----------------+-------------------+----------------+-----------------------------+
| Alternate name  | Text field        | 1              | An alternative name for the |
|                 |                   |                | solution                    |
+-----------------+-------------------+----------------+-----------------------------+
| Description     | Text area         | 1,required     | Content description         |
+-----------------+-------------------+----------------+-----------------------------+
| Meta            | Text area         | 1, required    | Current meta description    |
| Description     |                   |                |                             |                
+-----------------+-------------------+----------------+-----------------------------+
| Disambiguation  | Text area (plain) | 1              | A short description of the  |
| Description     |                   |                | item used to disambiguate   |
|                 |                   |                | from other, similar items   |
+-----------------+-------------------+----------------+-----------------------------+
| Legal issues    | Term reference    | unlimited,     | Current legal issues field  |
|                 |                   | required       |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Primary legal   | Term reference    | 1, required    | Current primary legal       |
| category        |                   |                | category                    |
+-----------------+-------------------+----------------+-----------------------------+
| Identifier      | Hidden            | 1              | Node UUID                   |
+-----------------+-------------------+----------------+-----------------------------+
| url             | Hidden            | 1              | Website url for the node    |
+-----------------+-------------------+----------------+-----------------------------+
| solution type   | Term reference    | 1              | Reference to solution types |
+-----------------+-------------------+----------------+-----------------------------+
| legal forms     | Entity reference  | unlimited      | Reference to legal forms    |
| needed          |                   |                |                             |
+-----------------+-------------------+----------------+-----------------------------+
| information     | Text field        | unlimited      |                             |
| needed          |                   |                |                             |
+-----------------+-------------------+----------------+-----------------------------+
| legalDifficulty | Text area         | 1              | Explanation of the legal    |
|                 |                   |                | difficulty involved         |
+-----------------+-------------------+----------------+-----------------------------+
| estimated time  | Duration          | 1              |                             |
| required        |                   |                |                             |
+-----------------+-------------------+----------------+-----------------------------+
| eligibilityRules| Paragraphs        | unlimited      | Text blocks                 |
+-----------------+-------------------+----------------+-----------------------------+
| jurisdiction    | Paragraphs        | unlimited      | Coverage area paragraphs    |
+-----------------+-------------------+----------------+-----------------------------+
| helpful         | entity reference  | unlimited      | Helpful organizations       |
| organizations   |                   |                | content type                |
+-----------------+-------------------+----------------+-----------------------------+
| legal organiza  | entity reference  | unlimited      | reference to organization   |
| tions           |                   |                | (group)                     |
+-----------------+-------------------+----------------+-----------------------------+
| howTos          | Entity reference  | unlimited      | Reference to a legal how to |
+-----------------+-------------------+----------------+-----------------------------+
| result          | Paragraphs        | one            | Text blocks                 |
+-----------------+-------------------+----------------+-----------------------------+
| citations       | Paragraphs        | unlimited      | Citation block              |
+-----------------+-------------------+----------------+-----------------------------+ 
| legal position  | List              | 1, required    | Current field_legal_position|
+-----------------+-------------------+----------------+-----------------------------+ 
| content managem | Term reference    | unlimited      | Current content management  |
| ent tags        |                   |                | tags                        |
+-----------------+-------------------+----------------+-----------------------------+
| request         | Boolean           | 1, default to  | Should translation be       |
| to be translated|                   | No             | requested                   |
+-----------------+-------------------+----------------+-----------------------------+
| mark translation| Boolean           | 1, default to  | Existing field              |
| as outdated     |                   | No             | mark as outdated            |
+-----------------+-------------------+----------------+-----------------------------+


Legal Question
----------------

Single question; packaged within an FAQ in a legal problem. 

+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Title (body)    | Title field       | 1              | Question title              |
+-----------------+-------------------+----------------+-----------------------------+
| Accepted Answer | Paragraphs        | 1              | Text block paragraphs       |
+-----------------+-------------------+----------------+-----------------------------+
| Suggested       | Paragraphs        | unlimited      | Text block paragraphs       |
| Answer          |                   |                |                             |
+-----------------+-------------------+----------------+-----------------------------+
| legal position  | List              | 1, required    | Current field_legal_position|
+-----------------+-------------------+----------------+-----------------------------+ 
| content managem | Term reference    | unlimited      | Current content management  |
| ent tags        |                   |                | tags                        |
+-----------------+-------------------+----------------+-----------------------------+
| request         | Boolean           | 1, default to  | Should translation be       |
| to be translated|                   | No             | requested                   |
+-----------------+-------------------+----------------+-----------------------------+
| mark translation| Boolean           | 1, default to  | Existing field              |
| as outdated     |                   | No             | mark as outdated            |
+-----------------+-------------------+----------------+-----------------------------+
| Description     | Text area         | 1,required     | Content description         |
+-----------------+-------------------+----------------+-----------------------------+
| Meta            | Text area         | 1, required    | Current meta description    |
| Description     |                   |                |                             |                
+-----------------+-------------------+----------------+-----------------------------+
| Legal issues    | Term reference    | unlimited,     | Current legal issues field  |
|                 |                   | required       |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Primary legal   | Term reference    | 1, required    | Current primary legal       |
| category        |                   |                | category                    |
+-----------------+-------------------+----------------+-----------------------------+
| Annual updates  | Term reference    | unlimited      | Current annual updates field|
+-----------------+-------------------+----------------+-----------------------------+
| Author/SME      | Entity reference  | unlimited      | Current author/SME field    |
+-----------------+-------------------+----------------+-----------------------------+
| jurisdiction    | Paragraphs        | unlimited      | Coverage area paragraphs    |
+-----------------+-------------------+----------------+-----------------------------+
| Last reviewed   | Date time         | 1              | Current last reviewed field |
+-----------------+-------------------+----------------+-----------------------------+
| Last revised    | Date time         | 1              | Current last revise field   |
+-----------------+-------------------+----------------+-----------------------------+

Legal Forms
---------------
+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Title (formName)| Title field       | 1              | Form title                  |
+-----------------+-------------------+----------------+-----------------------------+
| FilledOutWith   | Paragraphs        | unlimited      | FormPrep Program paragraphs |
+-----------------+-------------------+----------------+-----------------------------+
| formUse         | Text area         | 1              | Explanation of how/when the |
|                 |                   |                | form is used                |
+-----------------+-------------------+----------------+-----------------------------+
| legal position  | List              | 1, required    | Current field_legal_position|
+-----------------+-------------------+----------------+-----------------------------+ 
| content managem | Term reference    | unlimited      | Current content management  |
| ent tags        |                   |                | tags                        |
+-----------------+-------------------+----------------+-----------------------------+
| request         | Boolean           | 1, default to  | Should translation be       |
| to be translated|                   | No             | requested                   |
+-----------------+-------------------+----------------+-----------------------------+
| mark translation| Boolean           | 1, default to  | Existing field              |
| as outdated     |                   | No             | mark as outdated            |
+-----------------+-------------------+----------------+-----------------------------+
| Description     | Text area         | 1,required     | Content description         |
+-----------------+-------------------+----------------+-----------------------------+
| Meta            | Text area         | 1, required    | Current meta description    |
| Description     |                   |                |                             |                
+-----------------+-------------------+----------------+-----------------------------+
| jurisdiction    | Paragraphs        | unlimited      | Coverage area paragraphs    |
+-----------------+-------------------+----------------+-----------------------------+
| Legal issues    | Term reference    | unlimited,     | Current legal issues field  |
|                 |                   | required       |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Primary legal   | Term reference    | 1, required    | Current primary legal       |
| category        |                   |                | category                    |
+-----------------+-------------------+----------------+-----------------------------+
| Last reviewed   | Date time         | 1              | Current last reviewed field |
+-----------------+-------------------+----------------+-----------------------------+
| Last revised    | Date time         | 1              | Current last revised field  |
+-----------------+-------------------+----------------+-----------------------------+



Legal How-to
---------------
+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Title (Name)    | Title field       | 1, required    | Title                       |
+-----------------+-------------------+----------------+-----------------------------+
| prepTime        | duration          | 1, required    |                             |
+-----------------+-------------------+----------------+-----------------------------+
| performTime     | duration          | 1, required    |                             |
+-----------------+-------------------+----------------+-----------------------------+
| totalTime       | duration          | 1, required    | Prep time + perform time    |
+-----------------+-------------------+----------------+-----------------------------+
| stepSections    | paragraphs bundle | unlimited      | Reference to step sections  |
+-----------------+-------------------+----------------+-----------------------------+
| supply          | text field        | unlimited      | Things needed to complete   |
|                 |                   |                | the how-to                  |
+-----------------+-------------------+----------------+-----------------------------+
| tool            | text field        | unlimited      | Tools needed to complete the|
|                 |                   |                | how to                      |
+-----------------+-------------------+----------------+-----------------------------+
| yield           | text field        | one            | The quantity that results by|
|                 |                   |                | performing instructions     |
+-----------------+-------------------+----------------+-----------------------------+
| legal position  | List              | 1, required    | Current field_legal_position|
+-----------------+-------------------+----------------+-----------------------------+ 
| content managem | Term reference    | unlimited      | Current content management  |
| ent tags        |                   |                | tags                        |
+-----------------+-------------------+----------------+-----------------------------+
| request         | Boolean           | 1, default to  | Should translation be       |
| to be translated|                   | No             | requested                   |
+-----------------+-------------------+----------------+-----------------------------+
| mark translation| Boolean           | 1, default to  | Existing field              |
| as outdated     |                   | No             | mark as outdated            |
+-----------------+-------------------+----------------+-----------------------------+
| Description     | Text area         | 1,required     | Content description         |
+-----------------+-------------------+----------------+-----------------------------+
| Meta            | Text area         | 1, required    | Current meta description    |
| Description     |                   |                |                             |                
+-----------------+-------------------+----------------+-----------------------------+
| Legal issues    | Term reference    | unlimited,     | Current legal issues field  |
|                 |                   | required       |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Primary legal   | Term reference    | 1, required    | Current primary legal       |
| category        |                   |                | category                    |
+-----------------+-------------------+----------------+-----------------------------+
| Annual updates  | Term reference    | unlimited      | Current annual updates field|
+-----------------+-------------------+----------------+-----------------------------+
| Author/SME      | Entity reference  | unlimited      | Current author/SME field    |
+-----------------+-------------------+----------------+-----------------------------+
| jurisdiction    | Paragraphs        | unlimited      | Coverage area paragraphs    |
+-----------------+-------------------+----------------+-----------------------------+
| Last reviewed   | Date time         | 1              | Current last reviewed field |
+-----------------+-------------------+----------------+-----------------------------+
| Last revised    | Date time         | 1              | Current last revised field  |
+-----------------+-------------------+----------------+-----------------------------+



Legal Step
-------------
+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Title (Name)    | Title field       | 1, required    |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Step information| paragraphs bundle | unlimited      | Directions or Tips bundle   |
+-----------------+-------------------+----------------+-----------------------------+
| legal position  | List              | 1, required    | Current field_legal_position|
+-----------------+-------------------+----------------+-----------------------------+ 
| content managem | Term reference    | unlimited      | Current content management  |
| ent tags        |                   |                | tags                        |
+-----------------+-------------------+----------------+-----------------------------+
| request         | Boolean           | 1, default to  | Should translation be       |
| to be translated|                   | No             | requested                   |
+-----------------+-------------------+----------------+-----------------------------+
| mark translation| Boolean           | 1, default to  | Existing field              |
| as outdated     |                   | No             | mark as outdated            |
+-----------------+-------------------+----------------+-----------------------------+
| Description     | Text area         | 1,required     | Content description         |
+-----------------+-------------------+----------------+-----------------------------+
| Meta            | Text area         | 1, required    | Current meta description    |
| Description     |                   |                |                             |                
+-----------------+-------------------+----------------+-----------------------------+
| Legal issues    | Term reference    | unlimited,     | Current legal issues field  |
|                 |                   | required       |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Primary legal   | Term reference    | 1, required    | Current primary legal       |
| category        |                   |                | category                    |
+-----------------+-------------------+----------------+-----------------------------+
| Annual updates  | Term reference    | unlimited      | Current annual updates field|
+-----------------+-------------------+----------------+-----------------------------+
| Author/SME      | Entity reference  | unlimited      | Current author/SME field    |
+-----------------+-------------------+----------------+-----------------------------+
| jurisdiction    | Paragraphs        | unlimited      | Coverage area paragraphs    |
+-----------------+-------------------+----------------+-----------------------------+
| Last reviewed   | Date time         | 1              | Current last reviewed field |
+-----------------+-------------------+----------------+-----------------------------+
| Last revised    | Date time         | 1              | Current last revised field  |
+-----------------+-------------------+----------------+-----------------------------+


.. note:: There is also a position property in the legal steps in the schema. This is computed in the step sections paragraph bundle in the How-to and not stored directly in the steps. This will allow for step re-use.


Helpful Organization
---------------------
.. note::
   ILAO already has organization profile data that should be used for any organization in our system. New entities should only be added to reference organizations that are not legal services providers within our Organization platform.
   
   Fields will be hidden when an Organization is included.

+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Title (Name)    | Title field       | 1, required    |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Description     | Text area         | 1              |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Address         | Address           | 1              |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Area Served     | Paragraphs bundle | unlimited      | Coverage area               |
+-----------------+-------------------+----------------+-----------------------------+
| Email           | Email             | 1              |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Telephone       | Text field        | 1              |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Contact         | Paragraphs bundle | unlimited      |                             |
+-----------------+-------------------+----------------+-----------------------------+
| content managem | Term reference    | unlimited      | Current content management  |
| ent tags        |                   |                | tags                        |
+-----------------+-------------------+----------------+-----------------------------+
| request         | Boolean           | 1, default to  | Should translation be       |
| to be translated|                   | No             | requested                   |
+-----------------+-------------------+----------------+-----------------------------+
| mark translation| Boolean           | 1, default to  | Existing field              |
| as outdated     |                   | No             | mark as outdated            |
+-----------------+-------------------+----------------+-----------------------------+
| Last revised    | Date time         | 1              | Current last reviewed field |
+-----------------+-------------------+----------------+-----------------------------+

Paragraph Bundles
===================

There are a number of paragraphs bundle created to support the content entities in the schema:

* LegalCode, used in LegalProblem
* FormPrepProgram, used in LegalForms
* Step section, a holder for steps in Legal How-to
* How to directions and tips, used in Legal Steps
* CoverageArea, used in Legal Solution, Organization
* TextBlock, used in various text output where we need more control over structure.
* Contact point
* Paired markup to pair a WYSIWYG item with a plain text with footnotes version

Legal Code
------------
+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Code value      | Text field        | 1              |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Coding system   | Text field        | 1              |                             |
+-----------------+-------------------+----------------+-----------------------------+

Form Prep Program
--------------------

+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| name            | text  field       | 1              | Name of the form prep       |
|                 |                   |                | package or Easy Form        |                
+-----------------+-------------------+----------------+-----------------------------+
| url             | link              | 1              | link to the form prep       |
+-----------------+-------------------+----------------+-----------------------------+
| formPrepProgram | term reference    | 1              | Reference to the form prep  |
|                 |                   |                | programs taxonomy           |
+-----------------+-------------------+----------------+-----------------------------+

Legal Step Sections
----------------------
+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Title (Name)    | Title field       | 1, required    | Title or heading for section|
+-----------------+-------------------+----------------+-----------------------------+
| Include title?  | Boolean           | 1, required    | Include title in API feed?  |
+-----------------+-------------------+----------------+-----------------------------+
| Steps           | Entity reference  | unlimited      | Reference to legal steps    |
+-----------------+-------------------+----------------+-----------------------------+

.. note:: There is also a position property in the steps section in the schema. This is computed in the How To and not stored directly in the steps. 

How To Directions & Tips
--------------------------

+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| How-to Type     | Select            | 1, required    | Tip or Direction            |
+-----------------+-------------------+----------------+-----------------------------+
| Body            | Paragraphs item   | 1, required    | Paired markup               |
+-----------------+-------------------+----------------+-----------------------------+
| referencedUrls  | Links             | unlimited      | Links included in markup    |
+-----------------+-------------------+----------------+-----------------------------+

.. note:: There is also a position property in the schema. This is computed in the How-to and not stored in the database.



Structured Text Block
------------------------

+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Heading         | Text field        | 1              |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Body            | Paragraphs bundle | required       | Paired markup               |
|                 |                   | unlimited      |                             |
+-----------------+-------------------+----------------+-----------------------------+
| List            | Paragraphs bundle | unlimited      | Item list bundle            |
+-----------------+-------------------+----------------+-----------------------------+   

Paired Markup
-----------------         

+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Body            | Hidden            | unlimited,     | Clean version of body with  |
|                 |                   | required       | markup                      |
+-----------------+-------------------+----------------+-----------------------------+
| Body with markup| Text area         | unlimited,     | WYSIWYG                     |
|                 |                   | required       |                             |
+-----------------+-------------------+----------------+-----------------------------+

Structured Item List
----------------------

+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Item List Order | Select            | 1, required    | ascending, descending, or   |
|                 |                   |                | unordered                   |
+-----------------+-------------------+----------------+-----------------------------+
| Item List       | Paragraphs bundle | unlimited,     | Paired markup               |
| Elements        |                   | required       |                             |  
+-----------------+-------------------+----------------+-----------------------------+


Coverage Area
----------------

+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Administrative  | Select            | 1, required    | Country, state, city,       |
| area            |                   |                | postal code                 |
+-----------------+-------------------+----------------+-----------------------------+
| Counties        | Term reference    | unlimited      | Region taxonomy             |
+-----------------+-------------------+----------------+-----------------------------+
| Cities          | Term reference    | unlimited      | Region taxonomy             |
+-----------------+-------------------+----------------+-----------------------------+
| Zip codes       | Term reference    | unlimited      | Region taxonomy             |
+-----------------+-------------------+----------------+-----------------------------+
| Countries       | Country           | unlimited      | Defaults to United States   |
+-----------------+-------------------+----------------+-----------------------------+

Contact Point
------------------
+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Contact type    | Text field        | unlimited      |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Area served     | Paragraphs bundle | unlimited      | Coverage area bundle        |
+-----------------+-------------------+----------------+-----------------------------+
| Email           | Email             | 1              |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Telephone       | Text field        | 1              |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Hours           | Hours field       | unlimited      |                             |
+-----------------+-------------------+----------------+-----------------------------+
| Products        | Text field        | unlimited      | Type of service or product  |
| Supported       |                   |                | offered through the         |
|                 |                   |                | organization.               |
+-----------------+-------------------+----------------+-----------------------------+

Citation
-----------
+-----------------+-------------------+----------------+-----------------------------+
| Field           | Type              | Cardinality    | Description                 |
+=================+===================+================+=============================+
| Citation        | Text field        | one            | Citation text               |
+-----------------+-------------------+----------------+-----------------------------+
| URL             | Link              |one             |  Link to citation           |
+-----------------+-------------------+----------------+-----------------------------+

Taxonomies
=============

* life areas (used in legal problem)
* solution types (used in legal solutions)
* form prep programs (used in Legal forms)


Technical Notes
===================

* We can use \Drupal\Core\Mail\MailFormatHelper::htmlToText($string) to render plain text with urls as footnotes from the with markup fields. 


.. image:: ../assets/clean-markup.png




