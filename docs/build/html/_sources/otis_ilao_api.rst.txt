============================
ILAO OTIS API
============================

Status
========


Permissions
=============
 

.. todo:: Understand how the authentication that was created works.

Triage User
=============

Get Triage User(s)
--------------------
Triage user API supports GET commands to return one or more existing triage users.


.. code-block:: php
   
    GET /jsonapi/oas_triage_user/oas_triage_user?page[limit]=
    GET /jsonapi/oas_triage_user/oas_triage_user/{{uuid}} returns a specific triage user
    GET /jsonapi/oas_triage_user/oas_triage_user?sort=-changed returns the newest 
    GET /jsonapi/oas_triage_user/oas_triage_user?filter[county]=Cook&filter[intake_status]=etransferred
    
  
Create Triage User
---------------------

.. code-block:: json

    curl -X POST -H "Content-Type:application/vnd.api+json" -d '{
  "data": {
        "type": "oas_triage_user--oas_triage_user",
        "attributes": {
            "status": true,
            "intake_created": "1970-01-01T00:00:00+00:00",
            "intake_changed": "1970-01-01T00:00:00+00:00",
            "household_size": 5,
            "household_adults": 2,
            "household_children": 3,
            "total_income": 0,
            "total_expenses": 0,
            "total_assets": 0,
            "zip_code": "60603",
            "triage_status": "Started",
            "intake_status": null,
            "lsc_code": null,
            "lsc_subcode": null,
            "referral_source": null,
            "county": "Cook",
            "state": "Illinois",
            "ip_address": "10.159.81.163",
            "last_screen_viewed": null,
            "intake_notes": null,
            "gender": null,
            "race": null,
            "ethnicity": null,
            "marital_status": null,
            "citizenship": null,
            "immigrant_status": null,
            "age": null,
            "primary_language": null,
            "country_of_origin": null,
            "overincome": null,
            "etransfer_attempts": 0,
            "etransfer_failure_reason": null,
            "etransfer_status": null,
            "etransfer_data": {
                "": ""
            },
            "hourly_reminder_sent": null,
            "daily_reminder_sent": null,
            "default_langcode": true,
            "oas_mobile_phone": null,
            "oas_opt_in_sms": null,
            "oas_triage_callback_times": [],
            "oas_triage_help_type": [
                "forms"
            ],
			"oas_triage_search": "Child custody"
        },
        "relationships": {
            "oas_triage_user_type": {
                "data": {
                    "type": "oas_triage_user_type--oas_triage_user_type",
                    "id": "ba7bab21-7cdf-4e07-990d-94fda9655f64"
                }
            },
                      "intake_organization": {
                "data": {
                    "type": "oas_intake_settings--oas_intake_settings",
                    "id": "19f38f98-93f2-4209-adaf-608fd97bb530"
                }
            },
            "oas_limited_populations": {
                "data": []
            },
            "oas_triage_problem": {
                "data": {
                    "type": "taxonomy_term--legal_issues",
                    "id": "7e7404dd-49c1-4261-9c5a-acc1fab27dde"
                }
            },
            "oas_triage_problem_history": {
                "data": []
            }
        }
    }
   }' http://ilaodrupal8.prod.dd:8083/jsonapi/oas_triage_user/oas_triage_user


    curl -X POST -H "Content-Type:application/vnd.api+json" -d '{
  "data": {
        "type": "oas_triage_user--oas_triage_user",
        "attributes": {
            "status": true,
            "intake_created": "1970-01-01T00:00:00+00:00",
            "intake_changed": "1970-01-01T00:00:00+00:00"}}}' http://ilaodrupal8.prod.dd:8083/jsonapi/oas_triage_user/oas_triage_user
            
            
Update triage user
---------------------

 curl -X PATCH -H "Content-Type:application/vnd.api+json" -d '{
  "data": {
        "type": "oas_triage_user--oas_triage_user",
        "id": "e08ff647-362f-4428-bcaf-8b45191a8df7",
        "attributes": {
            "household_size": 6,
            "household_children": 4
        }
    }
}' http://ilaodrupal8.prod.dd:8083/jsonapi/oas_triage_user/oas_triage_user/e08ff647-362f-4428-bcaf-8b45191a8df7
            
Delete triage user
---------------------
            
   curl -X DELETE http://ilaodrupal8.prod.dd:8083/jsonapi/oas_triage_user/oas_triage_user/e08ff647-362f-4428-bcaf-8b45191a8df7          
            
 
Taxonomies 
============          
      curl -X GET -H "Content-Type:application/vnd.api+json" http://ilaodrupal8.prod.dd:8083/jsonapi/taxonomy_term/oas_marital_status    
