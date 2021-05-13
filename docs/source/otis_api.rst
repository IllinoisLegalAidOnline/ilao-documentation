=========================
Online triage/intake API
=========================

Our Online triage and intake API offers functionality to interact with:

* triage user data
* intake settings

Triage users
================

Get Triage User
------------------

cURL example:  

.. code-block:: 

   curl --location --request GET 'https://www.illinoislegalaid.org/jsonapi/oas_triage_user/oas_triage_user' \ 
   --header 'Authorization: Bearer [your-token-here]'
  
By default, this will return one or more triage users.  Filters are supported to get targeted users. 

Example filters:

* adding ?filter[drupal_internal__id]=6 will return the triage user record with a triage_id of 6
* adding ?filter[foo][condition][value]=Cook&filter[foo][conditon][operator]=%3D&filter[foo][condition][path]=county will return all triage users with a county of Cook

Create Triage User
--------------------

Update Triage User
---------------------


   
   
   


