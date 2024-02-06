:original_name: vpc_apiroutetab_0007.html

.. _vpc_apiroutetab_0007:

Disassociating Subnets from a Route Table
=========================================

Function
--------

This API is used to disassociate subnets from a route table.

For details, see `Associating a Route Table with a Subnet <https://docs.otc.t-systems.com/virtual-private-cloud/umn/route_tables/associating_a_route_table_with_a_subnet.html>`__.

URI
---

POST /v1/{project_id}/routetables/{routetable_id}/action

:ref:`Table 1 <vpc_apiroutetab_0007__table125312228469>` describes the parameters.

.. _vpc_apiroutetab_0007__table125312228469:

.. table:: **Table 1** Parameter description

   +---------------+-----------+--------+------------------------------------------------------------------------+
   | Name          | Mandatory | Type   | Description                                                            |
   +===============+===========+========+========================================================================+
   | project_id    | Yes       | String | Specifies the project ID.                                              |
   +---------------+-----------+--------+------------------------------------------------------------------------+
   | routetable_id | Yes       | String | Specifies the route table ID, which uniquely identifies a route table. |
   +---------------+-----------+--------+------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request parameter

   +------------+-----------+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Name       | Mandatory | Type                                                               | Description                                                                                           |
   +============+===========+====================================================================+=======================================================================================================+
   | routetable | Yes       | :ref:`routetable <vpc_apiroutetab_0007__table104243226461>` object | Specifies the route table. For details, see :ref:`Table 3 <vpc_apiroutetab_0007__table104243226461>`. |
   +------------+-----------+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0007__table104243226461:

.. table:: **Table 3** Description of the **routetable** field

   +-----------------+-----------------+------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type                                                             | Description                                                                                                                      |
   +=================+=================+==================================================================+==================================================================================================================================+
   | subnets         | Yes             | :ref:`subnet <vpc_apiroutetab_0007__table12518142212468>` object | -  Specifies the subnets associated with the route table.                                                                        |
   |                 |                 |                                                                  | -  Only subnets (specified by **network_id**) in the VPC that the route table belongs to can be associated with the route table. |
   +-----------------+-----------------+------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0007__table12518142212468:

.. table:: **Table 4** Description of the **subnet** field

   +--------------+-----------+------------------+----------------------------------------------------------------------------+
   | Name         | Mandatory | Type             | Description                                                                |
   +==============+===========+==================+============================================================================+
   | associate    | No        | Array of strings | Specifies the IDs of the subnets to be associated with the route table.    |
   +--------------+-----------+------------------+----------------------------------------------------------------------------+
   | disassociate | No        | Array of strings | Specifies the IDs of the subnets to be disassociated from the route table. |
   +--------------+-----------+------------------+----------------------------------------------------------------------------+

Example Request
---------------

-  Disassociate route table 3d42a0d4-a980-4613-ae76-a2cddecff054 from subnet 815a6b9e-f766-48eb-967c-0ada72d85435.

   .. code-block:: text

      POST https://{Endpoint}/v1/6fbe9263116a4b68818cf1edce16bc4f/routetables/3d42a0d4-a980-4613-ae76-a2cddecff054/action

      {
          "routetable": {
              "subnets": {
                  "disassociate": [
                      "815a6b9e-f766-48eb-967c-0ada72d85435"
                  ]
              }
          }
      }

Response Parameters
-------------------

.. table:: **Table 5** Response parameter

   +------------+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Name       | Type                                                               | Description                                                                                           |
   +============+====================================================================+=======================================================================================================+
   | routetable | :ref:`routetable <vpc_apiroutetab_0007__table884119412392>` object | Specifies the route table. For details, see :ref:`Table 6 <vpc_apiroutetab_0007__table884119412392>`. |
   +------------+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0007__table884119412392:

.. table:: **Table 6** Description of the **routetable** field

   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                       | Description                                                                                                                            |
   +=======================+============================================================================+========================================================================================================================================+
   | id                    | String                                                                     | -  Specifies the route table ID, which uniquely identifies the route table.                                                            |
   |                       |                                                                            | -  The value must be in standard UUID format.                                                                                          |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                     | -  Specifies the route table name.                                                                                                     |
   |                       |                                                                            | -  The value can contain no more than 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).         |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | default               | Boolean                                                                    | -  Specifies whether the route table is the default one.                                                                               |
   |                       |                                                                            | -  The value can be **true** (default route table) or **false** (custom route table).                                                  |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | routes                | Array of :ref:`route <vpc_apiroutetab_0007__table1687317463915>` objects   | -  Specifies the route list. For details, see :ref:`Table 7 <vpc_apiroutetab_0007__table1687317463915>`.                               |
   |                       |                                                                            | -  Each route table can have a maximum of 200 routes.                                                                                  |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | subnets               | Array of :ref:`subnet <vpc_apiroutetab_0007__table17950204203919>` objects | -  Specifies the subnets associated with the route table. For details, see :ref:`Table 8 <vpc_apiroutetab_0007__table17950204203919>`. |
   |                       |                                                                            | -  Only subnets in the VPC to which the route table belongs can be associated with the route table.                                    |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                                                                     | -  Specifies the project ID.                                                                                                           |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id                | String                                                                     | -  Specifies the ID of the VPC associated with the route table.                                                                        |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                     | -  Provides supplementary information about the route table.                                                                           |
   |                       |                                                                            | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                       |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                     | -  Specifies the time (UTC) when the route table is created.                                                                           |
   |                       |                                                                            | -  Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                       |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                     | -  Specifies the time (UTC) when the route table is updated.                                                                           |
   |                       |                                                                            | -  Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                       |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0007__table1687317463915:

.. table:: **Table 7** Description of the **route** field

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | Name                  | Type                  | Description                                                                                      |
   +=======================+=======================+==================================================================================================+
   | type                  | String                | -  Specifies the route type.                                                                     |
   |                       |                       | -  Values:                                                                                       |
   |                       |                       |                                                                                                  |
   |                       |                       |    -  **ecs** (ECS)                                                                              |
   |                       |                       |    -  **eni** (NIC)                                                                              |
   |                       |                       |    -  **vip** (Virtual IP address)                                                               |
   |                       |                       |    -  **nat** (NAT gateway)                                                                      |
   |                       |                       |    -  **peering** (VPC peering connection)                                                       |
   |                       |                       |    -  **vpn** (VPN)                                                                              |
   |                       |                       |    -  **dc** (Direct Connect connection)                                                         |
   |                       |                       |    -  **egw**: VPC endpoint node                                                                 |
   |                       |                       |    -  **er**: enterprise router                                                                  |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | destination           | String                | -  Specifies the destination CIDR block of a route.                                              |
   |                       |                       | -  The value must be in the valid CIDR format.                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | nexthop               | String                | -  Specifies the ID of the next hop in the route.                                                |
   |                       |                       | -  Values:                                                                                       |
   |                       |                       |                                                                                                  |
   |                       |                       |    -  When **type** is **ecs**, the value is the ECS ID.                                         |
   |                       |                       |    -  When **type** is **eni**, the value is the extension NIC ID.                               |
   |                       |                       |    -  When **type** is **vip**, the value is the virtual IP address.                             |
   |                       |                       |    -  When **type** is **nat**, the value is NAT gateway ID.                                     |
   |                       |                       |    -  When **type** is **peering**, the value is the VPC peering connection ID.                  |
   |                       |                       |    -  When **type** is **vpn**, the value is the VPN ID.                                         |
   |                       |                       |    -  When **type** is **dc**, the value is the Direct Connect connection ID.                    |
   |                       |                       |    -  When **type** is set to **egw**, the value is the VPC endpoint ID.                         |
   |                       |                       |    -  When **type** is set to **er**, the value is the ID of the enterprise router.              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | description           | String                | -  Provides supplementary information about the route.                                           |
   |                       |                       | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >). |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0007__table17950204203919:

.. table:: **Table 8** Description of the **subnet** field

   +------+--------+-----------------------------------------------------------------+
   | Name | Type   | Description                                                     |
   +======+========+=================================================================+
   | id   | String | Specifies the ID of the subnet associated with the route table. |
   +------+--------+-----------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "routetable": {
           "id": "3d42a0d4-a980-4613-ae76-a2cddecff054",
           "vpc_id": "ab78be2d-782f-42a5-aa72-35879f6890ff",
           "description": "abc",
           "routes": [
               {
                   "type": "ecs",
                   "destination": "10.10.10.0/24",
                   "nexthop": "7c50463d-d36c-4417-aa85-cc11fa10f341",
                   "description": "abc"
               }
           ],
           "subnets": [
               {
                   "id": "8d4ce32f-d68a-4c4c-9f18-c68d8a5c7f2f"
               }
           ],
           "tenant_id": "6fbe9263116a4b68818cf1edce16bc4f"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
