=============================
Structured Content Overview
=============================

Structured legal content is designed to offer a way of delivering legal information across channels, whether it be the web, SMS, chatbots, or voice services. It is structured to be problem/solution-focused.

Every problem in our structured content:

* has a description of the problem
* may have one or more questions that help more fully describe the problem. Each question:

  * has an accepted answer
  * may have suggested answers
  * has a jurisdiction associated

* has one or more defined possible solutions that offers:

  * Step-by-step instructions to solve the problem. Each step section:

    * Includes one or more steps
    * An optional title
    * Each step consists of one or more directions or tips

  * Eligibility information for the solution
  * Information needed to complete the solution
  * Any helpful organizations that may be relevant
  * Forms needed to complete the solution. This includes:

    * The name of the court form
    * What the form is filled out with (name, type of program, link)
    * Jurisdiction
    * When it may or may not be used (optional)

  * Jurisdiction applicable to the solution.
  * Expected result from completing the solution. This may include segments of text and/or structured lists.

* May have a primary and secondary prevention solutions, which are based on the same solution structure
* May have related resources

.. note::
   We've stored jurisdiction data on questions, steps, how-tos, forms, and solutions which allows us to tailor responses based on the user's location. There are 2 jurisdiction fields available:

   * Jurisdiction - this is required
   * Negate jurisdiction - this is optional and is used to exclude an area from the jurisdiction (for example, to set something to "all but Cook county", you can set the jurisdiction to Illinois and the negate jurisdiction to Cook county).

   Examples:
   * Content applies the same statewide, then the negate jurisdiction field would not be used and the jurisdiction would be set to State - Illinois.
   * Content applies differently in Cook county, there would be two pieces of content:

     * Content A would be set to a jurisdiction of Cook; this step would not be delivered for users outside of Cook county.
     * Content B would be set to a jurisdiction of Illinois and a negate jurisdiction of County = Cook; this step would not be delivered for users inside Cook county.

  * Content applies statewide and another step applies just in Cook County (except Chicago), and another applies just in Chicago:

    * The statewide step would be tagged to Illinois and no negate jurisdiction set
    * The Cook county step would be tagged to County = Cook with a negate jurisdiction of city = Chicago
    * The Chicago step would be tagged to city = Chicago
    * A Chicago user would see the Chicago and statewide step; A suburban Cook county user would see the Cook step and the statewide step. All other users would get the statewide step only.


Content formats
=================

We have defined two key formats for text-based markup:

* the list format.
* a structured text format

Both formats rely on the "paired content markup" that translates HTML text into plain text with footnoted urls, which will work better on non-web channels.





