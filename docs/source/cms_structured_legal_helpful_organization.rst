.. _cms-legal-helpful-org:

================================
Structured Helpful Organization
================================

Helpful organizations can be added to structured legal content within a solution. 

.. warning:: Do not add an existing `legal organization <https://www.illinoislegalaid.org/admin/group>`_  as a helpful organization. Within a solution, you can reference existing legal organizations directly. 

What is a helpful organization?
==================================

These are organizations that do not qualify for inclusion within our organization/locations/services system but that may still be helpful to users  This might include:

* DV shelters and/or hotlines
* Social services
* Government offices

.. todo:: When to include a helpful organization in structured content should be defined as part of overall content governance.


Creating a helpful organization
=================================

To create a helpful organization:

* Enter the name of the organization as the title
* Add a short description and a meta description. The meta description will be used in the solution.
* Enter the main location of the organization
* Set the area served in the coverage area. You can add multiple administrative areas within one coverage area and/or add multiple coverage areas for different types of administrative areas
* Optionally, set an organization email
* Optionally, set an organization telephone
* Add at least one contact point
* Add any content management tags
* Indicate whether a translation should be created
* Indicate whether a translation is outdated


Contact point
----------------
A contact point is a specific set of data associated with a helpful organization that tells the user how to reach the organization. For legal organizations, this information lives in the services node.

To create a contact type:

* Add a contact type. Schema.org provides examples of Customer complaints department, sales department. For our purposes it may be: intake, help desk, navigator. 
* Set the area served. This may be different than the organization service area. For example, A contact type of "Intake" may only serve 3 counties of the 14 county service area.
* Email for the contact point, if users can contact via email
* Telephone for the contact point, if users can contact via phone
* Hours of operation
* Products supported. Schema.org defines this as "The product or service this support contact point is related to (such as product support for a particular product line). This can be a specific product or product line (e.g. "iPhone") or a general category of products or services (e.g. "smartphones")."  For our purposes, this is likely to be things like legal referrals, social service referrals, food services, financial support, housing support, utility assistance. 


.. todo:: Determine if we should actually require the location or indicate that it should not be displayed/shared.

.. todo:: Determine if we should standardize a set of contact types and products supported for use in this content.



Full add/edit form
=====================

.. image:: ../assets/cms-structured-helpful-org.png

