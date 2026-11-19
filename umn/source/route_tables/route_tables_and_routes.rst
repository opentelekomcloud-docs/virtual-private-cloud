:original_name: vpc_route01_0001.html

.. _vpc_route01_0001:

Route Tables and Routes
=======================

Route Tables
------------

A route table contains a set of routes that are used to determine where network traffic from your subnets in a VPC is directed. Each subnet must be associated with a route table. A subnet can only be associated with one route table, but you can associate multiple subnets with the same route table.


.. figure:: /_static/images/en-us_image_0000001865662949.png
   :alt: **Figure 1** Route tables

   **Figure 1** Route tables

-  Default route table: When you create a VPC, the system automatically generates a default route table for the VPC. If you create a subnet in the VPC, the subnet automatically associates with the default route table. The default route table ensures that subnets in a VPC can communicate with each other.

   -  You can add routes to, delete routes from, and modify routes in the default route table, but cannot delete the table.
   -  When you create a VPC endpoint, VPN or Direct Connect connection, the default route table automatically delivers a route that cannot be deleted or modified.

-  Custom route table: If you do not want to use the default route table, you can create a custom route table and associate it with the subnet. Custom route tables can be deleted if they are no longer required.

   The custom route table associated with a subnet affects only the outbound traffic. The default route table of a subnet controls the inbound traffic.

Route
-----

You can add routes to default and custom route tables and configure the destination type, destination, next hop type, and next hop in the routes to determine where network traffic is directed. Routes are classified into system routes and custom routes.

-  System routes: These routes are automatically added by the system and cannot be modified or deleted.

   Each route table comes with **Local** routes. :ref:`Table 1 <vpc_route01_0001__en-us_topic_0118498988_table9986131015235>` shows details about **Local** routes.

   .. _vpc_route01_0001__en-us_topic_0118498988_table9986131015235:

   .. table:: **Table 1** Local routes

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Local Route Destination           | Destination Description                                                                                                                                                                                                                                                   |
      +===================================+===========================================================================================================================================================================================================================================================================+
      | 100.64.0.0/10                     | Used by public services on the cloud. This local route allows instances in a subnet to access public services on the cloud, such as the DNS servers.                                                                                                                      |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | 198.19.128.0/20                   | Used by internal services, such as VPC Endpoint.                                                                                                                                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | 127.0.0.0/8                       | Provides local loopback addresses.                                                                                                                                                                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Subnet CIDR block                 | Subnet CIDR block in a VPC. This local route allows different subnets in the VPC to communicate with each other.                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                           |
      |                                   | When you create a subnet, you can specify an IPv4 CIDR block for the subnet. If you select **IPv6 CIDR Block** when creating a subnet, the system automatically assigns an IPv6 CIDR block to the subnet. Then, you can view IPv6 routes in its route table. For example: |
      |                                   |                                                                                                                                                                                                                                                                           |
      |                                   | -  IPv4 CIDR block of a subnet: 192.168.2.0/24                                                                                                                                                                                                                            |
      |                                   | -  IPv6 CIDR block of a subnet: 2407:c080:802:be7::/64                                                                                                                                                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Custom route: After a route table is created, you can add custom routes and configure information such as the destination and next hop in the route to determine where network traffic is directed. In addition to manually added custom routes, there are custom routes added by other cloud services, such as Cloud Container Engine (CCE) or NAT Gateway.

   You cannot add two routes with the same destination to a VPC route table even if their next hop types are different, because the destination determines the route priority. According to the longest match routing rule, the destination with a higher matching degree is preferentially selected for packet forwarding.

   There are default and custom route tables. They support the next hop types described in :ref:`Table 2 <vpc_route01_0001__en-us_topic_0118498988_table12546151672511>` and :ref:`Table 3 <vpc_route01_0001__table161700340487>`. The default route table supports fewer next hop types than a custom route table. This is because some services automatically add routes to the default table.

   .. _vpc_route01_0001__en-us_topic_0118498988_table12546151672511:

   .. table:: **Table 2** Next hop types supported by the default route table

      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Next Hop Type          | Description                                                                                                                                                 |
      +========================+=============================================================================================================================================================+
      | Server                 | Traffic intended for the destination is forwarded to an ECS in the VPC.                                                                                     |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Extension NIC          | Traffic intended for the destination is forwarded to the extended network interface of an ECS in the VPC.                                                   |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | NAT gateway            | Traffic intended for the destination is forwarded to a NAT gateway.                                                                                         |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | VPC peering connection | Traffic intended for the destination is forwarded to a VPC peering connection.                                                                              |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Virtual IP address     | Traffic intended for the destination is forwarded to a virtual IP address and then sent to active and standby ECSs that the virtual IP address is bound to. |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise router      | Traffic intended for the destination is forwarded to an enterprise router.                                                                                  |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cloud firewall         | Traffic intended for the destination is forwarded to a cloud firewall.                                                                                      |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _vpc_route01_0001__table161700340487:

   .. table:: **Table 3** Next hop types supported by a custom route table

      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Next Hop Type          | Description                                                                                                                                                 |
      +========================+=============================================================================================================================================================+
      | Server                 | Traffic intended for the destination is forwarded to an ECS in the VPC.                                                                                     |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Extension NIC          | Traffic intended for the destination is forwarded to the extended network interface of an ECS in the VPC.                                                   |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | VPN connection         | Traffic intended for the destination is forwarded to a VPN gateway.                                                                                         |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Direct Connect gateway | Traffic intended for the destination is forwarded to a Direct Connect gateway.                                                                              |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | NAT gateway            | Traffic intended for the destination is forwarded to a NAT gateway.                                                                                         |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | VPC peering connection | Traffic intended for the destination is forwarded to a VPC peering connection.                                                                              |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Virtual IP address     | Traffic intended for the destination is forwarded to a virtual IP address and then sent to active and standby ECSs that the virtual IP address is bound to. |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise router      | Traffic intended for the destination is forwarded to an enterprise router.                                                                                  |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cloud firewall         | Traffic intended for the destination is forwarded to a cloud firewall.                                                                                      |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   If you specify the destination when creating a resource, a system route is delivered. If you do not specify a destination when creating a resource, a custom route that can be modified or deleted is delivered.

   For example, when you create a NAT gateway, the system automatically delivers a custom route without a specific destination (0.0.0.0/0 is used by default). In this case, you can change the destination. However, when you create a VPN connection or Direct Connect gateway, you need to specify the remote subnet, that is, the destination of a route. In this case, the system delivers a system route. Do not modify the route destination on the **Route Tables** page. If you do, the destination will be inconsistent with the configured remote subnet. To modify the route destination, go to the specific resource page and modify the remote subnet, then the route destination will be changed accordingly.

How Route Tables Work
---------------------

Each subnet in a VPC must have a route table associated. A subnet can be associated with the default route table or a custom route table. For details about the association between a subnet and a route table, see :ref:`Changing the Route Table Associated with a Subnet <vpc_route01_0008>`.

:ref:`Figure 2 <vpc_route01_0001__fig24301738173916>` shows two subnets in VPC-A. They are associated with different route tables to meet different network access requirements.

-  Subnet 1 is associated with the default route table that contains a route pointing to the VPN gateway. This route allows ECSs in subnet 1 to access the on-premises data center through VPN.
-  Subnet 2 is associated with a custom route table that contains a route pointing to the NAT gateway. This route allows ECSs in subnet 2 to access the Internet through the NAT gateway and EIP.

.. _vpc_route01_0001__fig24301738173916:

.. figure:: /_static/images/en-us_image_0000002524845288.png
   :alt: **Figure 2** **Default and custom route tables of subnets**

   **Figure 2** **Default and custom route tables of subnets**

Route Priority
--------------

In a VPC route table, routes are matched by priority in the following order: Local route > specific route > EIP route > default route. For details about each type of route, see :ref:`Table 4 <vpc_route01_0001__table1427601412451>`.

.. _vpc_route01_0001__table1427601412451:

.. table:: **Table 4** VPC route priorities

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | No.                   | Route Type            | Description                                                                                                                                                                                                                             |
   +=======================+=======================+=========================================================================================================================================================================================================================================+
   | 1                     | Local route           | **Local routes are system routes used for communications within a VPC and have the highest priority.** :ref:`Table 5 <vpc_route01_0001__table656811322585>` provides examples of local routes.                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 2                     | Specific route        | **Excepting local routes, if there are multiple routes that match the request destination, the longest prefix match is used.** This means that the route with the longest subnet mask is preferentially used to determine the next hop. |
   |                       |                       |                                                                                                                                                                                                                                         |
   |                       |                       | For example, if the destination of traffic entering a VPC is 192.168.1.12/32, the VPC route table has the following routes:                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                         |
   |                       |                       | -  Route A with 192.168.0.0/16 as the destination and ECS-A as the next hop                                                                                                                                                             |
   |                       |                       | -  Route B with 192.168.1.0/24 as the destination and VPC peering connection as the next hop                                                                                                                                            |
   |                       |                       | -  Route C with 0.0.0.0/0 as the destination and NAT gateway as the next hop                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                         |
   |                       |                       | According to the longest prefix match, the request preferentially matches route B and will be forwarded to the VPC peering connection.                                                                                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 3                     | EIP route             | **If an ECS in a subnet has an EIP bound,** **the EIP route takes precedence over the default route** (destination: 0.0.0.0/0) in the route table. In this case, the EIP is used for Internet access.                                   |
   |                       |                       |                                                                                                                                                                                                                                         |
   |                       |                       | For example:                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                         |
   |                       |                       | -  There is route A with 0.0.0.0/0 as the destination and NAT gateway as the next hop.                                                                                                                                                  |
   |                       |                       | -  ECS-A in a VPC subnet has an EIP bound.                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                         |
   |                       |                       | In this case, ECS-A will use the EIP to access the Internet instead of the NAT gateway.                                                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 4                     | Default route         | **The route with the destination 0.0.0.0/0 is the default route, which can match any traffic. According to the longest prefix match, 0.0.0.0/0 has the lowest priority.**                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Constraints
-----------

In each VPC route table, there are local routes and custom routes.

-  Generally, the destination of a custom route cannot overlap with that of a local route. The destination of a local route can be a subnet CIDR block or CIDR blocks that are used for internal communications.

   For example, if VPC-A has a subnet that supports IPv4/IPv6 dual stack. Its IPv4 CIDR block is 192.168.2.0/24 and IPv6 CIDR block is 2407:c080:802:be7::/64. The system automatically adds the local routes in :ref:`Table 5 <vpc_route01_0001__table656811322585>` to the route table of VPC-A. In this case, the destinations of the custom routes you set cannot overlap with those of the existing local routes.

   .. _vpc_route01_0001__table656811322585:

   .. table:: **Table 5** VPC-A local routes

      +-------------------------+-----------------------------------------------------------+
      | Local Route Destination | Destination Description                                   |
      +=========================+===========================================================+
      | 192.168.2.0/24          | IPv4 CIDR block of the subnet                             |
      +-------------------------+-----------------------------------------------------------+
      | 2407:c080:802:be7::/64  | IPv6 CIDR block of the subnet                             |
      +-------------------------+-----------------------------------------------------------+
      | 100.64.0.0/10           | Network used by public services on the cloud, such as DNS |
      +-------------------------+-----------------------------------------------------------+
      | 198.19.128.0/20         | Network used by internal services, such as VPC Endpoint   |
      +-------------------------+-----------------------------------------------------------+
      | 127.0.0.0/8             | Loopback address                                          |
      +-------------------------+-----------------------------------------------------------+

-  You cannot add two routes with the same destination to a VPC route table even if their next hop types are different.

Custom Route Table Configuration Process
----------------------------------------


.. figure:: /_static/images/en-us_image_0000002553156842.png
   :alt: **Figure 3** Process for configuring a custom route table

   **Figure 3** Process for configuring a custom route table

.. table:: **Table 6** Description of the process for configuring a custom route table

   +-----+------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | No. | Step                                     | Description                                                                                                                                            | Reference                                                         |
   +=====+==========================================+========================================================================================================================================================+===================================================================+
   | 1   | Create a custom route table.             | If the default route table cannot meet your service requirements, you can create a custom route table.                                                 | :ref:`Creating a Custom Route Table <vpc_route01_0005>`           |
   +-----+------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | 2   | Add a custom route.                      | You can add a custom route and configure information such as the destination and next hop in the route to determine where network traffic is directed. | :ref:`Adding a Custom Route <vpc_route01_0006>`                   |
   +-----+------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | 3   | Associate the route table with a subnet. | After a route table is associated with a subnet, the routes in the route table control the routing for all cloud resources in the subnet.              | :ref:`Associating a Route Table with a Subnet <vpc_route01_0007>` |
   +-----+------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
