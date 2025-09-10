:original_name: vpc_apiroutetab_0002.html

.. _vpc_apiroutetab_0002:

Querying a Route Table
======================

Function
--------

This API is used to query details about a route table.

URI
---

GET /v1/{project_id}/routetables/{routetable_id}

:ref:`Table 1 <vpc_apiroutetab_0002__table12826134133917>` describes the parameters.

.. _vpc_apiroutetab_0002__table12826134133917:

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

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v1/26ae5181a416420998eb2093aaed84d9/routetables/66df8c1f-d4f6-4a63-9abb-09701fe27b39

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +------------+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter  | Type                                                               | Description                                                                                           |
   +============+====================================================================+=======================================================================================================+
   | routetable | :ref:`routetable <vpc_apiroutetab_0002__table884119412392>` object | Specifies the route table. For details, see :ref:`Table 3 <vpc_apiroutetab_0002__table884119412392>`. |
   +------------+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0002__table884119412392:

.. table:: **Table 3** Description of the **routetable** field

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

.. _vpc_apiroutetab_0002__table1687317463915:

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

.. _vpc_apiroutetab_0002__table17950204203919:

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
    "routetable": {
     "id": "05250d7e-0396-4fc9-9c9c-e4d5594784e4",
     "name": "rtb-vpc-l2cg-1",
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
       "id": "0e0faa8f-ea73-47aa-b919-8c133e98d5ac"
      },
      {
       "id": "e007e005-10aa-4614-b439-c9a14e55130e"
      }
     ],
     "vpc_id": "7978e43c-f892-49d8-9fab-9bb90a51709b",
     "default": true,
     "tenant_id": "05e369f07a800f802f41c002632ba5f9",
     "created_at": "2022-12-15T02:56:40",
     "updated_at": "2022-12-15T02:56:40"
    }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
