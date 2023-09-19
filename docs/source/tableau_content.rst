===============================
Content metrics in Tableau
===============================

Data Sources
================

Static sources
-----------------
These sources rarely change but are used in data cleanup:

* Navigational_IA export file which contains the term IDs and names of the second level naviational categories
* Categories export file which contains the term IDs and names of the top level navigational categories
* Content type export file which contains the English language content format names and term ids

Legal Content Flow
---------------------

The Legal content flow relies on:

* an exported CSV from "Find Legal Content"
* the navigational_ia export to replace primary and secondary legal term IDs with their English language names
* the categories export
* the content_format export to replace the content type in Legal Content with the name of the format, in English, instead of the term ID

.. note:: Should edit find legal content report to display publish status and support Any as a filter option

When processed through the Prep Builder, the resulting file is a data structure as follows:

+------------------------------+----------------------------------+--------------------+
| Column                       | Description                      |  Type              |
+==============================+==================================+====================+
| ID                           | Node ID                          | Number             |
+------------------------------+----------------------------------+--------------------+
| Title                        | English content title            | String             |
+------------------------------+----------------------------------+--------------------+
| Content type                 | Drupal content type              | String             |
+------------------------------+----------------------------------+--------------------+
| Created                      | Date content was created         | Date               |
+------------------------------+----------------------------------+--------------------+
| Last changed                 | Last time the content was changed| Date               |
|                              | in any way                       |                    |
+------------------------------+----------------------------------+--------------------+
| Last substantive revision    | Date the content was revised in  | Date               |
|                              | a substantive way, as determined |                    |
|                              | by the content team              |                    |
+------------------------------+----------------------------------+--------------------+
| Last expert view             | Date the content was last        | Date               |
|                              | reviewed by a SME                |                    |
+------------------------------+----------------------------------+--------------------+
| Language                     | The language of the content      | String             |
+------------------------------+----------------------------------+--------------------+
| Full url                     | Full website url to content      | String             |
+------------------------------+----------------------------------+--------------------+
| Page path                    | page path of the content         | String             |
+------------------------------+----------------------------------+--------------------+
| Subtopic                     | Level 2 taxonomy term, in English| String             |
+------------------------------+----------------------------------+--------------------+
| Category                     | Primary category, in English     | String             |
+------------------------------+----------------------------------+--------------------+
| Content format               | Name of content format           | String             |
+------------------------------+----------------------------------+--------------------+

Google Analytics Page Views Flow
-----------------------------------

The Google Analytics flow merges a subset of Google Analytics data to be able to create reports that use page view data. This flow relies on:

* CSV files exported from universal analytics from January 1, 2017 - June 30, 2023
* An API call to Google Analytics 4 with data from July 1, 2023 - forward

It produces a Tableau file that merges and cleans up the data into a single set of metrics that are available in both Universal Analytics and GA4.

+------------------------------+----------------------------------+--------------------+
| Column                       | Description                      |  Type              |
+==============================+==================================+====================+
| eventDate                    | Date page was viewed             | Date               |
+------------------------------+----------------------------------+--------------------+
| engagementRate               | GA4 only                         | Number             |
+------------------------------+----------------------------------+--------------------+
| bounceRate                   | GA4 only                         | Number             |
+------------------------------+----------------------------------+--------------------+
| deviceCategory               | desktop, mobile, or tablet       | String             |
+------------------------------+----------------------------------+--------------------+
| sessionMedium                | medium used (display, email, cpc | String             |
|                              | organic)                         |                    |
+------------------------------+----------------------------------+--------------------+
| sessionSource                | Direct, referral domain, etc     | String             |
+------------------------------+----------------------------------+--------------------+
| pagePath                     | Path of the page accessed,       | String             |
|                              | without hostname                 |                    |
+------------------------------+----------------------------------+--------------------+
| pageReferrer                 | URL of the previous page         | String             |
+------------------------------+----------------------------------+--------------------+
| screenPageViews              | Number of page views             | Number             |
+------------------------------+----------------------------------+--------------------+
| sessions                     | Number of sessions               | Number             |
+------------------------------+----------------------------------+--------------------+
| Unique pageviews             | Number of unique pageviews       | Number             |
+------------------------------+----------------------------------+--------------------+
| Bounces                      | Universal analytics only         | Number             |
+------------------------------+----------------------------------+--------------------+

Content Revisions Flow
-------------------------

This flow takes data from our `Content Revisions <https://www.illinoislegalaid.org/admin/reporting/content/legal-revisions>`_ report exported to CSV.

It produced a cleaned up data file that can be used to track revision activity, including number of SME reviews, substantive updates, and can be tied back to data in the legal content flow on tne node ID.


+------------------------------+----------------------------------+--------------------+
| Column                       | Description                      | Type               |
+==============================+==================================+====================+
| Node ID                      | Node of the content revised      | Number             |
+------------------------------+----------------------------------+--------------------+
| Revision ID                  | Unique identifier of the revision| Number             |
+------------------------------+----------------------------------+--------------------+
| SME date                     | Date of the last SME review, at  | Date               |
|                              | the time of the revision         |                    |
+------------------------------+----------------------------------+--------------------+
| Staff revised date           | Date of the last staff revision, | Date               |
|                              | at the time of the revision      |                    |
+------------------------------+----------------------------------+--------------------+
| Revision saved               | Date the revision was created    | Date               |
+------------------------------+----------------------------------+--------------------+
| Revision log message         | Message entered when revision    | String             |
|                              | was created                      |                    |
+------------------------------+----------------------------------+--------------------+
| Language                     | Language associated with the     | String             |
|                              | revision                         |                    |
+------------------------------+----------------------------------+--------------------+
| Revision author              | Name of the person who created   | String             |
|                              | the revision                     |                    |
+------------------------------+----------------------------------+--------------------+





