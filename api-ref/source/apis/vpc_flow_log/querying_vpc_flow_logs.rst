:original_name: vpc_flow_0002.html

.. _vpc_flow_0002:

Querying VPC Flow Logs
======================

Function
--------

This API is used to query all VPC flow logs of the tenant submitting the request. The VPC flow logs are filtered based on the filtering condition.

URI
---

GET /v1/{project_id}/fl/flow_logs

Example:

.. code-block:: text

   GET https://{Endpoint}/v1/b2782e6708b8475c993e6064bc456bf8/fl/flow_logs?name=flowlog

:ref:`Table 1 <vpc_flow_0002__table238711153416>` describes the parameters.

.. _vpc_flow_0002__table238711153416:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================+
   | project_id      | Yes             | String          | Specifies the project ID.                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id              | No              | String          | Specifies the VPC flow log UUID.                                                                                                                                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | -  Specifies the VPC flow log name.                                                                                                                                                                                    |
   |                 |                 |                 | -  The value can contain no more than 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                         |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_type   | No              | String          | Specifies the type of resource on which to create the VPC flow log.                                                                                                                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_id     | No              | String          | Specifies the unique resource ID.                                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | traffic_type    | No              | String          | Specifies the type of traffic to log.                                                                                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | No              | String          | Specifies the log group ID.                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_topic_id    | No              | String          | Specifies the log topic ID.                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Specifies the VPC flow log status.                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | -  **ACTIVE**: Enabled                                                                                                                                                                                                 |
   |                 |                 |                 | -  **DOWN**: Disabled                                                                                                                                                                                                  |
   |                 |                 |                 | -  **ERROR**: Abnormal fault                                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax.                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Specifies a resource ID for pagination query, indicating that the query starts from the next record of the specified resource ID.                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | This parameter can work together with the parameter **limit**.                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | -  If parameters **marker** and **limit** are not passed, all resource records will be returned.                                                                                                                       |
   |                 |                 |                 | -  If the parameter **marker** is not passed and the value of parameter **limit** is set to **10**, the first 10 resource records will be returned.                                                                    |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the value of parameter **limit** is set to **10**, the 11th to 20th resource records will be returned.                    |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the parameter **limit** is not passed, resource records starting from the 11th records (including 11th) will be returned. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

-  Request parameter

   None

-  Example request

   None

Response Message
----------------

-  Response parameter

   .. table:: **Table 2** Response parameter

      +-----------+----------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
      | Name      | Type                                                                 | Description                                                                                                  |
      +===========+======================================================================+==============================================================================================================+
      | flow_logs | Array of :ref:`FlowLog <vpc_flow_0002__table34811015184118>` objects | Specifies the **FlowLog** object list. For details, see :ref:`Table 3 <vpc_flow_0002__table34811015184118>`. |
      +-----------+----------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+

   .. _vpc_flow_0002__table34811015184118:

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
          "flow_logs": [
              {
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
          ]
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
