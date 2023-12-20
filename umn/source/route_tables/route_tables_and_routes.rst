:original_name: vpc_route01_0001.html

.. _vpc_route01_0001:

Route Tables and Routes
=======================

Route Tables
------------

A route table contains a set of routes that are used to determine where network traffic from your subnets in a VPC is directed. Each subnet must be associated with a route table. A subnet can only be associated with one route table, but you can associate multiple subnets with the same route table.


.. figure:: /_static/images/en-us_image_0000001650535960.png
   :alt: **Figure 1** Route tables

   **Figure 1** Route tables

-  Default route table: When you create a VPC, the system automatically generates a default route table for the VPC. If you create a subnet in the VPC, the subnet automatically associates with the default route table. The default route table ensures that subnets in a VPC can communicate with each other.

   -  You can add routes to, delete routes from, and modify routes in the default route table, but cannot delete the table.
   -  When you create a VPC endpoint, VPN or Direct Connect connection, the default route table automatically delivers a route that cannot be deleted or modified.

-  Custom route table: If you do not want to use the default route table, you can create a custom route table and associate it with the subnet. Custom route tables can be deleted if they are no longer required.

   The custom route table associated with a subnet affects only the outbound traffic. The default route table of a subnet controls the inbound traffic.

Route
-----

You can add routes to default and custom route tables and configure the destination, next hop type, and next hop in the routes to determine where network traffic is directed. Routes are classified into system routes and custom routes.

-  System routes: These routes are automatically added by the system and cannot be modified or deleted.

   After a route table is created, the system automatically adds the following system routes to the route table, so that instances in a VPC can communicate with each other.

   -  Routes whose destination is 100.64.0.0/10 or 198.19.128.0/20.

   -  Routes whose destination is a subnet CIDR block.

      If you enable IPv6 when creating a subnet, the system automatically assigns an IPv6 CIDR block to the subnet. Then, you can view IPv6 routes in its route table. Example destinations of subnet CIDR blocks are as follows:

      -  IPv4: 192.168.2.0/24
      -  IPv6: 2407:c080:802:be7::/64

      .. note::

         In addition to the preceding system routes, the system automatically adds a route whose destination is 127.0.0.0/8. This is the local loopback address.

-  Custom routes: These are routes that you can add, modify, and delete. The destination of a custom route cannot overlap with that of a system route.

   You can add a custom route and configure the destination, next hop type, and next hop in the route to determine where network traffic is directed. :ref:`Table 1 <vpc_route01_0001__en-us_topic_0038263963_route_0001_table1727714140542>` lists the supported types of next hops.

   You cannot add two routes with the same destination to a VPC route table even if their next hop types are different. The route priority depends on the destination. According to the longest match routing rule, the destination with a higher matching degree is preferentially selected for packet forwarding.

   .. _vpc_route01_0001__en-us_topic_0038263963_route_0001_table1727714140542:

   .. table:: **Table 1** Next hop type

      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Next Hop Type            | Description                                                                                                                                                  | Supported Route Table  |
      +==========================+==============================================================================================================================================================+========================+
      | Server                   | Traffic intended for the destination is forwarded to an ECS in the VPC.                                                                                      | -  Default route table |
      |                          |                                                                                                                                                              | -  Custom route table  |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Extension NIC            | Traffic intended for the destination is forwarded to the extension NIC of an ECS in the VPC.                                                                 | -  Default route table |
      |                          |                                                                                                                                                              | -  Custom route table  |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | BMS user-defined network | Traffic intended for the destination is forwarded to a BMS user-defined network. Currently, this parameter is available only in eu-de.                       | -  Default route table |
      |                          |                                                                                                                                                              | -  Custom route table  |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | VPN connection           | Traffic intended for the destination is forwarded to a VPN gateway.                                                                                          | Custom route table     |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Direct Connect gateway   | Traffic intended for the destination is forwarded to a Direct Connect gateway.                                                                               | Custom route table     |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | NAT gateway              | Traffic intended for the destination is forwarded to a NAT gateway.                                                                                          | -  Default route table |
      |                          |                                                                                                                                                              | -  Custom route table  |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | VPC peering connection   | Traffic intended for the destination is forwarded to a VPC peering connection.                                                                               | -  Default route table |
      |                          |                                                                                                                                                              | -  Custom route table  |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Virtual IP address       | Traffic intended for the destination is forwarded to a virtual IP address and then sent to active and standby ECSs to which the virtual IP address is bound. | -  Default route table |
      |                          |                                                                                                                                                              | -  Custom route table  |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+

   .. note::

      If you specify the destination when creating a resource, a system route is delivered. If you do not specify a destination when creating a resource, a custom route that can be modified or deleted is delivered.

      For example, when you create a NAT gateway, the system automatically delivers a custom route without a specific destination (0.0.0.0/0 is used by default). In this case, you can change the destination. However, when you create a VPN connection or Direct Connect gateway, you need to specify the remote subnet, that is, the destination of a route. In this case, the system delivers this system route. Do not modify the route destination on the **Route Tables** page. If you do, the destination will be inconsistent with the configured remote subnet. To modify the route destination, go to the specific resource page and modify the remote subnet, then the route destination will be changed accordingly.

Custom Route Table Configuration Process
----------------------------------------

:ref:`Figure 2 <vpc_route01_0001__en-us_topic_0212076956_fig16862186152219>` shows the process of creating and configuring a custom route table.

.. _vpc_route01_0001__en-us_topic_0212076956_fig16862186152219:

.. figure:: /_static/images/en-us_image_0214585341.png
   :alt: **Figure 2** Route table configuration process

   **Figure 2** Route table configuration process

#. For details about how to create a custom route table, see :ref:`Creating a Custom Route Table <vpc_route01_0005>`.
#. For details about how to add a custom route, see :ref:`Adding a Custom Route <vpc_route01_0006>`.
#. For details about how to associate a subnet with a route table, see :ref:`Associating a Route Table with a Subnet <vpc_route01_0007>`. After the association, the routes in the route table control the routing for the subnet.
