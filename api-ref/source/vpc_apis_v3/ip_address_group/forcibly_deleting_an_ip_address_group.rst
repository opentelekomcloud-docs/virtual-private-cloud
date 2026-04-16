:original_name: vpc_apiv3_0027.html

.. _vpc_apiv3_0027:

Forcibly Deleting an IP Address Group
=====================================

Function
--------

You can call this API to delete an IP address group that is no longer used. This API is used to forcibly delete an IP address group. If the IP address group to be deleted is associated with security group rules or network ACL rules, the IP address group and its associated rules will be deleted together.

URI
---

DELETE /v3/{project_id}/vpc/address-groups/{address_group_id}/force

.. table:: **Table 1** Path Parameters

   +------------------+-----------------+-----------------+--------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                            |
   +==================+=================+=================+========================================================+
   | address_group_id | Yes             | String          | **Definition**:                                        |
   |                  |                 |                 |                                                        |
   |                  |                 |                 | ID of an IP address group.                             |
   |                  |                 |                 |                                                        |
   |                  |                 |                 | **Range**:                                             |
   |                  |                 |                 |                                                        |
   |                  |                 |                 | N/A                                                    |
   +------------------+-----------------+-----------------+--------------------------------------------------------+
   | project_id       | Yes             | String          | **Definition**:                                        |
   |                  |                 |                 |                                                        |
   |                  |                 |                 | ID of the project that an IP address group belongs to. |
   |                  |                 |                 |                                                        |
   |                  |                 |                 | **Range**:                                             |
   |                  |                 |                 |                                                        |
   |                  |                 |                 | N/A                                                    |
   +------------------+-----------------+-----------------+--------------------------------------------------------+

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

Forcibly delete the address group whose ID is **dd18a501-fcd5-4adc-acfe-b0e2384baf08**.

.. code-block:: text

   DELETE https://{{endpoint}}/v3/{{tenant_id}}/vpc/address-groups/dd18a501-fcd5-4adc-acfe-b0e2384baf08/force

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
