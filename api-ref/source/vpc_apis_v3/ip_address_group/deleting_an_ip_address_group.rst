:original_name: vpc_apiv3_0026.html

.. _vpc_apiv3_0026:

Deleting an IP Address Group
============================

Function
--------

This API is used to delete an IP address group. Before deleting an IP address group, ensure that no resource is using this group.

URI
---

DELETE /v3/{project_id}/vpc/address-groups/{address_group_id}

.. table:: **Table 1** Path Parameters

   +------------------+-----------+--------+--------------------------------------------------------------------+
   | Parameter        | Mandatory | Type   | Description                                                        |
   +==================+===========+========+====================================================================+
   | address_group_id | Yes       | String | IP address group ID that uniquely identifies the IP address group. |
   +------------------+-----------+--------+--------------------------------------------------------------------+
   | project_id       | Yes       | String | Project ID.                                                        |
   +------------------+-----------+--------+--------------------------------------------------------------------+

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

Delete the address group whose ID is **dd18a501-fcd5-4adc-acfe-b0e2384baf08**.

.. code-block:: text

   DELETE https://{{endpoint}}/v3/{{tenant_id}}/vpc/address-groups/dd18a501-fcd5-4adc-acfe-b0e2384baf08

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
