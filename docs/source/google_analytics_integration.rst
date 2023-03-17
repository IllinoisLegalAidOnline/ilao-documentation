====================================
Google Analytics/Google Tag Manager
====================================


Core Integration
==================

The website relies on the Google Tag Manager module to embed the appropriate container. We currently have 1 container listed on the site that feeds data into the Illinois Legal Aid Online (2016 - beyond) Google Analytics account.


Data Layer on IllinoisLegalAid.org
====================================

The default data layer includes the language being viewed, userUid, and detected zip code.

.. code-block::

   <script>window.dataLayer = window.dataLayer || []; window.dataLayer.push(
   {"drupalLanguage":"en",
   "drupalCountry":"US",
   "siteName":"Illinois Legal Aid Online",
   "userUid":"1",
   "zipcode":"60502"});
   </script>

On many pages, such as the drill-down for navigation and content pages, additional data layer elements are present by default.

Taxonomy-based pages
----------------------

Taxonomy based pages, like navigational IA pages, include:

* entityName (the name of the taxonomy term)
* entityStatus (1 for published; 0 for unpublished)
* entityUuid (the unique identifier for the taxonomy term)
* entityType (taxonomy_term)
* entityVID (vocabulary name)
* entityBundle (vocabulary name)
* entityID (taxonomy term ID)
* entityTitle (taxonomy term name)
* entityTaxonomy (object of vocabulary, term ID, term name)

.. code-block::

   <script>window.dataLayer = window.dataLayer || [];
   window.dataLayer.push(
   {"drupalLanguage":"en",
   "drupalCountry":"US",
   "siteName":"Illinois Legal Aid Online",
   "entityLangcode":"en",
   "entityName":"Divorce",
   "entityStatus":"1",
   "entityUuid":"98878af6-97e3-4107-80ad-79f8e5dbe4ac",
   "entityVid":"navigational_ia",
   "entityType":"taxonomy_term",
   "entityBundle":"navigational_ia",
   "entityId":"536576",
   "entityTitle":"Divorce",
   "entityTaxonomy":{"navigational_ia":{"536576":"Divorce"}},
   "userUid":"1"
   ,"zipcode":"60502"});</script>

Content pages
----------------

All content pages contain additional metadata. Depending on the content type, some elements may be empty.

* entityCreated - timestamp of when the content was initially created
* entityLangcode - language of the page being viewed
* entityStatus - 1 is published; 0 is unpublished
* entityUid - user ID of the author
* entittyUUid - unique id for the content
* entityVid - reversion ID
* entityName - author's name
* entityType - node
* entityBundle - content type (legal_content, legal_problem, basic_page, etc)
* entityID - Drupal Node ID
* entityTitle - Title of the content
* primary_category - for legal content, the primary top level category assigned to the content
* secondary_category - for legal content, the second level category assigned to the content
* legal_issues - an object of taxonomy terms from the legal issues taxonomy that the content is associated with.
* life_areas - an object of taxonomy terms from the life areas that COPE content is associated with
* navigational_ia - an object of taxonomy terms from the navigational IA that legal content is associated with


.. code-block::

   <script>window.dataLayer = window.dataLayer || [];
   window.dataLayer.push(
   {"drupalLanguage":"en","drupalCountry":"US",
   "siteName":"Illinois Legal Aid Online",
   "entityCreated":"1658171839",
   "entityLangcode":"en",
   "entityStatus":"1",
   "entityUid":"230971",
   "entityUuid":"4268b39b-de82-4d3d-97f8-ff6b7acf9e52",
   "entityVid":"3223801",
   "entityName":"Hannah Lee",
   "entityType":"node",
   "entityBundle":"legal_problem",
   "entityId":"176291",
   "entityTitle":"I can\u0027t pay my debts",
   "primary_category":[],
   "secondary_category":"Divorce",
   "entityTaxonomy":{"list_taxonomy":{"536181":"Bankruptcy"},
   "legal_issues":{"515706":"Money \u0026 Debt","515761":"Bankruptcy","515771":"Filing for bankruptcy","515776":"Not being able to pay my debts","515781":"A collection agency calling about my debts","515826":"Another debt issue"},
   "life_areas":{"533881":"Income"},
   "navigational_ia":{"536571":"Family \u0026 Safety","536576":"Divorce","536581":"Filing for divorce","536881":"Money \u0026 Debt","536886":"Debt collections","536896":"Bankruptcy"}},
   "userUid":"1","zipcode":"60502"});</script>





