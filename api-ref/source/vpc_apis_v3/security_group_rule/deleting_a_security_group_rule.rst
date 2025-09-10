:original_name: vpc_apiv3_0019.html

.. _vpc_apiv3_0019:

Deleting a Security Group Rule
==============================

Function
--------

You can call this API to delete a security group rule that is no longer used.

URI
---

DELETE /v3/{project_id}/vpc/security-group-rules/{security_group_rule_id}

.. table:: **Table 1** Path Parameters

   +------------------------+-----------------+-----------------+---------------------------------------------+
   | Parameter              | Mandatory       | Type            | Description                                 |
   +========================+=================+=================+=============================================+
   | project_id             | Yes             | String          | -  Definition: Project ID.                  |
   |                        |                 |                 |                                             |
   |                        |                 |                 | -  Range: None                              |
   +------------------------+-----------------+-----------------+---------------------------------------------+
   | security_group_rule_id | Yes             | String          | -  Definition: ID of a security group rule. |
   |                        |                 |                 |                                             |
   |                        |                 |                 | -  Range: None                              |
   +------------------------+-----------------+-----------------+---------------------------------------------+

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

Delete the security group rule whose ID is f626eb24-d8bd-4d26-ae0b-c16bb65730cb.

.. code-block:: text

   DELETE https://{Endpoint}/v3/{project_id}/vpc/security-group-rules/f626eb24-d8bd-4d26-ae0b-c16bb65730cb

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
