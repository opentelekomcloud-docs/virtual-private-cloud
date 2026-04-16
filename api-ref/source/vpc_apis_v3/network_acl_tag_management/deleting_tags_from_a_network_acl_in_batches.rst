:original_name: BatchDeleteFirewallTags.html

.. _BatchDeleteFirewallTags:

Deleting Tags from a Network ACL in Batches
===========================================

Function
--------

This API is used to delete tags from a specified network ACL in batches. This is an idempotent API. If some tags to be deleted do not exist, the deletion is considered to be successful by default. The character set of the tags will not be checked. When you delete tags, the tag structure cannot be missing, and the key cannot be left blank or be an empty string.

URI
---

POST /v3/{project_id}/firewalls/{firewall_id}/tags/delete

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

   +-----------+-----------+----------------------------------------------------------------------------------------------------------------------+-------------+
   | Parameter | Mandatory | Type                                                                                                                 | Description |
   +===========+===========+======================================================================================================================+=============+
   | tags      | Yes       | Array of :ref:`DeleteResourceTagRequestBody <batchdeletefirewalltags__request_deleteresourcetagrequestbody>` objects | Tags        |
   +-----------+-----------+----------------------------------------------------------------------------------------------------------------------+-------------+

.. _batchdeletefirewalltags__request_deleteresourcetagrequestbody:

.. table:: **Table 3** DeleteResourceTagRequestBody

   +-----------------+-----------------+-----------------+----------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                  |
   +=================+=================+=================+==============================================+
   | key             | Yes             | String          | Tag key.                                     |
   |                 |                 |                 |                                              |
   |                 |                 |                 | The key of the same resource must be unique. |
   +-----------------+-----------------+-----------------+----------------------------------------------+
   | value           | No              | String          | Tag key                                      |
   +-----------------+-----------------+-----------------+----------------------------------------------+

Response Parameters
-------------------

**Status code: 204**

Normal request response. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

None

Example Requests
----------------

Delete tags from a network ACL in batches. The key of the tag is **keyxxx**, and the value is **value1**.

.. code-block:: text

   POST https://{Endpoint}/v3/{project_id}/firewalls/{firewall_id}/tags/delete

   {
     "tags" : [ {
       "key" : "keyxxx",
       "value" : "value1"
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
