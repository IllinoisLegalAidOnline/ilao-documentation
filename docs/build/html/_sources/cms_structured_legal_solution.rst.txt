.. _cms-legal-solution:

==============================
Legal Solution
==============================

A legal solution is tied to one or more legal problems (see :ref:`cms-legal-problem`) and features:

* content metadata
* a solution type
* 0 or more pieces of needed information
* Legal difficulty (optional)
* Estimated time required to complete the entire process
* One or more eligibility rules to be able to use a specific solution
* A jurisdiction
* Optionally, a negate jurisdiction
* Zero or more helpful organizations
* Zero or more legal organizations
* One or more HowTos
* Zero or more citations
* A result
* Zero or more questions.

.. todo:: Determine if we should have information needed when we have tools/supplies in the how-to; This is especially important if the information needed might vary at a local level. How Tos should be required.

To create a legal solution
=============================

Create the core solution information
---------------------------------------

* Add a title. The title should match our standard title style for process-oriented legal content.
* Add a disambiguation tag, if applicable, to identify this solution from other similarly titled solutions. For example, if the content title is "Participate in the court case" the disambiguation tag might be "Eviction" or "Foreclosure" to distinguish between the two.
* Provide an alternative name if applicable.
* Add a meta description. This is the description that will be used in social media, search indexes, and in any API. This should be limited to 300 characters.
* Optionally, add a disambiguation description. This is used to better describe how one problem is different from a related problem.

Categorize the solution
-------------------------

* Tag the legal problem to one or more navigational IA tags. This is used to manage the drill down.
* Tag the legal problem to one or more legal issues. This is used to associate with Get Legal Help tools.
* Select the primary legal category. This is used to keep the information organized when it is tagged to multiple primary categories (for example, we may tag a criminal records issue to Business & Work and Crime & Traffic).
* Select the primary level 2 navigation term. This is used to help with breadcrumbs, reporting, and Guided Navigation. This single term comes from the navigational IA taxonomy.
* Define the solution type. A solution type are defined by our `solution types taxonomy <https://www.illinoislegalaid.org/admin/structure/taxonomy_manager/voc/solution_types>`_.


Create the solution content
------------------------------

* Define any information the individual needs to complete the solution. For example, a solution to get a divorce with children may require that the user:

  * the name of their spouse
  * the spouse's current address
  * the children's names and ages

* Define the legal difficulty. See style notes below.
* Define any eligibility rules to use a specific solution, if there are specific requirements for using a solution.
* Add the specific how-tos that outline the steps for a solution. A solution can have different how-tos depending on the solution.
* Define the result. This can include:

  * What the individual will get from completing this solution
  * What the user will not get from completing this solution
  * Why the user may not want to use this solution

* Add any helpful organizations to include. A helpful organization would be a non-legal organization that can provide help. See the helpful organization page.
* Add any legal organization that we need to highlight. This typically will be limited to Illinois Legal Aid Online.
* Add any Legal Questions related to the solution that should be included
* Add any Related Resources related to the solution. This would generally be legal content that can not be converted to a Legal Question (for example, videos, flowcharts, decision trees)
* Tag the solution to a specific jurisdiction. In most cases, this will be Illinois. We can define individual steps or how-tos to a specific county or city. This is the preferred approach over making an entire solution county/city specific.
* Add any citations related to the solution.
* Indicate the legal position associated with the solution. This is almost never going to be neutral.


.. note:: See the style notes for more information on when to use helpful vs. legal organizations

Add additional metadata
^^^^^^^^^^^^^^^^^^^^^^^^^^

* Optionally, add any content management tags
* Indicate whether a translation should be requested.
* Indicate whether an existing translation should be marked as outdated.

Style notes
===============


Disambiguation description
-----------------------------
This is an internal descriptor to be used to distinguish one solution from another. Examples may include:

* Appealing a UI denial at the initial stage vs Appealing a UI denial by UI board
* Getting a divorce with children vs Getting a divorce without children

This is used internally only.


Legal difficulty
--------------------
Legal difficulty can be used to indicate how difficult the solution is to execute on your own. Example legal difficulty statements:

* "We rate this an easy task in most cases. Fill out the form and file it with the court. No court appearance is generally required."

* "We rate this as a moderate task in most cases when our Easy Forms are used. You will likely have to appear in court."

* "We rate this as a moderate task in most cases. If you are not a legal resident or citizen, this task should not be undertaken without an attorney."

* "We rate this as a difficult task in most cases. We recommend getting legal advice from a lawyer."

Estimated time required
--------------------------
We want to provide an estimated duration from start to finish to solve the problem. This likely requires input from SMEs


Eligibility rules
--------------------
Eligibility rules use the :ref:`cms-structured-text` block. Each eligibility rule should have its own structured text block.

Examples
^^^^^^^^^^^^
The single eligibility rule below

.. code-block:: html

     <p>To use this program, you or the person you are filing the order against must:</p>
       <ol>
     	<li>Live in the county you are filing the request in;</li>
     	<li>The abuse must have taken place in the county;&nbsp;<strong>OR</strong></li>
	    <li>You must be living in the county temporarily to avoid abuse elsewhere</li>
       </ol>


might be created:

* with a heading of "One of the following must be true"
* with an unordered list of 3 list items:
* You or the person you are filing the order against must live in the county you are filing the request in
* The abuse must have taken place in the county
* You must be living in the county temporarily to avoid abuse elsewhere

.. note:: Because these may be rendered differently in different services, we've removed any punctuation at the end of each list item and have removed any AND/OR parts (instead, the header makes that case clear).

Jurisdiction
---------------
Structured content supports jurisdiction across different pieces of data. See :ref:`cms-coverage-area` documentation. A solution may have a jurisdiction that is broader than an attached How-to, attached steps, or attached organization. A solution, even if it has How-tos that vary by location or forms that apply only to some jurisdictions, can still be marked at a broader jurisdiction so long as:

* the eligibility rules apply to the solution jurisdiction
* the legal difficulty does not vary by location
* the result does not vary location

.. note:: Example:  The steps for getting an order of protection are different in Cook county than in the rest of the states. McHenry county requires a specific form that no one else does. But the eligibility rules, difficulty, and result is the same across Illinois. The solution should be set to Illinois while there should be 2 How-tos (one for Cook county, one for the other 101 counties), and the McHenry form should be specificially tagged to McHenry county.


Legal organization vs Helpful organization
--------------------------------------------

Solutions support both :ref:`cms-legal-helpful-org` and legal organizations.

A helpful organization is one that exists as a structured helpful organization.

Structured helpful organizations have much less information in our system. These are organizations that do not belong in our organization system but that may still be helpful to users  This might include:

* DV shelters and/or hotlines
* Social services
* Government offices

A legal organization is one that exists in `ILAO's organization system <https://www.illinoislegalaid.org/admin/group>`_. Rather than replicate the data as a structured helpful organization, these can be referenced directly as needed in the legal organization field. When one or more OTIS partners take cases in this area and the legal difficulty level is moderate to difficult, we should refer to Illinois Legal Aid Online as a legal organization to cause a prioritized block to appear versus the standard Get Legal Help block.

Result
------------

The result also uses the structured text block. It should be broken down to best support delivery across channels.

Example headings for a result might include:

* Why should I do this?
* Why shouldn't I do this?
* What can't [x] do for me?
* What can [x] do for me?

Example
-------------

.. code-block:: html

   <p>When a judge signs an Order of Protection, it makes it illegal for the abuser to do or not do certain things. For example, a judge can order the abuser to:</p>
   <ul>
	<li>Stop abusive acts;</li>
	<li>Stay away from the victim and other people protected by the order;</li>
	<li>Stop contacting the victim via telephone calls, mail, email, written notes, or third parties;</li>
	<li>Stay away from the victim's home, school, or work;</li>
	<li>Attend counseling;</li>
	<li>Pay child support;</li>
	<li>Return or stay away from the property; and</li>
	<li>Move out of a home they share with the victim.</li>
   </ul>
   <p>A judge can prevent an abuser from viewing the phone records of the victim and any minor child in the victim's custody. The <em>Order of Protection </em>can require phone service providers to transfer service so that the victim can keep the same phone number. The victim will have to pay the bill.&nbsp;</p>
   <p>A judge can also change a person's parental duties&nbsp;(custody/visitation) in an<em> Order of Protection</em>.</p>

This segment above may be structured as:

* Structured text block 1:

  * Body markup: When a judge signs an Order of Protection, it makes it illegal for the abuser to do or not do certain things. For example, a judge can order the abuser to:
  * List segments - unordered
  * A paired markup segment for each list item.

    * Pay child support
    * Return or stay away from the property
    * Move out of a home they share with the victim

* Structured text block 2 with body markup of "A judge can prevent an abuser from viewing the phone records of the victim and any minor child in the victim's custody. The <em>Order of Protection </em>can require phone service providers to transfer service so that the victim can keep the same phone number. The victim will have to pay the bill."
* Structured text block 3 with body markup of "A judge can also change a person's parental duties (custody/visitation) in an Order of Protection."

.. note::  Like in the example for eligibility rules, we have stripped off punctuation and and/or. Basic html markup like italics can be used in body markup but will be stripped in the plain text version.

Questions
--------------
Legal solutions can have Legal Questions attached. Questions should relate generally to the solution provided. Questions specifically related to how the solution affects a problem should go here. For example: When am I eligible for a second bankruptcy? would go in the bankruptcy solution but Can I save my house if I file for bankruptcy would go in a foreclosure-related problem.

Related Resources
----------------------
Legal solutions can also have related resources (other legal content) attached to it just like a legal problem.


Full add/edit form
======================


.. image:: ../assets/cms-legal-solution-edit-form.png
