:original_name: vpc_apiv3_0014.html

.. _vpc_apiv3_0014:

Deleting a Security Group
=========================

Function
--------

This API is used to delete a security group.

Constraints
-----------

Before deleting a security group, ensure that the security group is not associated with any instance.

URI
---

DELETE /v3/{project_id}/vpc/security-groups/{security_group_id}

.. table:: **Table 1** Path Parameters

   ================= ========= ====== ==================
   Parameter         Mandatory Type   Description
   ================= ========= ====== ==================
   project_id        Yes       String Project ID.
   security_group_id Yes       String Security group ID.
   ================= ========= ====== ==================

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Requests
----------------

Deleting a security group.

.. code-block:: text

   DELETE https://{Endpoint}/v3/{project_id}/vpc/security-groups/1d8b19c7-7c56-48f7-a99b-4b40eb390967

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
