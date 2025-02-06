:original_name: vpc_bandwidth_0002.html

.. _vpc_bandwidth_0002:

Querying Bandwidths
===================

Function
--------

This API is used to query bandwidths using search criteria.

URI
---

GET /v1/{project_id}/bandwidths

:ref:`Table 1 <vpc_bandwidth_0002__table62833603>` describes the parameters.

.. _vpc_bandwidth_0002__table62833603:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                                                                                                                                                 |
   +=======================+=================+=================+=============================================================================================================================================================================================================================================================+
   | project_id            | Yes             | String          | Specifies the project ID.                                                                                                                                                                                                                                   |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker                | No              | String          | Specifies a resource ID for pagination query, indicating that the query starts from the next record of the specified resource ID.                                                                                                                           |
   |                       |                 |                 |                                                                                                                                                                                                                                                             |
   |                       |                 |                 | This parameter can work together with the parameter **limit**.                                                                                                                                                                                              |
   |                       |                 |                 |                                                                                                                                                                                                                                                             |
   |                       |                 |                 | -  If parameters **marker** and **limit** are not passed, resource records on the first page will be returned.                                                                                                                                              |
   |                       |                 |                 | -  If the parameter **marker** is not passed and the value of parameter **limit** is set to **10**, the first 10 resource records will be returned.                                                                                                         |
   |                       |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the value of parameter **limit** is set to **10**, the 11th to 20th resource records will be returned.                                                         |
   |                       |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the parameter **limit** is not passed, 11th to 2,000th resource records will be returned. The default value of **limit** is **2000**.                          |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit                 | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax (2^31-1). The default value is 2000.                                                                                                                      |
   |                       |                 |                 |                                                                                                                                                                                                                                                             |
   |                       |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                                                                   |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | String          | -  Specifies the enterprise project ID. This field can be used to filter out the VPCs associated with a specified enterprise project.                                                                                                                       |
   |                       |                 |                 | -  The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). Value **0** indicates the default enterprise project. To obtain the VPCs bound to all enterprise projects of the user, set **all_granted_eps**. |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      GET https://{Endpoint}/v1/{project_id}/bandwidths?limit={limit}&marker={marker}

Response Message
----------------

-  Response parameter

   .. table:: **Table 2** Response parameter

      +------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
      | Parameter  | Type                                                                   | Description                                                                                           |
      +============+========================================================================+=======================================================================================================+
      | bandwidths | Array of :ref:`bandwidths <vpc_bandwidth_0002__table17227723>` objects | Specifies the bandwidth objects. For details, see :ref:`Table 3 <vpc_bandwidth_0002__table17227723>`. |
      +------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

   .. _vpc_bandwidth_0002__table17227723:

   .. table:: **Table 3** Description of the **bandwidths** field

      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                                                                      | Description                                                                                                                                                                                                                                                                                           |
      +=======================+===========================================================================+=======================================================================================================================================================================================================================================================================================================+
      | name                  | String                                                                    | -  Specifies the bandwidth name.                                                                                                                                                                                                                                                                      |
      |                       |                                                                           | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                                                                                                                |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size                  | Integer                                                                   | -  Specifies the bandwidth size in Mbit/s.                                                                                                                                                                                                                                                            |
      |                       |                                                                           | -  The value ranges from 1 Mbit/s to 1000 Mbit/s by default. (The specific range may vary depending on the configuration in each region. You can see the bandwidth range of each region on the management console.)                                                                                   |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id                    | String                                                                    | Specifies the bandwidth ID, which uniquely identifies the bandwidth.                                                                                                                                                                                                                                  |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | share_type            | String                                                                    | -  Possible values are as follows:                                                                                                                                                                                                                                                                    |
      |                       |                                                                           |                                                                                                                                                                                                                                                                                                       |
      |                       |                                                                           |    -  **PER**: Dedicated bandwidth                                                                                                                                                                                                                                                                    |
      |                       |                                                                           |    -  **WHOLE**: Shared bandwidth                                                                                                                                                                                                                                                                     |
      |                       |                                                                           |                                                                                                                                                                                                                                                                                                       |
      |                       |                                                                           | If this parameter is not set, the list of all bandwidths will be returned by default.                                                                                                                                                                                                                 |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | publicip_info         | Array of :ref:`publicip_info <vpc_bandwidth_0002__table30936422>` objects | -  Specifies the information about the EIP that uses the bandwidth. For details, see :ref:`Table 4 <vpc_bandwidth_0002__table30936422>`.                                                                                                                                                              |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tenant_id             | String                                                                    | Specifies the project ID.                                                                                                                                                                                                                                                                             |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | bandwidth_type        | String                                                                    | -  Specifies the bandwidth type.                                                                                                                                                                                                                                                                      |
      |                       |                                                                           | -  The value can be:                                                                                                                                                                                                                                                                                  |
      |                       |                                                                           |                                                                                                                                                                                                                                                                                                       |
      |                       |                                                                           |    -  **share**: Shared bandwidth                                                                                                                                                                                                                                                                     |
      |                       |                                                                           |    -  **gray**: Dedicated load balancer                                                                                                                                                                                                                                                               |
      |                       |                                                                           |    -  **bgp**: Dynamic BGP                                                                                                                                                                                                                                                                            |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | charge_mode           | String                                                                    | If the value is **traffic**, the bandwidth is billed by traffic.                                                                                                                                                                                                                                      |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | billing_info          | String                                                                    | Specifies the bill information.                                                                                                                                                                                                                                                                       |
      |                       |                                                                           |                                                                                                                                                                                                                                                                                                       |
      |                       |                                                                           | If **billing_info** is specified, the bandwidth is in yearly/monthly billing mode.                                                                                                                                                                                                                    |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | enterprise_project_id | String                                                                    | -  Specifies the enterprise project ID. The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). Value **0** indicates the default enterprise project. To obtain the bandwidth bound to all enterprise projects of the user, set **all_granted_eps**. |
      |                       |                                                                           | -  When creating a bandwidth, associate the enterprise project ID with the bandwidth.                                                                                                                                                                                                                 |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                                                                    | -  Specifies the bandwidth status.                                                                                                                                                                                                                                                                    |
      |                       |                                                                           | -  Possible values are as follows:                                                                                                                                                                                                                                                                    |
      |                       |                                                                           |                                                                                                                                                                                                                                                                                                       |
      |                       |                                                                           |    -  **FREEZED** (Frozen)                                                                                                                                                                                                                                                                            |
      |                       |                                                                           |    -  **NORMAL** (Normal)                                                                                                                                                                                                                                                                             |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | created_at            | String                                                                    | -  Specifies the time (UTC) when the bandwidth is created.                                                                                                                                                                                                                                            |
      |                       |                                                                           | -  Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                                                                                                                                      |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | updated_at            | String                                                                    | -  Specifies the time (UTC) when the bandwidth is updated.                                                                                                                                                                                                                                            |
      |                       |                                                                           | -  Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                                                                                                                                      |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | public_border_group   | String                                                                    | Specifies whether it is in a central site or an edge site.                                                                                                                                                                                                                                            |
      |                       |                                                                           |                                                                                                                                                                                                                                                                                                       |
      |                       |                                                                           | The value can be:                                                                                                                                                                                                                                                                                     |
      |                       |                                                                           |                                                                                                                                                                                                                                                                                                       |
      |                       |                                                                           | -  center                                                                                                                                                                                                                                                                                             |
      |                       |                                                                           | -  *Edge site name*                                                                                                                                                                                                                                                                                   |
      |                       |                                                                           |                                                                                                                                                                                                                                                                                                       |
      |                       |                                                                           | An EIP can only be bound to a resource of the same region.                                                                                                                                                                                                                                            |
      +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _vpc_bandwidth_0002__table30936422:

   .. table:: **Table 4** **publicip_info** object

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                      |
      +=======================+=======================+==================================================================================================================================+
      | publicip_id           | String                | Specifies the ID of the EIP that uses the bandwidth.                                                                             |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
      | publicip_address      | String                | Specifies the obtained EIP if only IPv4 EIPs are available.                                                                      |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
      | ip_version            | Integer               | -  Specifies the IP address version.                                                                                             |
      |                       |                       | -  Possible values are as follows:                                                                                               |
      |                       |                       |                                                                                                                                  |
      |                       |                       |    -  **4**: IPv4                                                                                                                |
      |                       |                       |    -  **6**: IPv6                                                                                                                |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
      | publicip_type         | String                | -  Specifies the EIP type.                                                                                                       |
      |                       |                       | -  The value can be **5_bgp** (Dynamic BGP), **5_mailbgp** (Mail BGP), **5_gray** (Dedicated Load Balancer), or **5_dualStack**. |
      |                       |                       | -  Constraints:                                                                                                                  |
      |                       |                       |                                                                                                                                  |
      |                       |                       |    -  The configured value must be supported by the system.                                                                      |
      |                       |                       |    -  **publicip_id** is an IPv4 port. If **publicip_type** is not specified, the default value is **5_bgp**.                    |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "bandwidths": [
          {
            "id": "09b99c91-da7c-449f-94e2-f4934c5b2a71",
            "name": "test-f632a7b0-ef50-4ac5-97e9-ddc56b3d5977",
            "size": 200,
            "share_type": "PER",
            "public_border_group": "center",
            "created_at": "2024-04-27T00:14:36Z",
            "updated_at": "2024-04-27T00:14:36Z",
            "publicip_info": [
              {
                "publicip_id": "2a65923c-7133-415d-ae3b-cf9635a942c5",
                "publicip_address": "10.xx.xx.3",
                "ip_version": 4,
                "publicip_type": "5_bgp"
              }
            ],
            "tenant_id": "26ae5181a416420998eb2093aaed84d9",
            "bandwidth_type": "bgp",
            "charge_mode": "traffic",
            "billing_info": "",
            "enterprise_project_id": "0",
            "status": "NORMAL"
          },
          {
            "id": "0a583ff1-b43e-4000-ade3-e7af0097f832",
            "name": "test-7e880d5b-f458-40ad-a7e5-735c44cd8b7d",
            "size": 300,
            "share_type": "PER",
            "public_border_group": "center",
            "created_at": "2024-04-27T00:14:36Z",
            "updated_at": "2024-04-27T00:14:36Z",
            "publicip_info": [
              {
                "publicip_id": "c754bc9a-16d5-4763-9674-d7561917aa80",
                "publicip_address": "10.xx.xx.9",
                "ip_version": 4,
                "publicip_type": "5_bgp"
              }
            ],
            "tenant_id": "26ae5181a416420998eb2093aaed84d9",
            "bandwidth_type": "bgp",
            "charge_mode": "traffic",
            "billing_info": "",
            "enterprise_project_id": "0",
            "status": "NORMAL"
          },
          {
            "id": "0a673f00-3640-4a13-949e-7049b2916baf",
            "name": "bandwidth123",
            "size": 10,
            "share_type": "PER",
            "public_border_group": "center",
            "created_at": "2024-04-27T00:14:36Z",
            "updated_at": "2024-04-27T00:14:36Z",
            "publicip_info": [
              {
                "publicip_id": "cec7fb70-2f82-4561-bd83-2121fb642fdc",
                "publicip_address": "10.xx.xx.184",
                "ip_version": 4,
                "publicip_type": "5_bgp"
              }
            ],
            "tenant_id": "26ae5181a416420998eb2093aaed84d9",
            "bandwidth_type": "bgp",
            "charge_mode": "traffic",
            "billing_info": "",
            "enterprise_project_id": "0",
            "status": "NORMAL"
          },
          {
            "id": "0dde1eae-1783-46dc-998c-930fbe261ff9",
            "name": "bandwidth123",
            "size": 100,
            "share_type": "PER",
            "public_border_group": "center",
            "created_at": "2024-04-27T00:14:36Z",
            "updated_at": "2024-04-27T00:14:36Z",
            "publicip_info": [
              {
                "publicip_id": "24232038-e178-40ad-80e4-5abb75db84be",
                "publicip_address": "10.xx.xx.101",
                "ip_version": 4,
                "publicip_type": "5_bgp"
              }
            ],
            "tenant_id": "26ae5181a416420998eb2093aaed84d9",
            "bandwidth_type": "bgp",
            "charge_mode": "traffic",
            "billing_info": "",
            "enterprise_project_id": "0",
            "status": "NORMAL"
          }
        ]
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
