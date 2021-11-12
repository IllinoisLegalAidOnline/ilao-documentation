.. _taxonomy-status-label:

==========================
Legal taxonomies status
==========================

This is accurate as of November 2021.


The legal issues taxonomy:

* is used to tag legal content at a granular legal issue
* the top 2 levels are used as navigation within the website

The navigational IA:
* Has terms created
* All legal content has been updated to use it.


Best practices
================

* Tag the content to the best category you can find. One is the goal - only tag multiple categories if the content truly fits both places.

* If you tag a piece of content to a taxonomy tag that starts with "another" or "other," **do not tag that piece of content to any other taxonomy tags**


Next steps
=============


We envision that we will use the `navigational IA taxonomy <https://www.illinoislegalaid.org/admin/structure/taxonomy_manager/voc/navigational_ia>`_ for navigating the website by mid-2022.

In order to do this, we must:

* Add translations for Spanish and Polish

* Populate the navigational IA taxonomy with our revised legal issues taxonomy (content) This will include for each language (English, Spanish, and Polish):

	* Copying definitions
	* Copying any alternates
	* Copying icons
	* Copying images

* Implement changes to our front end:

  * Remove existing path aliases so that they can be re-used (Gwen)
  * Update navigational IA to use the current legal issues taxonomy (Gwen)
  * Update category, subcategory, forms, practice resources to use new taxonomy (developers)
  * Re-run sitemaps (Gwen)


.. note:: We will continue to tag content to both taxonomies as Get Legal Help relies heavily on the depth of the legal issues taxonomy and some relationships between content also use this information.
