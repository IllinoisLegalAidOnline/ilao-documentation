.. _cms-legal-step:

===================
Legal Step
===================

Legal steps are part of a :ref:`cms-legal-howto` which are part of a :ref:`cms-legal-solution`. 

A step is composed of 1 or more directions and 0 or more tips.

.. note:: Legal steps can be re-used in multiple how-tos. 

Direction vs Tip
==================

A direction is "A direction indicating a **single** action to do in the instructions for how to achieve a result."

A tip is "An explanation in the instructions for how to achieve a result. It provides supplementary information about a technique, supply, author's preference, etc. It can explain what could be done, or what should not be done, but doesn't specify what should be done."  What should be done is a direction.

For example, the step "Move out and clean the apartment" might have:

* a Direction of "Move all of your items from the unit."
* a Direction of "Clean the unit thoroughly"
* a Tip of "This includes all floors and surfaces, the refrigerator, the freezer, the oven, and all bathrooms."
* a Direction of "Check the written lease, if there is one, to make sure you have followed all of the instructions for moving out."

Bulleted lists
===================
Bulleted lists are not supported within a Direction or Tip as direction and tips are themselves list items within a step. 

Return all of the keys to the landlord right after you move. If you do not, the landlord may charge you. If you return the keys to a leasing office, have the landlord write up a receipt acknowledging that the keys have been returned. If you are returning keys by mail, send the keys with a tracking number and keep that tracking number for your records. 

This could be structured as:

* A Direction of "Return all of the keys to the landlord right after you move."
* A Tip of "If you do not, the landlord may charge you."
* A Direction of "Get proof that you returned the keys."
* A Tip with 2 body elements of "If you return the keys to a leasing office, have the landlord write up a receipt acknowledging that the keys have been returned."and "If you are returning keys by mail, send the keys with a tracking number and keep that tracking number for your records."

This might render on the web as:

1. Return all of the keys to the landlord right after you move. If you do not, the landlord may charge you. 
2. Get proof that you returned the keys. If you return the keys to a leasing office, have the landlord write up a receipt acknowledging that the keys have been returned. If you are returning keys by mail, send the keys with a tracking number and keep that tracking number for your records.

and over SMS may be:

* Segment 1:  Return all of the keys to the landlord right after you move. 
* Segment 2:  Tip:  If you do not, the landlord may charge you. Reply N for the next direction
* Segment 3:  Get proof that you returned the keys.
* Segment 4:  Tip:  If you return the keys to a leasing office, have the landlord write up a receipt acknowledging that the keys have been returned.
* If you are returning keys by mail, send the keys with a tracking number and keep that tracking number for your records.

Creating or editing a step
============================
Every step:

* must have a title; this  
* should have a content description
* should have a meta description
* should have one or more legal issues
* should have a primary legal category
* one or more step blocks (see below)
* should have a legal position
* may have an annual update selection
* may have an author/SME 
* may request a translation
* may mark translation as outdated

.. note:: While content description, meta description, legal issues, primary legal category, and legal position are not technically required, we recommend including them for future-proofing and filtering/reporting purposes.

Step block
--------------
A  step block consists of:

* a type (direction or tip)
* one or more body elements, using :ref:`cms-paired-markup`. Using multiple body elements allows us to better segment content over non-web channels. 
* reference URLS (links within the content)

.. todo:: Determine whether the metadata fields should be required, whether last revised/reviewed dates should be added (or is at the how-to level sufficient) and whether we need the referenceUrls field (those were added before we had paired markup).




Full add/edit step form
==========================


.. image:: ../assets/cms-legal-step-edit.png