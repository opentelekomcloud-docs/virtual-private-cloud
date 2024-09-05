:original_name: vpc_apiroutetab_0001.html

.. _vpc_apiroutetab_0001:

Querying Route Tables
=====================

Function
--------

This API is used to query route tables.

URI
---

GET /v1/{project_id}/routetables

Example:

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/routetables?limit=10&marker=4779ab1c-7c1a-44b1-a02e-93dfc361b32d&vpc_id=3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85&subnet_id=9873b33f-ac1c-4630-ad1c-7dba1ed79r78

:ref:`Table 1 <vpc_apiroutetab_0001__table135921530121310>` describes the parameters.

.. _vpc_apiroutetab_0001__table135921530121310:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================+
   | project_id      | Yes             | String          | Specifies the project ID.                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax (2^31-1). The default value is 2000.                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Specifies a resource ID for pagination query, indicating that the query starts from the next record of the specified resource ID.                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | This parameter can work together with the parameter **limit**.                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | -  If parameters **marker** and **limit** are not passed, resource records on the first page will be returned.                                                                                                         |
   |                 |                 |                 | -  If the parameter **marker** is not passed and the value of parameter **limit** is set to **10**, the first 10 resource records will be returned.                                                                    |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the value of parameter **limit** is set to **10**, the 11th to 20th resource records will be returned.                    |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the parameter **limit** is not passed, resource records starting from the 11th records (including 11th) will be returned. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id              | No              | String          | Specifies the route table ID that is used as the filter.                                                                                                                                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id          | No              | String          | Specifies the VPC UUID that is used as the filter.                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnet_id       | No              | String          | Specifies the subnet UUID that is used as the filter.                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | If you use the management console, the value of this parameter is the **Network ID** value.                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/routetables?limit=10&marker=4779ab1c-7c1a-44b1-a02e-93dfc361b32d&vpc_id=3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85&subnet_id=9873b33f-ac1c-4630-ad1c-7dba1ed79r78

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type                                                                          | Description                                                                                                 |
   +=============+===============================================================================+=============================================================================================================+
   | routetables | Array of :ref:`routetable <vpc_apiroutetab_0001__table5685153016131>` objects | Specifies the route table list. For details, see :ref:`Table 3 <vpc_apiroutetab_0001__table5685153016131>`. |
   +-------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0001__table5685153016131:

.. table:: **Table 3** Description of the **routetable** field

   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                      | Description                                                                                                                           |
   +=======================+===========================================================================+=======================================================================================================================================+
   | id                    | String                                                                    | -  Specifies the route table ID that uniquely identifies a route table.                                                               |
   |                       |                                                                           | -  The value must be in standard UUID format.                                                                                         |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                    | -  Specifies the route table name.                                                                                                    |
   |                       |                                                                           | -  The value can contain up to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).               |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | default               | Boolean                                                                   | -  Specifies whether the route table is the default one.                                                                              |
   |                       |                                                                           | -  The value can be **true** (default route table) or **false** (custom route table).                                                 |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | routes                | Array of :ref:`route <vpc_apiroutetab_0001__table1687317463915>` objects  | -  Specifies the route list. For details, see :ref:`Table 4 <vpc_apiroutetab_0001__table1687317463915>`.                              |
   |                       |                                                                           | -  Each route table can have a maximum of 200 routes.                                                                                 |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | subnets               | Array of :ref:`subnet <vpc_apiroutetab_0001__table4856530131313>` objects | -  Specifies the subnets associated with the route table. For details, see :ref:`Table 5 <vpc_apiroutetab_0001__table4856530131313>`. |
   |                       |                                                                           | -  Only subnets in the VPC to which the route table belongs can be associated with the route table.                                   |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                                                                    | -  Specifies the project ID.                                                                                                          |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id                | String                                                                    | -  Specifies the ID of the VPC associated with the route table.                                                                       |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                    | -  Provides supplementary information about the route table.                                                                          |
   |                       |                                                                           | -  The value can contain up to 255 characters and cannot contain angle brackets (< or >).                                             |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                    | -  Specifies the time (UTC) when the route table is created.                                                                          |
   |                       |                                                                           | -  Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                      |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                    | -  Specifies the time (UTC) when the route table is updated.                                                                          |
   |                       |                                                                           | -  Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                      |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0001__table1687317463915:

.. table:: **Table 4** Description of the **route** field

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                             |
   +=======================+=======================+=========================================================================================================================================+
   | type                  | String                | -  Specifies the route type.                                                                                                            |
   |                       |                       | -  Values:                                                                                                                              |
   |                       |                       |                                                                                                                                         |
   |                       |                       |    -  **ecs** (ECS)                                                                                                                     |
   |                       |                       |    -  **eni** (NIC)                                                                                                                     |
   |                       |                       |    -  **vip** (Virtual IP address)                                                                                                      |
   |                       |                       |    -  **nat** (NAT gateway)                                                                                                             |
   |                       |                       |    -  **peering** (VPC peering connection)                                                                                              |
   |                       |                       |    -  **vpn** (VPN)                                                                                                                     |
   |                       |                       |    -  **dc** (Direct Connect connection)                                                                                                |
   |                       |                       |    -  **egw**: VPC endpoint. This route type is not supported.                                                                          |
   |                       |                       |    -  **er**: enterprise router                                                                                                         |
   |                       |                       |    -  **subeni**: supplementary network interface. This type of route cannot be created or updated by users.                            |
   |                       |                       |    -  **local**: reserved CIDR block. The destination CIDR block of the route configured cannot overlap with that defined by **local**. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | destination           | String                | -  Specifies the destination CIDR block of a route.                                                                                     |
   |                       |                       | -  Constraints: The value must be in valid IPv4 or IPv6 CIDR formats.                                                                   |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | nexthop               | String                | -  Specifies the ID of the next hop in the route.                                                                                       |
   |                       |                       | -  Values:                                                                                                                              |
   |                       |                       |                                                                                                                                         |
   |                       |                       |    -  When **type** is **ecs**, the value is an ECS ID.                                                                                 |
   |                       |                       |    -  When **type** is **eni**, the value is an extension NIC ID.                                                                       |
   |                       |                       |    -  When **type** is **vip**, the value is a virtual IP address.                                                                      |
   |                       |                       |    -  When **type** is **nat**, the value a NAT gateway ID.                                                                             |
   |                       |                       |    -  When **type** is **peering**, the value is a VPC peering connection ID.                                                           |
   |                       |                       |    -  When **type** is **vpn**, the value is a VPN ID.                                                                                  |
   |                       |                       |    -  When **type** is **dc**, the value is a Direct Connect connection ID.                                                             |
   |                       |                       |    -  When **type** is set to **egw**, the value is a VPC endpoint ID.                                                                  |
   |                       |                       |    -  When **type** is set to **er**, the value is the ID of an enterprise router.                                                      |
   |                       |                       |    -  When **type** is set to **subeni**, the value is the ID of a supplementary network interface.                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | -  Provides supplementary information about the route.                                                                                  |
   |                       |                       | -  The value can contain up to 255 characters and cannot contain angle brackets (< or >).                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0001__table4856530131313:

.. table:: **Table 5** Description of the **subnet** field

   +-----------+--------+-----------------------------------------------------------------+
   | Parameter | Type   | Description                                                     |
   +===========+========+=================================================================+
   | id        | String | Specifies the ID of the subnet associated with the route table. |
   +-----------+--------+-----------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "routetables": [
           {
               "id": "3d42a0d4-a980-4613-ae76-a2cddecff054",
               "name": "routetable-1234",
               "vpc_id": "ab78be2d-782f-42a5-aa72-35879f6890ff",
               "routes": [
                  {
                   "type": "local",
                   "destination": "192.168.4.0/24",
                   "nexthop": "-"
                  },
                  {
                   "type": "local",
                   "destination": "192.168.1.0/24",
                   "nexthop": "-"
                  },
                  {
                   "type": "local",
                   "destination": "198.19.128.0/20",
                   "nexthop": "-"
                  },
                  {
                   "type": "local",
                   "destination": "127.0.0.0/8",
                   "nexthop": "-"
                  },
                  {
                   "type": "local",
                   "destination": "100.64.0.0/10",
                   "nexthop": "-"
                  }
               ],
               "subnets": [
                   {
                       "id": "8d4ce32f-d68a-4c4c-9f18-c68d8a5c7f2f"
                   }
               ],
               "tenant_id": "6fbe9263116a4b68818cf1edce16bc4f",
               "description": "abc",
               "created_at": "2022-12-15T02:56:40",
               "updated_at": "2022-12-15T02:56:40"
           },
           {
               "id": "3d42a0d4-a980-4613-ae76-a2cddecfff89",
               "name": "routetable-5678",
               "vpc_id": "ab78be2d-782f-42a5-aa72-35879f667809",
               "routes": [
                  {
                   "type": "local",
                   "destination": "192.168.4.0/24",
                   "nexthop": "-"
                  },
                  {
                   "type": "local",
                   "destination": "192.168.1.0/24",
                   "nexthop": "-"
                  },
                  {
                   "type": "local",
                   "destination": "198.19.128.0/20",
                   "nexthop": "-"
                  },
                  {
                   "type": "local",
                   "destination": "127.0.0.0/8",
                   "nexthop": "-"
                  },
                  {
                   "type": "local",
                   "destination": "100.64.0.0/10",
                   "nexthop": "-"
                  }
               ],
               "subnets": [
                   {
                       "id": "8d4ce32f-d68a-4c4c-9f18-c68d8a5c7f2f"
                   }
               ],
               "tenant_id": "6fbe9263116a4b68818cf1edce16bc4f",
               "description": "abc",
               "created_at": "2022-12-15T02:59:03",
               "updated_at": "2022-12-15T02:59:03"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
