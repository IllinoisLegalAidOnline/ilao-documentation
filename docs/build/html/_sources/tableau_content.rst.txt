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




