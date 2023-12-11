================================
Automated Helpful Organizations
================================

With custom tools, helpful organizations can be automatically brought in and displayed in the appropriate places.

For each automation, a scheduled task will bring in and update data on a regular basis.

Housing Counselors
======================
We utilize housing counselor data from the Consumer financial protection bureau. This data is accessible via JSON files that are stored on that site and are available at:

https://files.consumerfinance.gov/a/assets/hud/jsons/" + zip + ".json";
where zip is the relevant zip code

https://files.consumerfinance.gov/a/assets/hud/jsons/60505.json for example.

Each json file contains:

* 2 objects: zip and counseling_agencies
* zip object contains:

  * zipcode (the 5 digit zip code)
  * lat (the latitude of the zip code)
  * lng (the longetiude of the zip code)

* counseling_agencies object contains an array of organizations. The mapping below shows how ILAO maps these agencies to our helpful organizations content types.

Unless otherwise noted, the JSON element is at counseling_agencies[i]

+--------------------------------------+----------------------------------------------+
|  Helpful organization field          | JSON element                                 |
+======================================+==============================================+
| Title                                | .nme                                         |
+--------------------------------------+----------------------------------------------+
| Content description                  | Hardcoded text                               |
+--------------------------------------+----------------------------------------------+
| Meta description                     | Hardcoded text                               |
+--------------------------------------+----------------------------------------------+
| Location - street address            | .mailingadr1                                 |
+--------------------------------------+----------------------------------------------+
| Location - city                      | .mailingcity                                 |
+--------------------------------------+----------------------------------------------+
| Location - state                     | .mailingstatecd                              |
+--------------------------------------+----------------------------------------------+
| Location - postal code               | .mailingadrzipcd                             |
+--------------------------------------+----------------------------------------------+
| Area served - admin area             | Zip Codes                                    |
+--------------------------------------+----------------------------------------------+
| Area served - zip code               | zip.zipcode                                  |
+--------------------------------------+----------------------------------------------+
| Email                                | .email                                       |
+--------------------------------------+----------------------------------------------+
| Telephone                            | .phone1                                      |
+--------------------------------------+----------------------------------------------+
| Contact - contact type               | "Housing counseling"                         |
+--------------------------------------+----------------------------------------------+
| Contact - area served                |                                              |
+--------------------------------------+----------------------------------------------+
| --Admin area                         | Zip Codes                                    |
+--------------------------------------+----------------------------------------------+
| --Zip codes                          | zip.zipcode                                  |
+--------------------------------------+----------------------------------------------+
| Contact - email                      | .email                                       |
+--------------------------------------+----------------------------------------------+
| Contact - telephone                  | .phone1                                      |
+--------------------------------------+----------------------------------------------+
| Contact - hours                      | null                                         |
+--------------------------------------+----------------------------------------------+
| Contact - products supported         | .services (this is an array; each item       |
|                                      | should be added separately)                  |
+--------------------------------------+----------------------------------------------+
| Languages                            | .languages (this is an array; each item      |
|                                      | should be added separately)                  |
+--------------------------------------+----------------------------------------------+
| Source                               | "ConsumerFinanceHousingCounselors"           |
+--------------------------------------+----------------------------------------------+
| Navigational IA                      |  If proudcts supported includes "Rental      |
|                                      |  housing counseling," being evicted; if      |
|                                      |  includes any term with mortgage delingquency|
|                                      |  then "foreclosure of a home I own"          |
+--------------------------------------+----------------------------------------------+
| Website                              | .website                                     |
+--------------------------------------+----------------------------------------------+

Hard-coded content and meta description: Housing counselors approved by HUD offer free or low cost independent advice on renting, foreclosures, and other housing and credit issues.



Domestic Violence Agencies
============================

We built a scrapper that pulls in the list of domestic violence organizations from the IDHS website.

+--------------------------------------+----------------------------------------------+
|  Helpful organization field          | Stores                                       |
+======================================+==============================================+
| Title                                | Organization name                            |
+--------------------------------------+----------------------------------------------+
| Description                          | Scrapped description                         |
+--------------------------------------+----------------------------------------------+
| Location - street address            | Scrapped street address                      |
+--------------------------------------+----------------------------------------------+
| Location - city                      | Scrapped city                                |
+--------------------------------------+----------------------------------------------+
| Location - state                     | Illinois                                     |
+--------------------------------------+----------------------------------------------+
| Location - postal code               | Scrapped zip code                            |
+--------------------------------------+----------------------------------------------+
| Area served - admin area             | County                                       |
+--------------------------------------+----------------------------------------------+
| Area served - zip code               | Scrapped county                              |
+--------------------------------------+----------------------------------------------+
| Email                                | not available                                |
+--------------------------------------+----------------------------------------------+
| Telephone                            | Scrapped phone                               |
+--------------------------------------+----------------------------------------------+
| Contact - contact type               | "Government"                                 |
+--------------------------------------+----------------------------------------------+
| Contact - area served                |                                              |
+--------------------------------------+----------------------------------------------+
| --Admin area                         | County                                       |
+--------------------------------------+----------------------------------------------+
| --Counties                           | Scrapped county                              |
+--------------------------------------+----------------------------------------------+
| Contact - email                      | not available                                |
+--------------------------------------+----------------------------------------------+
| Contact - telephone                  | Scrapped phone                               |
+--------------------------------------+----------------------------------------------+
| Contact - hours                      | null                                         |
+--------------------------------------+----------------------------------------------+
| Contact - products supported         | hard coded to Crisis support, Counseling,    |
|                                      | Safety planning                              |
+--------------------------------------+----------------------------------------------+
| Languages                            | not available                                |
+--------------------------------------+----------------------------------------------+
| Source                               | "DVagencies"                                 |
+--------------------------------------+----------------------------------------------+
| Navigational IA                      | Safety planning, Restraining orders          |
+--------------------------------------+----------------------------------------------+
| Website                              | Scrapped website url                         |
+--------------------------------------+----------------------------------------------+




