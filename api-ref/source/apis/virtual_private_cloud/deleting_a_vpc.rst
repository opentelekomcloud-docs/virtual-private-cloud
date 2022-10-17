:original_name: vpc_api01_0005.html

.. _vpc_api01_0005:

Deleting a VPC
==============

Function
--------

This API is used to delete a VPC.

URI
---

DELETE /v1/{project_id}/vpcs/{vpc_id}

:ref:`Table 1 <vpc_api01_0005__table47834478>` describes the parameters.

.. _vpc_api01_0005__table47834478:

.. table:: **Table 1** Parameter description

   +------------+-----------+----------------------------------------------------------+
   | Name       | Mandatory | Description                                              |
   +============+===========+==========================================================+
   | project_id | Yes       | Specifies the project ID.                                |
   +------------+-----------+----------------------------------------------------------+
   | vpc_id     | Yes       | Specifies the VPC ID, which uniquely identifies the VPC. |
   +------------+-----------+----------------------------------------------------------+

Request Message
---------------

-  Request parameter

   None

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v1/{project_id}/vpcs/13551d6b-755d-4757-b956-536f674975c0

Response Message
----------------

-  Response parameter

   None

-  Example response

   None

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
