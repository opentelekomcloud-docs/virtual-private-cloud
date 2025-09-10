:original_name: vpc_quota_0001.html

.. _vpc_quota_0001:

Querying Quotas
===============

Function
--------

This API is used to query network resource quotas of a tenant. The network resources include VPCs, subnets, security groups, security group rules, VPNs, and EIPs.

URI
---

GET /v1/{project_id}/quotas

Example:

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/quotas?type={type}

:ref:`Table 1 <vpc_quota_0001__table38014313>` describes the parameters.

.. _vpc_quota_0001__table38014313:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                  |
   +=================+=================+=================+==============================================================================+
   | project_id      | Yes             | String          | Specifies the project ID.                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+
   | type            | No              | String          | -  Specifies the resource type.                                              |
   |                 |                 |                 | -  Values:                                                                   |
   |                 |                 |                 |                                                                              |
   |                 |                 |                 |    -  **vpc**: VPC                                                           |
   |                 |                 |                 |    -  **subnet**: Subnet                                                     |
   |                 |                 |                 |    -  **securityGroup**: Security group                                      |
   |                 |                 |                 |    -  **securityGroupRule**: Security group rule                             |
   |                 |                 |                 |    -  **publicIp**: EIP                                                      |
   |                 |                 |                 |    -  **vpn**: VPN                                                           |
   |                 |                 |                 |    -  **vpcPeer**: VPC peering connection                                    |
   |                 |                 |                 |    -  **loadbalancer**: Load balancer                                        |
   |                 |                 |                 |    -  **listener**: Load balancer listener                                   |
   |                 |                 |                 |    -  **physicalConnect**: Direct Connect connection                         |
   |                 |                 |                 |    -  **virtualInterface**: Virtual interface                                |
   |                 |                 |                 |    -  **firewall**: Firewall                                                 |
   |                 |                 |                 |    -  **shareBandwidthIP**: IP address added to a shared bandwidth           |
   |                 |                 |                 |    -  **shareBandwidth**: Shared bandwidth                                   |
   |                 |                 |                 |    -  **address_group**: IP address group                                    |
   |                 |                 |                 |    -  **flow_log**: VPC flow log                                             |
   |                 |                 |                 |    -  **vpcContainRoutetable**: Number of route tables associated with a VPC |
   |                 |                 |                 |    -  **routetableContainRoutes**: Number of routes in a route table         |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/quotas

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------+------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                       | Description                                                                                        |
   +===========+============================================================+====================================================================================================+
   | quotas    | :ref:`quotas <vpc_quota_0001__table11308015155544>` object | Specifies the quota object. For details, see :ref:`Table 3 <vpc_quota_0001__table11308015155544>`. |
   +-----------+------------------------------------------------------------+----------------------------------------------------------------------------------------------------+

.. _vpc_quota_0001__table11308015155544:

.. table:: **Table 3** Description of the **quotas** field

   +-----------+-----------------------------------------------------------------+-------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                            | Description                                                                                     |
   +===========+=================================================================+=================================================================================================+
   | resources | Array of :ref:`resource <vpc_quota_0001__table8208684>` objects | Specifies the resource objects. For details, see :ref:`Table 4 <vpc_quota_0001__table8208684>`. |
   +-----------+-----------------------------------------------------------------+-------------------------------------------------------------------------------------------------+

.. _vpc_quota_0001__table8208684:

.. table:: **Table 4** Description of the **resource** field

   +-----------------------+-----------------------+------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                  |
   +=======================+=======================+==============================================================================+
   | type                  | String                | -  Specifies the resource type.                                              |
   |                       |                       | -  Values:                                                                   |
   |                       |                       |                                                                              |
   |                       |                       |    -  **vpc**: VPC                                                           |
   |                       |                       |    -  **subnet**: Subnet                                                     |
   |                       |                       |    -  **securityGroup**: Security group                                      |
   |                       |                       |    -  **securityGroupRule**: Security group rule                             |
   |                       |                       |    -  **publicIp**: EIP                                                      |
   |                       |                       |    -  **vpn**: VPN                                                           |
   |                       |                       |    -  **vpcPeer**: VPC peering connection                                    |
   |                       |                       |    -  **loadbalancer**: Load balancer                                        |
   |                       |                       |    -  **listener**: Load balancer listener                                   |
   |                       |                       |    -  **physicalConnect**: Direct Connect connection                         |
   |                       |                       |    -  **virtualInterface**: Virtual interface                                |
   |                       |                       |    -  **firewall**: Firewall                                                 |
   |                       |                       |    -  **shareBandwidthIP**: IP address added to a shared bandwidth           |
   |                       |                       |    -  **shareBandwidth**: Shared bandwidth                                   |
   |                       |                       |    -  **address_group**: IP address group                                    |
   |                       |                       |    -  **flow_log**: VPC flow log                                             |
   |                       |                       |    -  **vpcContainRoutetable**: Number of route tables associated with a VPC |
   |                       |                       |    -  **routetableContainRoutes**: Number of routes in a route table         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------+
   | used                  | Integer               | -  Specifies the number of created network resources.                        |
   |                       |                       | -  The value ranges from **0** to the value of **quota**.                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------+
   | quota                 | Integer               | -  Specifies the maximum quota values for the resources.                     |
   |                       |                       | -  The value ranges from the default quota value to the maximum quota value. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------+
   | min                   | Integer               | Specifies the minimum quota value allowed.                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------+

.. note::

   If value **-1** is returned when you use an API to query your VPC quota, this indicates that the VPC quota is not limited.

Example Response
----------------

.. code-block::

   {
       "quotas": {
           "resources": [
               {
                   "type": "vpc",
                   "used": 4,
                   "quota": 150,
                   "min": 0
               },
               {
                   "type": "subnet",
                   "used": 5,
                   "quota": 400,
                   "min": 0
               },
               {
                   "type": "securityGroup",
                   "used": 1,
                   "quota": 100,
                   "min": 0
               },
               {
                   "type": "securityGroupRule",
                   "used": 6,
                   "quota": 5000,
                   "min": 0
               },
               {
                   "type": "publicIp",
                   "used": 2,
                   "quota": 10,
                   "min": 0
               },
               {
                   "type": "vpn",
                   "used": 0,
                   "quota": 5,
                   "min": 0
               },
               {
                   "type": "vpcPeer",
                   "used": 0,
                   "quota": 50,
                   "min": 0
               },
               {
                   "type":"physicalConnect",
                   "used":0,
                   "quota":10,
                   "min":0
               },
               {
                   "type":"virtualInterface",
                   "used":0,
                   "quota":50,
                   "min":0
               },
               {
                   "type": "firewall",
                   "used": 0,
                   "quota": 200,
                   "min": 0
               },
               {
                   "type": "shareBandwidth",
                   "used": 0,
                   "quota": 5,
                   "min": 0
               },
               {
                   "type": "shareBandwidthIP",
                   "used": 0,
                   "quota": 20,
                   "min": 0
               },
               {
                   "type": "loadbalancer",
                   "used": 0,
                   "quota": 10,
                   "min": 0
               },
               {
                   "type": "listener",
                   "used": 0,
                   "quota": 10,
                   "min": 0
               },
               {
                   "type": "flow_log",
                   "used": 0,
                   "quota": 10,
                   "min": 0
               },
               {
                   "type": "vpcContainRoutetable",
                   "used": 0,
                   "quota": 1,
                   "min": 0
               },
               {
                   "type": "routetableContainRoutes",
                   "used": 0,
                   "quota": 200,
                   "min": 0
               }
           ]
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
