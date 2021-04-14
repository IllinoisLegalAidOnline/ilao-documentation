========================
Using Site Search
========================

How Search Works
==================

We apply the following filters to search:

* HTML filter to strip HTML from search queries
* Stopwords to remove stopwords from query
* Highlight to highlight the search term in the results.

Through custom code we also:

* Boost easy forms when the search term contains the word "form"
* Boost video when the search term contains "video"
* Boost a result when the content is an exact match to the best bet field

Language support
==================

The site search results are language dependent. Searching the English site for Spanish or Polish terms is likely to result in no results but searching for those terms on the Spanish or Polish search pages will generate appropriate results.

Facets (or Filters)
====================
There are 3 filters available for search:

* Content type - this lists the content types included in the search results.

.. note:: Content types use the name provided for the content type. We have multiple types of legal content (Legal content, ADRM, Portal main page)

* Primary content type:  this is applicable only to legal content and includes the content formats like How-to, Guide, Easy form

* Topic:  this is applicable to all included content types except Job postings and basic pages. This is the top level taxonomy terms. 

.. todo:: Look at cleaning up some of these content type names.

Search Results
===============

.. image:: ../assets/mobile-search.png

The search results are ordered by score descending (the score is determined by Solr). Each search result includes:

* Icon representing the content type/format. Jobs, events, and basic pages do not have icons.
* a content type label (format is used for legal content)
* Content title
* Content description, if one exists. 

.. todo::  Basic pages, job postings, and events do not have a description field.

Search Tips
============

* Using quotes requires an exact match to the phrase. For example, searching "minor offense" will return no results but searching minor offense will return Getting a ticket for a minor traffic offense, Clearing arrests for minor cannabis offenses.
* Multi-word searches are treated as OR but AND pairs will rank higher
* You can prefix + or - to better control search. For example:

  * +child +support will require the content include both the word child and the word support.
  * +child -support will require the content include the word child but not the word support.


No results
============

When no results are found, a message of "No results found" displays.

.. todo:: Consider adding a block for no results tips when no results are provided.


