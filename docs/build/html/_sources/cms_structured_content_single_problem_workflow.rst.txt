=================================
SMS Prototype for Single Problem
=================================

This documents the proposed studio flow for a single problem.


With a single problem, the flow has the UUID of the problem already.

The Studio Flow:

* Gets the problem metadata and stores it as flow variables:

  * uuid, the uuid of the Problem
  * array of subtypes
  * array of uuids of questions
  * array of attached solutions
  * array of related resources

* Get the introduction and delivers it. Each introduction segment is delivered as a separate text message.
* Gives user options to see solutions or faqs




