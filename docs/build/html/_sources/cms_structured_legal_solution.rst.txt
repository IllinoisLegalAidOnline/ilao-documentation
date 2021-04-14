.. _cms-legal-solution:

==============================
Legal Solution
==============================

A legal solution is tied to one or more legal problems (see :ref:`cms-legal-problem`) and features:

* content metadata
* a solution type
* 0 or more :ref:`cms-legal-forms`
* 0 or more pieces of needed information 
* Legal difficulty (optional)
* Estimated time required to complete the entire process
* One or more eligibility rules to be able to use a specific solution
* A jurisdiction
* Zero or more helpful organizations
* Zero or more legal organizations
* One or more HowTos
* A result

.. todo:: Determine if we should have information needed when we have tools/supplies in the how-to; This is especially important if the information needed might vary at a local level. How Tos should be required.

Solution type
=================

A solution type are defined by our `solution types taxonomy <https://www.illinoislegalaid.org/admin/structure/taxonomy_manager/voc/solution_types>`_.


Eligibility rules
===================
Eligibility rules use the :ref:`cms-structured-text` block. Each eligibility rule should have its own structured text block.

Examples
----------
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
================
Structured content supports jurisdiction across different pieces of data. See :ref:`cms-coverage-area` documentation. A solution may have a jurisdiction that is broader than an attached How-to, attached legal forms, or attached organization. A solution, even if it has How-tos that vary by location or forms that apply only to some jurisdictions, can still be marked at a broader jurisdiction so long as:

* the eligibility rules apply to the solution jurisdiction
* the legal difficulty varies by location
* the result varies by location  

.. note:: Example:  The steps for getting an order of protection are different in Cook county than in the rest of the states. McHenry county requires a specific form that no one else does. But the eligibility rules, difficulty, and result is the same across Illinois. The solution should be set to Illinois while there should be 2 How-tos (one for Cook county, one for the other 101 counties), and the McHenry form should be specificially tagged to McHenry county.

Legal organization vs Helpful organization
===========================================

Solutions support both :ref:`cms-legal-helpful-org` and legal organizations.

A helpful organization is one that exists as a structured helpful organization. 

Structured helpful organizations have much less information in our system. These are organizations that do not belong in our organization system but that may still be helpful to users  This might include:

* DV shelters and/or hotlines
* Social services
* Government offices

A legal organization is one that exists in `ILAO's organization system <https://www.illinoislegalaid.org/admin/group>`_. Rather than replicate the data as a structured helpful organization, these can be referenced directly as needed in the legal organization field.

Result
==========

The result also uses the structured text block. A result should describe the outcome when a solution is completed. It should be broken down to best support delivery across channels. 

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
    


Full add/edit form
======================


.. image:: ../assets/cms-legal-solution-edit-form.png