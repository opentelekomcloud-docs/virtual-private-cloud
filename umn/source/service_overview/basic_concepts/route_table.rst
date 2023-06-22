:original_name: en-us_topic_0038263963.html

.. _en-us_topic_0038263963:

Route Table
===========

Route Tables
------------

A route table contains a set of routes that are used to determine where network traffic from your subnets in a VPC is directed. Each subnet must be associated with a route table. You can associate a subnet with only one route table at a time, but you can associate multiple subnets with the same route table.


.. figure:: /_static/images/en-us_image_0000001229959315.png
   :alt: **Figure 1** Route Table

   **Figure 1** Route Table

Default Route Table and Custom Route Table
------------------------------------------

When you create a VPC, the system automatically generates a default route table for the VPC. If you create a subnet in the VPC, the subnet automatically associates with the default route table.

-  You can add routes to, delete routes from, and modify routes in the default route table, but cannot delete the table.
-  When you create a VPC endpoint, VPN or Direct Connect connection, the default route table automatically delivers a route that cannot be deleted or modified.

If you do not want to use the default route table, you can now create a custom route table and associate it with the subnet. You can delete the custom route table if it is no longer required.

.. note::

   The custom route table associated with a subnet affects only the outbound traffic. The default route table determines the inbound traffic.

Route
-----

A route is configured with the destination, next hop type, and next hop to determine where network traffic is directed. Routes are classified into system routes and custom routes.

-  System routes: These routes are automatically added by the system and cannot be modified or deleted.

   After a route table is created, the system automatically adds the following system routes to the route table, so that instances in a VPC can communicate with each other.

   -  Routes whose destination is 100.64.0.0/10 or 198.19.128.0/20.
   -  Routes whose destination is a subnet CIDR block.

      .. note::

         In addition to the preceding system routes, the system automatically adds a route whose destination is 127.0.0.0/8. This is the local loopback address.

-  Custom routes: These are routes that you can add, modify, and delete. The destination of a custom route cannot overlap with that of a system route.

   You can add a custom route and configure the destination, next hop type, and next hop in the route to determine where network traffic is directed. :ref:`Table 1 <en-us_topic_0038263963__route_0001_table1727714140542>` lists the supported types of next hops.

   You cannot add two routes with the same destination to a VPC route table even if their next hop types are different. The route priority depends on the destination. According to the longest match routing rule, the destination with a higher matching degree is preferentially selected for packet forwarding.

   .. _en-us_topic_0038263963__route_0001_table1727714140542:

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
