:original_name: vpc_flow_0004.html

.. _vpc_flow_0004:

Updating a VPC Flow Log
=======================

Function
--------

This API is used to update a VPC flow log.

URI
---

PUT /v1/{project_id}/fl/flow_logs/{flowlog_id}

:ref:`Table 1 <vpc_flow_0004__table12780121844016>` describes the parameters.

.. _vpc_flow_0004__table12780121844016:

.. table:: **Table 1** Parameter description

   ========== ========= ====== ===========
   Name       Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   flowlog_id Yes       String Flow log ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request parameter

   +----------+-----------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | Name     | Mandatory | Type                                                        | Description                                                                                |
   +==========+===========+=============================================================+============================================================================================+
   | flow_log | Yes       | :ref:`flow_log <vpc_flow_0004__table13828101864013>` object | **FlowLog** objects. For details, see :ref:`Table 3 <vpc_flow_0004__table13828101864013>`. |
   +----------+-----------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------+

.. _vpc_flow_0004__table13828101864013:

.. table:: **Table 3** Description of the **FlowLog** field

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                    |
   +=================+=================+=================+================================================================================================================================+
   | name            | No              | String          | -  Flow log name                                                                                                               |
   |                 |                 |                 | -  The value can contain no more than 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | -  Flow log description                                                                                                        |
   |                 |                 |                 | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                               |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
   | admin_state     | No              | Boolean         | -  Whether to enable the flow log function                                                                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  Change the name of the VPC flow log whose ID is f49f00f1-0f15-470a-a8c5-4e879e461c8d to **flow-log-update**.

   .. code-block:: text

      PUT https://{Endpoint}/v1/b2782e6708b8475c993e6064bc456bf8/fl/flow_logs/f49f00f1-0f15-470a-a8c5-4e879e461c8d

      {
          "flow_log": {
              "name": "flow-log-update",
              "description": "update",
              "admin_state": false
          }
      }

Response Parameters
-------------------

.. table:: **Table 4** Response parameter

   +----------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | Name     | Type                                                        | Description                                                                                |
   +==========+=============================================================+============================================================================================+
   | flow_log | :ref:`flow_log <vpc_flow_0004__table17299234185110>` object | **FlowLog** objects. For details, see :ref:`Table 5 <vpc_flow_0004__table17299234185110>`. |
   +----------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------+

.. _vpc_flow_0004__table17299234185110:

.. table:: **Table 5** Description of the **FlowLog** field

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Type                  | Description                                                                                                                    |
   +=======================+=======================+================================================================================================================================+
   | id                    | String                | -  Flow log ID                                                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | -  Flow log name                                                                                                               |
   |                       |                       | -  The value can contain no more than 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.). |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                | -  Project ID                                                                                                                  |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | -  Flow log description                                                                                                        |
   |                       |                       | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | resource_type         | String                | -  Type of the resource for which that the logs to be collected.                                                               |
   |                       |                       | -  The value can be:                                                                                                           |
   |                       |                       |                                                                                                                                |
   |                       |                       |    -  **port**: NIC                                                                                                            |
   |                       |                       |    -  **vpc**: All NICs in a VPC                                                                                               |
   |                       |                       |    -  **network**: All NICs in a subnet                                                                                        |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | resource_id           | String                | -  ID of the resource for which that the logs to be collected.                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | traffic_type          | String                | -  Type of the traffic for which that the logs to be collected.                                                                |
   |                       |                       | -  The value can be:                                                                                                           |
   |                       |                       |                                                                                                                                |
   |                       |                       |    -  **all**: specifies that both accepted and rejected traffic of the specified resource will be logged.                     |
   |                       |                       |    -  **accept**: specifies that only accepted inbound and outbound traffic of the specified resource will be logged.          |
   |                       |                       |    -  **reject**: specifies that only rejected inbound and outbound traffic of the specified resource will be logged.          |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id          | String                | -  Log group ID                                                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | log_topic_id          | String                | -  Log topic ID                                                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | admin_state           | Boolean               | -  Whether to enable the flow log function                                                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                | -  Flow log status                                                                                                             |
   |                       |                       | -  The value can be:                                                                                                           |
   |                       |                       |                                                                                                                                |
   |                       |                       |    -  **ACTIVE**: Enabled                                                                                                      |
   |                       |                       |    -  **DOWN**: Disabled                                                                                                       |
   |                       |                       |    -  **ERROR**: Abnormal                                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                | -  Time when the flow log is created                                                                                           |
   |                       |                       | -  UTC time in the format of yyyy-MM-ddTHH:mmss                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                | -  Time when the flow log is updated                                                                                           |
   |                       |                       | -  UTC time in the format of yyyy-MM-ddTHH:mmss                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "flow_log": {
           "id": "f49f00f1-0f15-470a-a8c5-4e879e461c8d",
           "name": " flow-log-update",
           "description": "update",
           "tenant_id": "b2782e6708b8475c993e6064bc456bf8",
           "resource_type": "port",
           "resource_id": "05c4052d-8d14-488f-aa00-19fea5a25fde",
           "traffic_type": "reject",
           "log_group_id": "05c4052d-8d14-488f-aa00-19fea5a25fdd",
           "log_topic_id": "a9d7dee7-37d2-4cba-a208-a016252aaa63",
           "created_at": "2019-01-14T11:03:02",
           "updated_at": "2019-01-14T12:03:02",
           "status": "DOWN",
           "admin_state": false
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
