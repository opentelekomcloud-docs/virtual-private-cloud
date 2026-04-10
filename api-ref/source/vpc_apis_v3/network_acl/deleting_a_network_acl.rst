:original_name: DeleteFirewall.html

.. _DeleteFirewall:

Deleting a Network ACL
======================

Function
--------

This API is used to delete a network ACL that is no longer required.

URI
---

DELETE /v3/{project_id}/vpc/firewalls/{firewall_id}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================================================+
   | firewall_id     | Yes             | String          | **Definition**:                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 | Network ACL ID. You can call the API :ref:`Querying Network ACLs <listfirewall>` to obtain the ID of the target network ACL, and then use this API to delete the network ACL. |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 | **Range**:                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 | N/A                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id      | Yes             | String          | **Definition**:                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 | ID of the project that the network ACL belongs to.                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 | **Range**:                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 | N/A                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 204**

Normal response to the DELETE operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

None

Example Requests
----------------

Deleting a network ACL

.. code-block:: text

   DELETE https://{Endpoint}/v3/{project_id}/vpc/firewalls/{firewall_id}

Example Responses
-----------------

None

Status Codes
------------

+-------------+---------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                             |
+=============+=========================================================================================================+
| 204         | Normal response to the DELETE operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`. |
+-------------+---------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
