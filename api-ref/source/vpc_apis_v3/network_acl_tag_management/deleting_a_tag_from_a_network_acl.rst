:original_name: DeleteFirewallTag.html

.. _DeleteFirewallTag:

Deleting a Tag from a Network ACL
=================================

Function
--------

This API is used to delete a tag from a specified network ACL. This is an idempotent API. The tag key cannot be left blank or be an empty string. If the key of the tag to be deleted does not exist, 404 will be returned.

URI
---

DELETE /v3/{project_id}/firewalls/{firewall_id}/tags/{tag_key}

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
   | tag_key         | Yes             | String          | Tag key                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 204**

Normal request response. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

None

Example Requests
----------------

Delete a tag from a network ACL.

.. code-block:: text

   DELETE https://{Endpoint}/v3/{project_id}/firewalls/{firewall_id}/tags/{tag_key}

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
