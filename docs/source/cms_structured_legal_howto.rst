.. _cms-legal-howto:

======================
Legal How-To
======================

A legal how-to is a container made up of:

* standard content metadata
* time information
* steps
* supplies
* tools
* jurisdiction

It is attached to one or more Legal solutions. See the :ref:`cms-legal-solution` documentation.

Times
=========
A How-to requires three time entries:

* prep time:  the estimated amount of time it takes to prepare to complete the how-to. This time should the time to prepare the materials used to execute the How-to. This should include the time to:

  * Gather background documents and materials

* perform time:  the estimated amount of time it takes to perform the how-to. This should include time for:

  * Filling out forms
  * Wait time from filing to having a hearing
  * Wait time from having a hearing to resolution
  
* Total time should be the sum of the prep + perform time. 

Time format
-------------

Times use the standard `duration format <https://en.wikipedia.org/wiki/ISO_8601>`_.

Standard format:  P(n)Y(n)M(n)W(n)D(n)T(n)H(n)M(n)S)
P, followed by the number for each:

* Years (Y)
* Months (M)
* Weeks (W)
* Days (D)

T, followed by the number for each:

* Hours (H)
* Minutes (M)
* Seconds (S)
  
Examples:

* 2 weeks: P2W  
* 1 year, 3 months, 6 days: P1Y3M6D
* 3 days, 14 hours, 5 minutes: P3DT14H5M
* 6 hours: PT6H

.. todo:: Help text for duration is missing W(n)D(n).

Step sections
===============

Step lists can be created in sections. A how-to may have a single linear steps section or may have multiple step sections. 

.. note::  An example how-to for washing a car may have a step section labeled "Option 1:  Take it the car washing service" and "Option 2:  Hand wash in the driveway."  Even linear, but complex How-tos may benefit from sections. For example, in applying for unemployment, it may make sense to have a Step section "Determine if you are eligible" with steps of Determine whether the reason you no longer have a job is eligible, determine whether you have sufficient earnings to be eligible. 

Each section should have:

* A heading or title. This can be set to display or not display. For how-to's with one step section, this should be set to not display.
* One or more steps. These are entity references to legal step content. The step must be written before it can be included.

Supplies, tools, & yield
=========================

Supplies and tools should be entered one at a time.

A supply is something needed to complete the steps in the how-to. Supply examples might be:

* an ID or driver's license
* a birth certificate
* a marriage license

A tool is something used to complete the steps in the how-to. Tool examples might be:

* a telephone
* a pen
* an email address for e-filing.

Yield is likely not applicable but is part of the standard. It's used to indicate a quantity that results by performing instructions (and in Schema is most often used in recipes).

Jurisdiction
===============

Each how-to should be coded to the jurisdiction(s) it applies to. See :ref:`cms-coverage-area`. A :ref:`cms-legal-solution` can have multiple how-tos, each with different jurisdictions. Individual steps are not tagged by jurisdiction.

For example:

*  Getting an order of protection solution could have 102 how-tos, one for each county. Each how-to could contain then same 8 steps but step 9 is specific to that county.


.. todo::  Should individual steps be tagged to jurisdiction?


Full add/edit form
====================

.. image:: ../assets/cms-structured-legal-howto.png

