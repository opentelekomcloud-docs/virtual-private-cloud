:original_name: vpc_apiv3_0014.html

.. _vpc_apiv3_0014:

Deleting a Security Group
=========================

Function
--------

You can call this API to delete a security group that is no longer used.

Constraints
-----------

Before deleting a security group, ensure that the security group is not associated with any instance.

URI
---

DELETE /v3/{project_id}/vpc/security-groups/{security_group_id}

.. table:: **Table 1** Path Parameters

   +-------------------+-----------------+-----------------+--------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                        |
   +===================+=================+=================+====================================================================+
   | project_id        | Yes             | String          | -  Definition: ID of the project that a security group belongs to. |
   |                   |                 |                 |                                                                    |
   |                   |                 |                 | -  Range: None                                                     |
   +-------------------+-----------------+-----------------+--------------------------------------------------------------------+
   | security_group_id | Yes             | String          | -  Definition: ID of a security group.                             |
   |                   |                 |                 |                                                                    |
   |                   |                 |                 | -  Range: None                                                     |
   +-------------------+-----------------+-----------------+--------------------------------------------------------------------+

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

Deleting a security group

.. code-block:: text

   DELETE https://{Endpoint}/v3/{project_id}/vpc/security-groups/69c999ad-d9ef-4d79-94fd-35e6ceb75325

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
