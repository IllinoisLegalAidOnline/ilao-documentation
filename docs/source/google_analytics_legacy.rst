=============================
Legacy Google Analytics Data
=============================

Legacy Google Analytics data is that data from July 1, 2017 to June 30, 2023. Earlier data is not available. Data after June 30, 2023 is part of ILAO's Google Analytics 4 profile.

Legacy data is accessible in ILAO's Tableau cloud in the `Google Analytics Legacy project <https://prod-useast-b.online.tableau.com/#/site/ilaootis/projects/638937>`_. Raw CSV files are available in ILAO's team drive:

.. warning:: Most of these files contain more rows than are supported in Excel or Google Sheets. For best results, download the file and open in Excel, do whatever filtering and totaling you need to do and do not save your changes as saving will cause data loss.

"All" files
=====================
These files only contain data where the segment was set to "in Illinois"

* GA-pages-all-2017-2020 contains pageviews data for Illinois users between July 1, 2017 - June 30, 2020
* GA-pages-all-2020-2023 contains pageviews data for Illinois users between July 1, 2020 - June 30, 2023
* GA-acquisition-all-2017-2013 contains acquisition data for Illinois users between July 1, 2017 - June 30, 2023
* GA-events-all-2017-2013 contains event data for Illinois users between July 1, 2017 - June 30, 2023
* GA-search-all-2017-2013 contains search data for Illinois users between July 1, 2017 - June 30, 2023

Illinois files
=====================
These files only contain data where the segment was set to "in Illinois"

* GA-pages-IL-2017-2020 contains pageviews data for Illinois users between July 1, 2017 - June 30, 2020
* GA-pages-IL-2020-2023 contains pageviews data for Illinois users between July 1, 2020 - June 30, 2023
* GA-acquisition-illinois-2017-2013 contains acquisition data for Illinois users between July 1, 2017 - June 30, 2023
* GA-events-illinois-2017-2013 contains event data for Illinois users between July 1, 2017 - June 30, 2023
* GA-search-illinois-2017-2013 contains search data for Illinois users between July 1, 2017 - June 30, 2023

To reduce file size, data is aggregated by month in all categories.

Data Structures
================

Pageviews
------------

Pageviews data includes:

* Date - the month/year of the pageviews.
* Device category - mobile, desktop, or tablet
* Medium
* Page - the page path being viewed
* Previous page path - the page path the individual previously accessed.
* Source
* Bounces
* Entrances
* Exits
* Page Depth
* Pageviews
* Session duration
* Sessions
* Unique page views

There are 4 different data sets due to the amount of traffic ILAO receives.

Events
--------
Events data source includes:

* Date - the month/year of the event
* Device category
* Event Category - the broad category of the event (download, outbound link, telephone link, etc)
* Event action - print, click, etc
* Event label - label defined by ILAO to track. For outbound links, it is the URL.
* Page - the page where the event occurred
* Sessions with event - number of sessions with the specific event
* Total events - total number of events
* Unique events  - total number of unique event/user pairs.

Total events vs unique events: User A clicks the same link 5 times in a session. That is 5 total events but 1 unique event.

Acquisition
-------------

The acquisition data source includes:

* Date - the month/year of the event
* Default channel grouping
* Device category
* Medium
* Source
* Bounces
* New Users
* Pageviews
* Sessions
* Users

Search
--------

The search data source includes:

* Date - the month/year of the event
* Default channel grouping
* Device category
* Search destination
* Search term
* Source / medium
* Start page
* Search depth
* Search exits
* Search refinements
* Sessions with search
* Time after Search
* Total unique searches


