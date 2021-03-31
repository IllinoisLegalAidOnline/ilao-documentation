====================
Navigational IA
====================

The Navigational IA is a simplified taxonomy for categorizing legal information. It is mono-hierarchical.  

It will be used on the website front-end in the future.  See :ref:`taxonomy-status-label` 

Taxonomy Structure
====================

Each taxonomy term has:
* a name
* a description.  This is used on subcategory and category pages.
* alternatives (these can be helpful for autocompletes)
* an icon.  This is only needed on the top level categories.  The icon is per language.
* an image.  This is used on category and subcategory pages.  The image is limited to one for all languages


Use Cases
=======================

This will be used for the front-end navigational drilldown.

curl -X PUT -H "Content-Type:application/json" -u "api_user:Ij&@D86P^Ux5qzKD" -d '{"firstName":"test","lastName":"test","eTransferOrganization
":"Chicago Legal Clinic"}' https://iloi-demo.legalserver.org/matter/api/online_intake_import 

curl -X PUT -H "Content-Type:application/json" -u api_user:Ij&@D86P^Ux5qzKD@ https://iloi-demo.legalserver.org/matter/api/online_intake_import 