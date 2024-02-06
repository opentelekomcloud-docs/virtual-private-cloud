:original_name: vpc_apiroutetab_0003.html

.. _vpc_apiroutetab_0003:

Creating a Route Table
======================

Function
--------

This API is used to create a route table.

Notes and Constraints

-  The destination CIDR block of a custom route table cannot be included in the CIDR blocks of the local route.
-  Each destination CIDR block of a route in the same route table must be unique.
-  No more than five routes can be created at a time.

URI
---

POST /v1/{project_id}/routetables

:ref:`Table 1 <vpc_apiroutetab_0003__table1211341604611>` describes the parameters.

.. _vpc_apiroutetab_0003__table1211341604611:

.. table:: **Table 1** Parameter description

   ========== ========= ====== =========================
   Name       Mandatory Type   Description
   ========== ========= ====== =========================
   project_id Yes       String Specifies the project ID.
   ========== ========= ====== =========================

Request Parameters
------------------

.. table:: **Table 2** Request parameter

   +------------+-----------+----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Name       | Mandatory | Type                                                                 | Description                                                                                             |
   +============+===========+======================================================================+=========================================================================================================+
   | routetable | Yes       | :ref:`routetable <vpc_apiroutetab_0003__table18269181620462>` object | Specifies the route table. For details, see :ref:`Table 3 <vpc_apiroutetab_0003__table18269181620462>`. |
   +------------+-----------+----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0003__table18269181620462:

.. table:: **Table 3** Description of the **routetable** field

   +-----------------+-----------------+--------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type                                                                     | Description                                                                                                                    |
   +=================+=================+==========================================================================+================================================================================================================================+
   | name            | No              | String                                                                   | -  Specifies the route table name.                                                                                             |
   |                 |                 |                                                                          | -  The value can contain no more than 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.). |
   +-----------------+-----------------+--------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | routes          | No              | Array of :ref:`route <vpc_apiroutetab_0003__table1539412169467>` objects | -  Specifies the route list. For details, see :ref:`Table 4 <vpc_apiroutetab_0003__table1539412169467>`.                       |
   |                 |                 |                                                                          | -  Each route table can have a maximum of 200 routes.                                                                          |
   +-----------------+-----------------+--------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id          | Yes             | String                                                                   | -  Specifies the ID of the VPC associated with the route table.                                                                |
   +-----------------+-----------------+--------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String                                                                   | -  Provides supplementary information about the route table.                                                                   |
   |                 |                 |                                                                          | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                               |
   +-----------------+-----------------+--------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0003__table1539412169467:

.. table:: **Table 4** Description of the **route** field

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                      |
   +=================+=================+=================+==================================================================================================+
   | type            | Yes             | String          | -  Specifies the route type.                                                                     |
   |                 |                 |                 | -  Values:                                                                                       |
   |                 |                 |                 |                                                                                                  |
   |                 |                 |                 |    -  **ecs** (ECS)                                                                              |
   |                 |                 |                 |    -  **eni** (NIC)                                                                              |
   |                 |                 |                 |    -  **vip** (Virtual IP address)                                                               |
   |                 |                 |                 |    -  **nat** (NAT gateway)                                                                      |
   |                 |                 |                 |    -  **peering** (VPC peering connection)                                                       |
   |                 |                 |                 |    -  **vpn** (VPN)                                                                              |
   |                 |                 |                 |    -  **dc** (Direct Connect connection)                                                         |
   |                 |                 |                 |    -  **egw**: VPC endpoint node                                                                 |
   |                 |                 |                 |    -  **er**: enterprise router                                                                  |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
   | destination     | Yes             | String          | -  Specifies the destination CIDR block of a route.                                              |
   |                 |                 |                 | -  The value must be in the valid CIDR format.                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
   | nexthop         | Yes             | String          | -  Specifies the ID of the next hop in the route.                                                |
   |                 |                 |                 | -  Values:                                                                                       |
   |                 |                 |                 |                                                                                                  |
   |                 |                 |                 |    -  When **type** is **ecs**, the value is the ECS ID.                                         |
   |                 |                 |                 |    -  When **type** is **eni**, the value is the extension NIC ID.                               |
   |                 |                 |                 |    -  When **type** is **vip**, the value is the virtual IP address.                             |
   |                 |                 |                 |    -  When **type** is **nat**, the value is NAT gateway ID.                                     |
   |                 |                 |                 |    -  When **type** is **peering**, the value is the VPC peering connection ID.                  |
   |                 |                 |                 |    -  When **type** is **vpn**, the value is the VPN ID.                                         |
   |                 |                 |                 |    -  When **type** is **dc**, the value is the Direct Connect connection ID.                    |
   |                 |                 |                 |    -  When **type** is set to **egw**, the value is the VPC endpoint ID.                         |
   |                 |                 |                 |    -  When **type** is set to **er**, the value is the ID of the enterprise router.              |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
   | description     | No              | String          | -  Provides supplementary information about the route.                                           |
   |                 |                 |                 | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+

Example Request
---------------

-  Create a route table named **routetable-1234** for the VPC whose ID is 60c809cb-6731-45d0-ace8-3bf5626421a9 and create a route with next hop type of ECS.

   .. code-block:: text

      POST https://{Endpoint}/v1/6fbe9263116a4b68818cf1edce16bc4f/routetables

      {
          "routetable": {
              "name": "routetable-1234",
              "vpc_id": "60c809cb-6731-45d0-ace8-3bf5626421a9",
              "routes":[
                {
                  "type": "ecs",
                  "destination": "10.10.10.0/24",
                  "nexthop":"7c50463d-d36c-4417-aa85-cc11fa10f341"
                }
             ],
              "description":"abc"
          }
      }

Response Parameters
-------------------

.. table:: **Table 5** Response parameter

   +------------+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Name       | Type                                                               | Description                                                                                           |
   +============+====================================================================+=======================================================================================================+
   | routetable | :ref:`routetable <vpc_apiroutetab_0003__table884119412392>` object | Specifies the route table. For details, see :ref:`Table 6 <vpc_apiroutetab_0003__table884119412392>`. |
   +------------+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0003__table884119412392:

.. table:: **Table 6** Description of the **routetable** field

   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Type                                                                       | Description                                                                                                                            |
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
   | routes                | Array of :ref:`route <vpc_apiroutetab_0002__table1687317463915>` objects   | -  Specifies the route list. For details, see :ref:`Table 4 <vpc_apiroutetab_0002__table1687317463915>`.                               |
   |                       |                                                                            | -  Each route table can have a maximum of 200 routes.                                                                                  |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | subnets               | Array of :ref:`subnet <vpc_apiroutetab_0002__table17950204203919>` objects | -  Specifies the subnets associated with the route table. For details, see :ref:`Table 5 <vpc_apiroutetab_0002__table17950204203919>`. |
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
