:original_name: vpc_apiv3_0019.html

.. _vpc_apiv3_0019:

Deleting a Security Group Rule
==============================

Function
--------

This API is used to delete a security group rule.

URI
---

DELETE /v3/{project_id}/vpc/security-group-rules/{security_group_rule_id}

.. table:: **Table 1** Path Parameters

   ====================== ========= ====== =======================
   Parameter              Mandatory Type   Description
   ====================== ========= ====== =======================
   project_id             Yes       String Project ID.
   security_group_rule_id Yes       String Security group rule ID.
   ====================== ========= ====== =======================

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Requests
----------------

Delete a single security group rule.

.. code-block:: text

   DELETE https://{Endpoint}/v3/{project_id}/vpc/security-group-rules/01a772b2-463e-47e3-a95d-bac85ee8adc6

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
