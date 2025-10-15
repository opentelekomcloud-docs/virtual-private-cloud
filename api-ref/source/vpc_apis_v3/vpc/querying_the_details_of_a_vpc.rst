:original_name: vpc_apiv3_0004.html

.. _vpc_apiv3_0004:

Querying the Details of a VPC
=============================

Function
--------

After a VPC is created, you can call this API to query all information about the VPC, including the VPC name, ID, and CIDR block.

URI
---

GET /v3/{project_id}/vpc/vpcs/{vpc_id}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                               |
   +=================+=================+=================+===========================================================+
   | project_id      | Yes             | String          | -  Definition: ID of the project that a VPC belongs to.   |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | -  Range: None                                            |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------+
   | vpc_id          | Yes             | String          | -  Definition: VPC ID, which uniquely identifies the VPC. |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | -  Range: None                                            |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------------------+--------------------------------------------------+----------------------------------------------------------------+
   | Parameter             | Type                                             | Description                                                    |
   +=======================+==================================================+================================================================+
   | request_id            | String                                           | -  Definition: Request ID.                                     |
   |                       |                                                  |                                                                |
   |                       |                                                  | -  Range: None                                                 |
   +-----------------------+--------------------------------------------------+----------------------------------------------------------------+
   | vpc                   | :ref:`Vpc <vpc_apiv3_0004__response_vpc>` object | -  Definition: Response body for querying details about a VPC. |
   |                       |                                                  |                                                                |
   |                       |                                                  | -  Range: None                                                 |
   +-----------------------+--------------------------------------------------+----------------------------------------------------------------+

.. _vpc_apiv3_0004__response_vpc:

.. table:: **Table 3** Vpc

   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                           | Description                                                                                                                                                        |
   +=======================+================================================================================+====================================================================================================================================================================+
   | id                    | String                                                                         | -  Definition: VPC ID. After a VPC is created, a VPC ID is generated, which uniquely identifies the VPC.                                                           |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | -  Range: The value is in UUID format with hyphens (-).                                                                                                            |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                         | -  Definition: VPC name.                                                                                                                                           |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | -  Range: The value can contain 0 to 64 characters. It can include letters, digits, underscores (_), hyphens (-), and periods (.).                                 |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                         | -  Definition: Description of a VPC.                                                                                                                               |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | -  Range: The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                                            |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cidr                  | String                                                                         | -  Definition: Available subnets in a VPC.                                                                                                                         |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | -  Range:                                                                                                                                                          |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  10.0.0.0/8-24: The IP address ranges from 10.0.0.0 to 10.255.255.255, and the netmask ranges from 8 to 24.                                                   |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  172.16.0.0/12-24: The IP address ranges from 172.16.0.0 to 172.31.255.255, and the netmask ranges from 12 to 24.                                             |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  192.168.0.0/16-24: The IP address ranges from 192.168.0.0 to 192.168.255.255, and the netmask ranges from 16 to 24.                                          |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  If **cidr** is not specified, the default value is **""**.                                                                                                   |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | extend_cidrs          | Array of strings                                                               | -  Definition: Secondary CIDR blocks of a VPC.                                                                                                                     |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | -  Range: The following CIDR blocks are not supported:                                                                                                             |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  10.0.0.0/8: The IP address range is 10.0.0.0-10.255.255.255.                                                                                                 |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  172.16.0.0/12: The IP address range is 172.16.0.0-172.31.255.255.                                                                                            |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  192.168.0.0/16: The IP address range is 192.168.0.0-192.168.255.255.                                                                                         |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  172.31.0.0/16: The IP address range is 172.31.0.0-172.31.255.255.                                                                                            |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  100.64.0.0/10: The IP address range is 100.64.0.0-100.127.255.255.                                                                                           |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  214.0.0.0/7: The IP address range is 214.0.0.0-215.255.255.255.                                                                                              |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  198.18.0.0/15: The IP address range is 198.18.0.0-198.19.255.255.                                                                                            |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  169.254.0.0/16: The IP address range is 169.254.0.0-169.254.255.255.                                                                                         |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  0.0.0.0/8: The IP address range is 0.0.0.0-0.255.255.255.                                                                                                    |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  127.0.0.0/8: The IP address range is 127.0.0.0-127.255.255.255.                                                                                              |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  240.0.0.0/4: The IP address range is 240.0.0.0-255.255.255.255.                                                                                              |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                                         | -  Definition: VPC status.                                                                                                                                         |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | -  Range:                                                                                                                                                          |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  **PENDING**: The VPC is being created.                                                                                                                       |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    -  **ACTIVE**: The VPC is created.                                                                                                                              |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                                         | -  Definition: ID of the project that a VPC belongs to.                                                                                                            |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | -  Range: None                                                                                                                                                     |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | String                                                                         | -  Definition: ID of the enterprise project that a VPC belongs to.                                                                                                 |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | -  Range: The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). **0** indicates the default enterprise project. |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                         | -  Definition: Time when a VPC was created.                                                                                                                        |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | -  Range: UTC time in the format of yyyy-MM-ddTHH:mm:ssZ                                                                                                           |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                         | -  Definition: Time when a VPC was updated.                                                                                                                        |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | -  Range: UTC time in the format of yyyy-MM-ddTHH:mm:ssZ                                                                                                           |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cloud_resources       | Array of :ref:`CloudResource <vpc_apiv3_0004__response_cloudresource>` objects | -  Definition: Type and number of resources associated with a VPC. For example, subnets and route tables.                                                          |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | -  Range: None                                                                                                                                                     |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Array of :ref:`ResponseTag <vpc_apiv3_0004__response_responsetag>` objects     | -  Definition: Tags of a VPC, including tag keys and tag values, which can be used to classify and identify resources. For details, see the tag objects.           |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | -  Range: None                                                                                                                                                     |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0004__response_cloudresource:

.. table:: **Table 4** CloudResource

   +-----------------------+-----------------------+-------------------------------------+
   | Parameter             | Type                  | Description                         |
   +=======================+=======================+=====================================+
   | resource_type         | String                | -  Definition: Resource type.       |
   |                       |                       |                                     |
   |                       |                       | -  Range: None                      |
   +-----------------------+-----------------------+-------------------------------------+
   | resource_count        | Integer               | -  Definition: Number of resources. |
   |                       |                       |                                     |
   |                       |                       | -  Range: None                      |
   +-----------------------+-----------------------+-------------------------------------+

.. _vpc_apiv3_0004__response_responsetag:

.. table:: **Table 5** ResponseTag

   +-----------------------+-----------------------+----------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                      |
   +=======================+=======================+==================================================================================+
   | key                   | String                | -  Definition: Tag key.                                                          |
   |                       |                       |                                                                                  |
   |                       |                       | -  Range:                                                                        |
   |                       |                       |                                                                                  |
   |                       |                       |    -  Each key can contain up to 36 Unicode characters and cannot be left blank. |
   |                       |                       |                                                                                  |
   |                       |                       |    -  Each key value of a resource must be unique.                               |
   |                       |                       |                                                                                  |
   |                       |                       |    -  The value can contain:                                                     |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Letters                                                                 |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Digits                                                                  |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Special characters: underscores (_) ,at signs (@), and hyphens (-)      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------+
   | value                 | String                | -  Definition: Tag value.                                                        |
   |                       |                       |                                                                                  |
   |                       |                       | -  Range:                                                                        |
   |                       |                       |                                                                                  |
   |                       |                       |    -  Each value can contain up to 43 Unicode characters and can be left blank.  |
   |                       |                       |                                                                                  |
   |                       |                       |    -  The value can contain:                                                     |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Letters                                                                 |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Digits                                                                  |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Special characters: underscore (_), at signs (@), and hyphen (-)        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------+

Example Requests
----------------

Querying the details of a VPC

.. code-block:: text

   GET https://{Endpoint}/v3/{project_id}/vpc/vpcs/0552091e-b83a-49dd-88a7-4a5c86fd9ec3

Example Responses
-----------------

**Status code: 200**

Normal response to the GET operation. For more status codes, see :ref:`Status Code <vpc_api_0002>`.

.. code-block::

   {
     "request_id" : "84eb4f775d66dd916db121768ec55626",
     "vpc" : {
       "id" : "0552091e-b83a-49dd-88a7-4a5c86fd9ec3",
       "name" : "name-test",
       "description" : "description-test",
       "cidr" : "192.168.0.0/16",
       "extend_cidrs" : [ "21.8.0.0/16" ],
       "enterprise_project_id" : "0",
       "tags" : [ {
         "key" : "key",
         "value" : "value"
       } ],
       "cloud_resources" : [ {
         "resource_type" : "routetable",
         "resource_count" : 1
       } ],
       "status" : "ACTIVE",
       "project_id" : "060576782980d5762f9ec014dd2f1148",
       "created_at" : "2018-03-23T09:26:08",
       "updated_at" : "2018-08-24T08:49:53"
     }
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                         |
+=============+=====================================================================================================+
| 200         | Normal response to the GET operation. For more status codes, see :ref:`Status Code <vpc_api_0002>`. |
+-------------+-----------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
