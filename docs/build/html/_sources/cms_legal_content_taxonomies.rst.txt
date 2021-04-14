.. _taxonomy-status-label:

==========================
Legal taxonomies status
==========================

As of January 2021, the legal issues taxonomy:

* is used to tag legal content at a granular legal issue 
* the top 2 levels are used as navigation within the website

We envision that we will use the `navigational IA taxonomy <https://www.illinoislegalaid.org/admin/structure/taxonomy_manager/voc/navigational_ia>`_ for navigating the website by the end of 2021. 

In order to do this, we must:

* Populate the navigational IA taxonomy with our revised legal issues taxonomy (content) This will include for each language (English, Spanish, and Polish):

	* Copying terms
	* Copying definitions
	* Copying any alternates
	* Copying icons
	* Copying images
	
* Add a field to all forms of legal content to tag content to the navigational IA (developers)
* Create a report that shows all legal content that does not have navigational IA terms (developers)
* Update all of our legal content (content) to add the new tags (content)
* Implement changes to our front end:

  * Remove existing path aliases so that they can be re-used (Gwen)
  * Update navigational IA to use the current legal issues taxonomy (Gwen)
  * Update category, subcategory, forms, practice resources to use new taxonomy (developers)
  * Re-run sitemaps (Gwen)




.. note:: For the immediate future, we will continue to tag content to both taxonomies as Get Legal Help relies heavily on the depth of the legal issues taxonomy and some relationships between content also use this information.
