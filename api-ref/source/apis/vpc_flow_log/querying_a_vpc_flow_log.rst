:original_name: vpc_flow_0003.html

.. _vpc_flow_0003:

Querying a VPC Flow Log
=======================

Function
--------

This API is used to query a VPC flow log.

URI
---

GET /v1/{project_id}/fl/flow_logs/{flowlog_id}

:ref:`Table 1 <vpc_flow_0003__table152848346516>` describes the parameters.

.. _vpc_flow_0003__table152848346516:

.. table:: **Table 1** Parameter description

   +------------+-----------+--------+----------------------------------------------------------------------------+
   | Name       | Mandatory | Type   | Description                                                                |
   +============+===========+========+============================================================================+
   | project_id | Yes       | String | Specifies the project ID.                                                  |
   +------------+-----------+--------+----------------------------------------------------------------------------+
   | flowlog_id | Yes       | String | Specifies the VPC flow log ID, which uniquely identifies the VPC flow log. |
   +------------+-----------+--------+----------------------------------------------------------------------------+

Request Message
---------------

-  Request parameter

   None

-  Example request

   .. code-block:: text

      GET https://{Endpoint}/v1/b2782e6708b8475c993e6064bc456bf8/fl/flow_logs/1e10cd9d-742a-4d36-a9fd-aee9784336ff

Response Message
----------------

-  Response parameter

   .. table:: **Table 2** Response parameter

      +----------+-------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+
      | Name     | Type                                                        | Description                                                                                              |
      +==========+=============================================================+==========================================================================================================+
      | flow_log | :ref:`flow_log <vpc_flow_0003__table17299234185110>` object | Specifies the **FlowLog** objects. For details, see :ref:`Table 3 <vpc_flow_0003__table17299234185110>`. |
      +----------+-------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+

   .. _vpc_flow_0003__table17299234185110:

   .. table:: **Table 3** Description of the **FlowLog** field

      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                         |
      +=======================+=======================+=====================================================================+
      | id                    | String                | Specifies the VPC flow log UUID.                                    |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | name                  | String                | Specifies the VPC flow log name.                                    |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | tenant_id             | String                | Specifies the project ID.                                           |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | description           | String                | Provides supplementary information about the VPC flow log.          |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | resource_type         | String                | Specifies the type of resource on which to create the VPC flow log. |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | resource_id           | String                | Specifies the unique resource ID.                                   |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | traffic_type          | String                | Specifies the type of traffic to log.                               |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | log_group_id          | String                | Specifies the log group ID.                                         |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | log_topic_id          | String                | Specifies the log topic ID.                                         |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | admin_state           | Boolean               | Specifies whether to enable the VPC flow log function.              |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | status                | String                | Specifies the VPC flow log status.                                  |
      |                       |                       |                                                                     |
      |                       |                       | -  **ACTIVE**: Enabled                                              |
      |                       |                       | -  **DOWN**: Disabled                                               |
      |                       |                       | -  **ERROR**: Abnormal fault                                        |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | created_at            | String                | Specifies the time when the VPC flow log was created.               |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | updated_at            | String                | Specifies the time when the VPC flow log was updated.               |
      +-----------------------+-----------------------+---------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "flow_log": {
              "id": "35868d55-443e-4d5c-90a4-ac618dc45c1a",
              "name": "flow",
              "description": "just a test",
              "tenant_id": "b2782e6708b8475c993e6064bc456bf8",
              "resource_type": "port",
              "resource_id": "05c4052d-8d14-488f-aa00-19fea5a25fde",
              "traffic_type": "reject",
              "log_group_id": "05c4052d-8d14-488f-aa00-19fea5a25fff",
              "log_topic_id": "a9d7dee7-37d2-4cba-a208-a016252aaa63",
              "created_at": "2019-01-14T11:03:02",
              "updated_at": "2019-01-14T11:03:02"
              "status": "ACTIVE",
              "admin_state": true
          }
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
