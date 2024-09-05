:original_name: vpc_apiroutetab_0006.html

.. _vpc_apiroutetab_0006:

Deleting a Route Table
======================

Function
--------

This API is used to delete a custom route table.

Constraints:

Only custom route tables can be deleted. If a custom route table has subnets associated, disassociate the subnets with the route table and then delete the route table.

URI
---

DELETE /v1/{project_id}/routetables/{routetable_id}

:ref:`Table 1 <vpc_apiroutetab_0006__table13893430173220>` describes the parameters.

.. _vpc_apiroutetab_0006__table13893430173220:

.. table:: **Table 1** Parameter description

   +---------------+-----------+--------+------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                            |
   +===============+===========+========+========================================================================+
   | project_id    | Yes       | String | Specifies the project ID.                                              |
   +---------------+-----------+--------+------------------------------------------------------------------------+
   | routetable_id | Yes       | String | Specifies the route table ID, which uniquely identifies a route table. |
   +---------------+-----------+--------+------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{Endpoint}/v1/{project_id}/routetables/3d42a0d4-a980-4613-ae76-a2cddecff054

Response Parameters
-------------------

None

Example Response
----------------

None

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
