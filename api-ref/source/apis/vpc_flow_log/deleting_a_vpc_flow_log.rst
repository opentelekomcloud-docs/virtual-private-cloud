:original_name: vpc_flow_0005.html

.. _vpc_flow_0005:

Deleting a VPC Flow Log
=======================

Function
--------

This API is used to delete a flow log.

URI
---

DELETE /v1/{project_id}/fl/flow_logs/{flowlog_id}

:ref:`Table 1 <vpc_flow_0005__table19961835154017>` describes the parameters.

.. _vpc_flow_0005__table19961835154017:

.. table:: **Table 1** Parameter description

   ========== ========= ====== ==============================
   Name       Mandatory Type   Description
   ========== ========= ====== ==============================
   project_id Yes       String Specifies the project ID.
   flowlog_id Yes       String Specifies the VPC flow log ID.
   ========== ========= ====== ==============================

Request Message
---------------

-  Request parameter

   None

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v1/b2782e6708b8475c993e6064bc456bf8/fl/flow_logs/60c809cb-6731-45d0-ace8-3bf5626421a9

Response Message
----------------

-  Request parameter

   None

-  Example response

   None

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
