=========================================
Integrating structured content into OTIS
=========================================

This is a work in progress. We will explain how we integrate ILAO's content chunks (structured content) into the OTIS guided navigation paths

basic concepts:

* trigger:

  * triggered by custom LegalServer field that includes: cope_option_603

* adding the element:

  * the field is added to a guided navigation path where the content needs to be displayed
  * add the node id for the legal content being called
  * instruction elements can be added to provide the user specific context to the legal content

* OTIS applicant sees:

  * Any instructions provided
  * content from the node id appears in the same theme as other guided navigation questions (without any boxes or indication that it is different that the triage questions)
  * any links provided in the content are shown to the user (i.e. link to apply for TANF benefits)
  * An instruction informing the applicant they can still continue their OTIS application
  * Continue button and Back link
