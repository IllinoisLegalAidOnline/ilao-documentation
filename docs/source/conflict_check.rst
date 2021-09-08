========================
Conflict API
========================

The conflict check API is accessible at https://[site].legalserver.org/api/v1/conflict_check and request basic authorization from the specific instance of Legal Server

Example JSON body
====================


.. code-block:: json

   {
  "first": "string",
  "middle": "string",
  "last": "string",
  "dob": "2020-10-15",
  "visa_number": "string",
  "phones": [
    {
      "number": "555-555-5555, 5555555555, (555) 555-5555",
      "type": "business"
    }
  ]
 }


Example call using Axios Node.js
==================================

.. code-block:: json

   var axios = require('axios');
   var data = JSON.stringify({
  "first": "string",
  "middle": "string",
  "last": "string",
  "dob": "2020-10-15",
  "visa_number": "string",
  "phones": [
    {
      "number": "555-555-5555, 5555555555, (555) 555-5555",
      "type": "business"
    }
  ]
  });

  var config = {
  method: 'post',
  url: 'https://legalaidchicago-demo.legalserver.org/api/v1/conflict_check',
  headers: {
    'Content-Type': 'application/json'
  },
  data : data
  };

  axios(config)
  .then(function (response) {
  console.log(JSON.stringify(response.data));
  })
  .catch(function (error) {
  console.log(error);
  });


Sample responses
=================

Lowest score example:

.. code-block:: json

   {
  "status": 200,
  "message": "conflict check completed successfully",
  "interval": "lowest",
  "score": 17
  }

Highest score example:

.. code-block:: json

   {
    "status": 200,
    "message": "conflict check completed successfully",
    "interval": "highest",
    "score": 100
  }

