====================
LCV Dashboard
====================

User profile data
====================
The website should store as part of the user's profile:

* the current total number of points earned
* the badges earned with the date the badge was earned
* the current total number of words captured
* the current total number of articles captured
* this quarter totals
* last quarter totals
* current month streak number

These fields should not be visible to users in their regular profile.

.. todo:: We need to determine what a quarter is (Jan-Mar, Apr -Jun, Jul -Sept, Oct -Dec or rolling basis [current month - 2. current month -2 to current month - 5])

System Tasks
==============
To generate content for the dashboard, the following scheduled tasks must be executed daily:

* a daily task to award badges
* a daily task to update totals.  We don't want to have to manually update the data every time the page is viewed (technically similar to the voting API module)
* monthly task to update streak


.. todo:: Number format (commas or no commas)


