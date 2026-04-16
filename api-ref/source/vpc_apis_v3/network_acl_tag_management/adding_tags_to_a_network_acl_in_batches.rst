:original_name: BatchCreateFirewallTags.html

.. _BatchCreateFirewallTags:

Adding Tags to a Network ACL in Batches
=======================================

Function
--------

This API is used to add tags to a specified network ACL in batches. This is an idempotent API. When you add tags, if there are duplicate keys in the request body, an error is reported. Duplicate keys are not allowed. If a key already exists, its value will be overwritten by the new value.

URI
---

POST /v3/{project_id}/firewalls/{firewall_id}/tags/create

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+---------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                 |
   +=================+=================+=================+=============================================+
   | firewall_id     | Yes             | String          | The unique ID of a network ACL.             |
   |                 |                 |                 |                                             |
   |                 |                 |                 | The value is a string in UUID format.       |
   |                 |                 |                 |                                             |
   |                 |                 |                 | The network ACL with a given ID must exist. |
   +-----------------+-----------------+-----------------+---------------------------------------------+
   | project_id      | Yes             | String          | Project ID                                  |
   +-----------------+-----------------+-----------------+---------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------+-----------+------------------------------------------------------------------------------------+-------------+
   | Parameter | Mandatory | Type                                                                               | Description |
   +===========+===========+====================================================================================+=============+
   | tags      | Yes       | Array of :ref:`ResourceTag <batchcreatefirewalltags__request_resourcetag>` objects | Tags        |
   +-----------+-----------+------------------------------------------------------------------------------------+-------------+

.. _batchcreatefirewalltags__request_resourcetag:

.. table:: **Table 3** ResourceTag

   +-----------------+-----------------+-----------------+------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                          |
   +=================+=================+=================+======================================================+
   | key             | Yes             | String          | -  Tag key                                           |
   |                 |                 |                 |                                                      |
   |                 |                 |                 | -  Tag keys must be unique for each resource.        |
   |                 |                 |                 |                                                      |
   |                 |                 |                 | -  The value can contain 1 to 128 characters.        |
   +-----------------+-----------------+-----------------+------------------------------------------------------+
   | value           | Yes             | String          | -  Tag value.                                        |
   |                 |                 |                 |                                                      |
   |                 |                 |                 | -  The value can contain no more than 255 characters |
   +-----------------+-----------------+-----------------+------------------------------------------------------+

Response Parameters
-------------------

**Status code: 204**

Normal request response. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

None

Example Requests
----------------

Add two tags to a network ACL. For one tag, the key is **keyxxx** and the value is **value1**. The key of the other tag is **keyyyy**, and the value is **value2**.

.. code-block:: text

   POST https://{Endpoint}/v3/{project_id}/firewalls/{firewall_id}/tags/create

   {
     "tags" : [ {
       "key" : "keyxxx",
       "value" : "value1"
     }, {
       "key" : "keyyyy",
       "value" : "value2"
     } ]
   }

Example Responses
-----------------

None

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------+
| Status Code | Description                                                                             |
+=============+=========================================================================================+
| 204         | Normal request response. For more status codes, see :ref:`Status Codes <vpc_api_0002>`. |
+-------------+-----------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
