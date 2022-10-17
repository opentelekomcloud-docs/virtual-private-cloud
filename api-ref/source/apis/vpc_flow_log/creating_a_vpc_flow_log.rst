:original_name: vpc_flow_0001.html

.. _vpc_flow_0001:

Creating a VPC Flow Log
=======================

Function
--------

This API is used to create a flow log.

A VPC flow log captures information about the traffic going to and from your VPC. You can use flow logs to monitor network traffic, analyze network attacks, and to determine whether security group and firewall rules need to be modified.

VPC flow logs must be used together with the Log Tank Service (LTS). You need to create a log group and a log topic in LTS, and then create a VPC flow log.

URI
---

POST /v1/{project_id}/fl/flow_logs

:ref:`Table 1 <vpc_flow_0001__table1851575853914>` describes the parameters.

.. _vpc_flow_0001__table1851575853914:

.. table:: **Table 1** Parameter description

   ========== ========= ====== =========================
   Name       Mandatory Type   Description
   ========== ========= ====== =========================
   project_id Yes       String Specifies the project ID.
   ========== ========= ====== =========================

Request Message
---------------

-  Request parameter

   .. table:: **Table 2** Request parameter

      +----------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
      | Name     | Type                                                      | Description                                                                                            |
      +==========+===========================================================+========================================================================================================+
      | flow_log | :ref:`flow_log <vpc_flow_0001__table656165873916>` object | Specifies the **FlowLog** objects. For details, see :ref:`Table 3 <vpc_flow_0001__table656165873916>`. |
      +----------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------+

   .. _vpc_flow_0001__table656165873916:

   .. table:: **Table 3** Description of the **FlowLog** field

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                    |
      +=================+=================+=================+================================================================================================================================+
      | name            | No              | String          | -  Specifies the VPC flow log name.                                                                                            |
      |                 |                 |                 | -  The value can contain no more than 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.). |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
      | description     | No              | String          | -  Provides supplementary information about the VPC flow log.                                                                  |
      |                 |                 |                 | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                               |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
      | resource_type   | Yes             | String          | Specifies the type of resource on which to create the VPC flow log. The value can be **Port**, **VPC**, and **Network**.       |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
      | resource_id     | Yes             | String          | Specifies the unique resource ID.                                                                                              |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
      | traffic_type    | Yes             | String          | Specifies the type of traffic to log. The value can be:                                                                        |
      |                 |                 |                 |                                                                                                                                |
      |                 |                 |                 | -  **all**: specifies that both accepted and rejected traffic of the specified resource will be logged.                        |
      |                 |                 |                 | -  **accept**: specifies that only accepted inbound and outbound traffic of the specified resource will be logged.             |
      |                 |                 |                 | -  **reject**: specifies that only rejected inbound and outbound traffic of the specified resource will be logged.             |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
      | log_group_id    | Yes             | String          | Specifies the log group ID.                                                                                                    |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
      | log_topic_id    | Yes             | String          | Specifies the log topic ID.                                                                                                    |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
      | index_enabled   | No              | Boolean         | Specifies whether to enable the log index.                                                                                     |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{Endpoint}/v1/b2782e6708b8475c993e6064bc456bf8/fl/flow_logs

      {
          "flow_log": {
              "name": "flowlog",
              "description": "just a test",
              "resource_type": "port",
              "resource_id": "05c4052d-8d14-488f-aa00-19fea5a25fde",
              "traffic_type": "reject",
              "log_group_id": "05c4052d-8d14-488f-aa00-19fea5a25fdd",
              "log_topic_id": "a9d7dee7-37d2-4cba-a208-a016252aaa63",
              "index_enabled": true
          }
      }

Response Message
----------------

-  Response parameter

   .. table:: **Table 4** Response parameter

      +----------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
      | Name     | Type                                                      | Description                                                                                            |
      +==========+===========================================================+========================================================================================================+
      | flow_log | :ref:`flow_log <vpc_flow_0001__table763920584395>` object | Specifies the **FlowLog** objects. For details, see :ref:`Table 5 <vpc_flow_0001__table763920584395>`. |
      +----------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------+

   .. _vpc_flow_0001__table763920584395:

   .. table:: **Table 5** Description of the **FlowLog** field

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
      | index_enabled         | Boolean               | Specifies whether to enable the log index.                          |
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
              "id": "f49f00f1-0f15-470a-a8c5-4e879e461c8d",
              "name": "flowlog",
              "description": "just a test",
              "tenant_id": "b2782e6708b8475c993e6064bc456bf8",
              "resource_type": "port",
              "resource_id": "05c4052d-8d14-488f-aa00-19fea5a25fde",
              "traffic_type": "reject",
              "log_group_id": "05c4052d-8d14-488f-aa00-19fea5a25fdd",
              "log_topic_id": "a9d7dee7-37d2-4cba-a208-a016252aaa63",
              "created_at": "2019-01-14T11:03:02",
              "updated_at": "2019-01-14T11:03:02",
              "index_enabled": false,
              "admin_state": true,
              "status": "ACTIVE"
          }
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
