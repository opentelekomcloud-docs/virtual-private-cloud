:original_name: vpc_apiroutetab_0004.html

.. _vpc_apiroutetab_0004:

Updating a Route Table
======================

Function
--------

This API is used to update a route table.

URI
---

PUT /v1/{project_id}/routetables/{routetable_id}

:ref:`Table 1 <vpc_apiroutetab_0004__table13791152173213>` describes the parameters.

.. _vpc_apiroutetab_0004__table13791152173213:

.. table:: **Table 1** Parameter description

   +---------------+-----------+--------+----------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                          |
   +===============+===========+========+======================================================================+
   | project_id    | Yes       | String | Specifies the project ID.                                            |
   +---------------+-----------+--------+----------------------------------------------------------------------+
   | routetable_id | Yes       | String | Specifies the route table ID that uniquely identifies a route table. |
   +---------------+-----------+--------+----------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request parameter

   +------------+-----------+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type                                                               | Description                                                                                           |
   +============+===========+====================================================================+=======================================================================================================+
   | routetable | Yes       | :ref:`routetable <vpc_apiroutetab_0004__table188071229326>` object | Specifies the route table. For details, see :ref:`Table 3 <vpc_apiroutetab_0004__table188071229326>`. |
   +------------+-----------+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0004__table188071229326:

.. table:: **Table 3** Description of the **routetable** field

   +-----------------+-----------------+-------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                      | Description                                                                                                                                                                               |
   +=================+=================+===========================================================================================+===========================================================================================================================================================================================+
   | name            | No              | String                                                                                    | -  Specifies the route table name.                                                                                                                                                        |
   |                 |                 |                                                                                           | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                                    |
   +-----------------+-----------------+-------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String                                                                                    | -  Provides supplementary information about the route.                                                                                                                                    |
   |                 |                 |                                                                                           | -  The value can contain up to 255 characters and cannot contain angle brackets (< or >).                                                                                                 |
   +-----------------+-----------------+-------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | routes          | No              | :ref:`RouteTableRouteAction <vpc_apiroutetab_0004__request_routetablerouteaction>` object | -  Specifies the route list. For details, see :ref:`Table 4 <vpc_apiroutetab_0004__request_routetablerouteaction>`.                                                                       |
   |                 |                 |                                                                                           | -  Constraints:                                                                                                                                                                           |
   |                 |                 |                                                                                           |                                                                                                                                                                                           |
   |                 |                 |                                                                                           |    -  Each route table can have a maximum of 200 routes.                                                                                                                                  |
   |                 |                 |                                                                                           |    -  The destination cannot be modified directly. To modify the destination, run the **del** command to delete the corresponding route, and then run the **add** command to add a route. |
   |                 |                 |                                                                                           |                                                                                                                                                                                           |
   |                 |                 |                                                                                           | -  Specifies the operation to perform. Possible values are as follows:                                                                                                                    |
   |                 |                 |                                                                                           |                                                                                                                                                                                           |
   |                 |                 |                                                                                           |    -  **add**: Adds a route. Parameters **type**, **destination**, and **nexthop** are mandatory.                                                                                         |
   |                 |                 |                                                                                           |    -  **mod**: Modifies a route. Parameters **type**, **destination**, and **nexthop** are mandatory.                                                                                     |
   |                 |                 |                                                                                           |    -  **del**: Deletes a route. Parameter **destination** is mandatory.                                                                                                                   |
   +-----------------+-----------------+-------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0004__request_routetablerouteaction:

.. table:: **Table 4** Description of the **route** field

   +-----------------+-----------------+----------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                   | Description                                                                                   |
   +=================+=================+========================================================================================+===============================================================================================+
   | add             | No              | Array of :ref:`AddRouteTableRoute <vpc_apiroutetab_0004__table11648235202119>` objects | Adds a route. For details, see :ref:`Table 5 <vpc_apiroutetab_0004__table11648235202119>`.    |
   |                 |                 |                                                                                        |                                                                                               |
   |                 |                 |                                                                                        | Parameters **type**, **destination**, and **nexthop** are mandatory.                          |
   +-----------------+-----------------+----------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | mod             | No              | Array of :ref:`ModRouteTableRoute <vpc_apiroutetab_0004__table1294364718262>` objects  | Modifies a route. For details, see :ref:`Table 6 <vpc_apiroutetab_0004__table1294364718262>`. |
   |                 |                 |                                                                                        |                                                                                               |
   |                 |                 |                                                                                        | Parameters **type**, **destination**, and **nexthop** are mandatory.                          |
   +-----------------+-----------------+----------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | del             | No              | Array of :ref:`DelRouteTableRoute <vpc_apiroutetab_0004__table27171519267>` objects    | Deletes a route. For details, see :ref:`Table 7 <vpc_apiroutetab_0004__table27171519267>`.    |
   |                 |                 |                                                                                        |                                                                                               |
   |                 |                 |                                                                                        | Parameter **destination** is mandatory.                                                       |
   +-----------------+-----------------+----------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0004__table11648235202119:

.. table:: **Table 5** Field description of adding a route

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================+
   | type            | Yes             | String          | -  Specifies the route type.                                                                                                            |
   |                 |                 |                 | -  Values:                                                                                                                              |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 |    -  **ecs** (ECS)                                                                                                                     |
   |                 |                 |                 |    -  **eni** (NIC)                                                                                                                     |
   |                 |                 |                 |    -  **vip** (Virtual IP address)                                                                                                      |
   |                 |                 |                 |    -  **nat** (NAT gateway)                                                                                                             |
   |                 |                 |                 |    -  **peering** (VPC peering connection)                                                                                              |
   |                 |                 |                 |    -  **vpn** (VPN)                                                                                                                     |
   |                 |                 |                 |    -  **dc** (Direct Connect connection)                                                                                                |
   |                 |                 |                 |    -  **egw**: VPC endpoint. This route type is not supported.                                                                          |
   |                 |                 |                 |    -  **er**: enterprise router                                                                                                         |
   |                 |                 |                 |    -  **subeni**: supplementary network interface. This type of route cannot be created or updated by users.                            |
   |                 |                 |                 |    -  **local**: reserved CIDR block. The destination CIDR block of the route configured cannot overlap with that defined by **local**. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | destination     | Yes             | String          | -  Specifies the destination CIDR block of a route.                                                                                     |
   |                 |                 |                 | -  Constraints: The value must be in valid IPv4 or IPv6 CIDR formats.                                                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | nexthop         | Yes             | String          | -  Specifies the ID of the next hop in the route.                                                                                       |
   |                 |                 |                 | -  Values:                                                                                                                              |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 |    -  When **type** is **ecs**, the value is an ECS ID.                                                                                 |
   |                 |                 |                 |    -  When **type** is **eni**, the value is an extension NIC ID.                                                                       |
   |                 |                 |                 |    -  When **type** is **vip**, the value is a virtual IP address.                                                                      |
   |                 |                 |                 |    -  When **type** is **nat**, the value a NAT gateway ID.                                                                             |
   |                 |                 |                 |    -  When **type** is **peering**, the value is a VPC peering connection ID.                                                           |
   |                 |                 |                 |    -  When **type** is **vpn**, the value is a VPN ID.                                                                                  |
   |                 |                 |                 |    -  When **type** is **dc**, the value is a Direct Connect connection ID.                                                             |
   |                 |                 |                 |    -  When **type** is set to **egw**, the value is a VPC endpoint ID.                                                                  |
   |                 |                 |                 |    -  When **type** is set to **er**, the value is the ID of an enterprise router.                                                      |
   |                 |                 |                 |    -  When **type** is set to **subeni**, the value is the ID of a supplementary network interface.                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | -  Provides supplementary information about the route.                                                                                  |
   |                 |                 |                 | -  The value can contain up to 255 characters and cannot contain angle brackets (< or >).                                               |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0004__table1294364718262:

.. table:: **Table 6** Field description of modifying a route

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================+
   | type            | Yes             | String          | -  Specifies the route type.                                                                                                            |
   |                 |                 |                 | -  Values:                                                                                                                              |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 |    -  **ecs** (ECS)                                                                                                                     |
   |                 |                 |                 |    -  **eni** (NIC)                                                                                                                     |
   |                 |                 |                 |    -  **vip** (Virtual IP address)                                                                                                      |
   |                 |                 |                 |    -  **nat** (NAT gateway)                                                                                                             |
   |                 |                 |                 |    -  **peering** (VPC peering connection)                                                                                              |
   |                 |                 |                 |    -  **vpn** (VPN)                                                                                                                     |
   |                 |                 |                 |    -  **dc** (Direct Connect connection)                                                                                                |
   |                 |                 |                 |    -  **egw**: VPC endpoint. This route type is not supported.                                                                          |
   |                 |                 |                 |    -  **er**: enterprise router                                                                                                         |
   |                 |                 |                 |    -  **subeni**: supplementary network interface. This type of route cannot be created or updated by users.                            |
   |                 |                 |                 |    -  **local**: reserved CIDR block. The destination CIDR block of the route configured cannot overlap with that defined by **local**. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | destination     | Yes             | String          | -  Specifies the destination CIDR block of a route.                                                                                     |
   |                 |                 |                 | -  Constraints: The value must be in valid IPv4 or IPv6 CIDR formats.                                                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | nexthop         | Yes             | String          | -  Specifies the ID of the next hop in the route.                                                                                       |
   |                 |                 |                 | -  Values:                                                                                                                              |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 |    -  When **type** is **ecs**, the value is an ECS ID.                                                                                 |
   |                 |                 |                 |    -  When **type** is **eni**, the value is an extension NIC ID.                                                                       |
   |                 |                 |                 |    -  When **type** is **vip**, the value is a virtual IP address.                                                                      |
   |                 |                 |                 |    -  When **type** is **nat**, the value a NAT gateway ID.                                                                             |
   |                 |                 |                 |    -  When **type** is **peering**, the value is a VPC peering connection ID.                                                           |
   |                 |                 |                 |    -  When **type** is **vpn**, the value is a VPN ID.                                                                                  |
   |                 |                 |                 |    -  When **type** is **dc**, the value is a Direct Connect connection ID.                                                             |
   |                 |                 |                 |    -  When **type** is set to **egw**, the value is a VPC endpoint ID.                                                                  |
   |                 |                 |                 |    -  When **type** is set to **er**, the value is the ID of an enterprise router.                                                      |
   |                 |                 |                 |    -  When **type** is set to **subeni**, the value is the ID of a supplementary network interface.                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | -  Provides supplementary information about the route.                                                                                  |
   |                 |                 |                 | -  The value can contain up to 255 characters and cannot contain angle brackets (< or >).                                               |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0004__table27171519267:

.. table:: **Table 7** Field description of deleting a route

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================+
   | type            | No              | String          | -  Specifies the route type.                                                                                                            |
   |                 |                 |                 | -  Values:                                                                                                                              |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 |    -  **ecs** (ECS)                                                                                                                     |
   |                 |                 |                 |    -  **eni** (NIC)                                                                                                                     |
   |                 |                 |                 |    -  **vip** (Virtual IP address)                                                                                                      |
   |                 |                 |                 |    -  **nat** (NAT gateway)                                                                                                             |
   |                 |                 |                 |    -  **peering** (VPC peering connection)                                                                                              |
   |                 |                 |                 |    -  **vpn** (VPN)                                                                                                                     |
   |                 |                 |                 |    -  **dc** (Direct Connect connection)                                                                                                |
   |                 |                 |                 |    -  **egw**: VPC endpoint. This route type is not supported.                                                                          |
   |                 |                 |                 |    -  **er**: enterprise router                                                                                                         |
   |                 |                 |                 |    -  **subeni**: supplementary network interface. This type of route cannot be created or updated by users.                            |
   |                 |                 |                 |    -  **local**: reserved CIDR block. The destination CIDR block of the route configured cannot overlap with that defined by **local**. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | destination     | Yes             | String          | -  Specifies the destination CIDR block of a route.                                                                                     |
   |                 |                 |                 | -  Constraints: The value must be in valid IPv4 or IPv6 CIDR formats.                                                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | nexthop         | No              | String          | -  Specifies the ID of the next hop in the route.                                                                                       |
   |                 |                 |                 | -  Values:                                                                                                                              |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 |    -  When **type** is **ecs**, the value is an ECS ID.                                                                                 |
   |                 |                 |                 |    -  When **type** is **eni**, the value is an extension NIC ID.                                                                       |
   |                 |                 |                 |    -  When **type** is **vip**, the value is a virtual IP address.                                                                      |
   |                 |                 |                 |    -  When **type** is **nat**, the value a NAT gateway ID.                                                                             |
   |                 |                 |                 |    -  When **type** is **peering**, the value is a VPC peering connection ID.                                                           |
   |                 |                 |                 |    -  When **type** is **vpn**, the value is a VPN ID.                                                                                  |
   |                 |                 |                 |    -  When **type** is **dc**, the value is a Direct Connect connection ID.                                                             |
   |                 |                 |                 |    -  When **type** is set to **egw**, the value is a VPC endpoint ID.                                                                  |
   |                 |                 |                 |    -  When **type** is set to **er**, the value is the ID of an enterprise router.                                                      |
   |                 |                 |                 |    -  When **type** is set to **subeni**, the value is the ID of a supplementary network interface.                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | -  Provides supplementary information about the route.                                                                                  |
   |                 |                 |                 | -  The value can contain up to 255 characters and cannot contain angle brackets (< or >).                                               |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  Change the route table whose ID is 3d42a0d4-a980-4613-ae76-a2cddecff054, add a route with next hop type of ECS, modify the route with next hop type of ECS, and delete the route whose destination is 20.20.10.0/24.

   .. code-block:: text

      PUT https://{Endpoint}/v1/6fbe9263116a4b68818cf1edce16bc4f/routetables/3d42a0d4-a980-4613-ae76-a2cddecff054

      {
          "routetable": {
              "name": "routertable-789",
              "description": "abc",
              "routes": {
                  "add": [
                      {
                          "type": "ecs",
                          "destination": "10.10.10.0/24",
                          "nexthop": "7c50463d-d36c-4417-aa85-cc11fa10f341",
                          "description": "abc"
                      }
                  ],
                  "mod": [
                      {
                          "type": "ecs",
                          "destination": "20.10.10.0/24",
                          "nexthop": "7c50463d-d36c-4417-aa85-cc11fa10f341",
                          "description": "abc"
                      }
                  ],
                  "del": [
                      {
                          "destination": "20.20.10.0/24"
                      }
                  ]
              }
          }
      }

Response Parameters
-------------------

.. table:: **Table 8** Response parameter

   +------------+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter  | Type                                                               | Description                                                                                           |
   +============+====================================================================+=======================================================================================================+
   | routetable | :ref:`routetable <vpc_apiroutetab_0004__table884119412392>` object | Specifies the route table. For details, see :ref:`Table 9 <vpc_apiroutetab_0004__table884119412392>`. |
   +------------+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0004__table884119412392:

.. table:: **Table 9** Description of the **routetable** field

   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                       | Description                                                                                                                            |
   +=======================+============================================================================+========================================================================================================================================+
   | id                    | String                                                                     | -  Specifies the route table ID that uniquely identifies the route table.                                                              |
   |                       |                                                                            | -  The value must be in standard UUID format.                                                                                          |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                     | -  Specifies the route table name.                                                                                                     |
   |                       |                                                                            | -  The value can contain up to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                |
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
   |                       |                                                                            | -  The value can contain up to 255 characters and cannot contain angle brackets (< or >).                                              |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                     | -  Specifies the time (UTC) when the route table is created.                                                                           |
   |                       |                                                                            | -  Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                       |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                     | -  Specifies the time (UTC) when the route table is updated.                                                                           |
   |                       |                                                                            | -  Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                       |
   +-----------------------+----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 10** Description of the **route** field

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

.. table:: **Table 11** Description of the **subnet** field

   +-----------+--------+-----------------------------------------------------------------+
   | Parameter | Type   | Description                                                     |
   +===========+========+=================================================================+
   | id        | String | Specifies the ID of the subnet associated with the route table. |
   +-----------+--------+-----------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "routetable": {
           "id": "3d42a0d4-a980-4613-ae76-a2cddecff054",
           "vpc_id": "ab78be2d-782f-42a5-aa72-35879f6890ff",
           "description": "abc",
           "default": false,
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
           "tenant_id": "6fbe9263116a4b68818cf1edce16bc4f",
           "created_at": "2022-12-15T02:56:40",
           "updated_at": "2022-12-15T03:03:42"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
