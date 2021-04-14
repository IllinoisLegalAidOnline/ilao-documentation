==========================
Structured Content Schema
==========================


A legal problem is the primary entity and has within it faqs and solutions. A solution may have processes (how-to) included.

Legal Problem
===============
A legal problem has:

* one or more possible solutions
* possible preventions
* faqs associated with the problems, built on the faq schema
* related resources (optionally)


Download :download:`JSON schema:  <../assets/code/structured-content.json>`
  
.. literalinclude:: ../assets/code/structured-content.json
   :language: JSON


         

References from Schema.org 
==========================

Schema.org does not have XML schema; I have adapted the applicable schema types to match and indicate parameters as required.


Question and Answer
--------------------
See: 

* https://schema.org/Answer
* https://schema.org/Question


   
How To
-------------

See 

* https://schema.org/HowTo
* https://schema.org/HowToStep
* https://schema.org/HowToSection
* https://schema.org/HowToDirection
* https://en.wikipedia.org/wiki/ISO_8601#Durations

    
Organization
---------------

See: 

* https://schema.org/Organization
* https://schema.org/ContactPoint
  
 

Order of Protection "bundle"
================================
  
This bundle validates against the proposed schema.

Download :download:`Order of protection:  <../assets/code/order-protection.json>`
  
.. literalinclude:: ../assets/code/order-protection.json
   :language: JSON



  