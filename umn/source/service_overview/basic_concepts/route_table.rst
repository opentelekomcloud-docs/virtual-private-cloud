:original_name: en-us_topic_0038263963.html

.. _en-us_topic_0038263963:

Route Table
===========

Background
----------

VPC has old and new console editions. You can click |image1| in the lower right corner of the console to switch between the old and new consoles.

-  On the new console, the route table module is accessible from the navigation pane on the left, as shown in :ref:`Figure 1 <en-us_topic_0038263963__en-us_topic_0118498988_fig166812264154>`. For details, see :ref:`Route Table (New Console Edition) <en-us_topic_0038263963__en-us_topic_0118498988_section22531339489>`, :ref:`Default Route Table and Custom Route Table <en-us_topic_0038263963__en-us_topic_0118498988_section29931443171216>`, and :ref:`Route <en-us_topic_0038263963__en-us_topic_0118498988_section16240184933120>`.

   .. _en-us_topic_0038263963__en-us_topic_0118498988_fig166812264154:

   .. figure:: /_static/images/en-us_image_0000001206933138.png
      :alt: **Figure 1** New console


      **Figure 1** New console

-  On the old console, the route table module is accessible from the VPC details page, as shown in :ref:`Figure 2 <en-us_topic_0038263963__en-us_topic_0118498988_fig1118575931512>`. For details, see :ref:`Route Table (Old Console Edition) <en-us_topic_0038263963__en-us_topic_0118498988_section1155203705018>`.

   .. _en-us_topic_0038263963__en-us_topic_0118498988_fig1118575931512:

   .. figure:: /_static/images/en-us_image_0000001251773147.png
      :alt: **Figure 2** Old console


      **Figure 2** Old console

.. _en-us_topic_0038263963__en-us_topic_0118498988_section22531339489:

Route Table (New Console Edition)
---------------------------------

A route table contains a set of routes that are used to determine where network traffic from your subnets in a VPC is directed. Each subnet must be associated with a route table. You can associate a subnet with only one route table at a time, but you can associate multiple subnets with the same route table.


.. figure:: /_static/images/en-us_image_0000001229959315.png
   :alt: **Figure 3** Route Table


   **Figure 3** Route Table

.. _en-us_topic_0038263963__en-us_topic_0118498988_section29931443171216:

Default Route Table and Custom Route Table
------------------------------------------

When you create a VPC, the system automatically generates a default route table for the VPC. If you create a subnet in the VPC, the subnet automatically associates with the default route table. You can add, delete, and modify routes in the default route table, but you cannot delete the route table. When you create a VPN, Direct Connect connection, the default route table automatically delivers a route that cannot be deleted or modified. If you want to modify or delete the route, you can associate your subnet with a custom route table and replicate the route to the custom route table to modify or delete it.

If you do not want to use the default route table, you can now create a custom route table and associate it with the subnet. Custom route tables can be deleted if they are no longer required.

.. _en-us_topic_0038263963__en-us_topic_0118498988_section16240184933120:

Route
-----

A route is configured with the destination, next hop type, and next hop to determine where network traffic is directed. Routes are classified into system routes and custom routes.

-  System routes: These routes are automatically added by the system and cannot be modified or deleted.

   After a route table is created, the system automatically adds the following system routes to the route table, so that instances in a VPC can communicate with each other.

   -  Routes whose destination is 100.64.0.0/10 or 198.19.128.0/20.
   -  Routes whose destination are the IPv4 and IPv6 CIDR blocks of subnets in the VPC.

      .. note::

         In addition to the preceding system routes, the system automatically adds a route whose destination is 127.0.0.0/8. This is the local loopback address.

-  Custom routes: These are routes that you can add, modify, and delete. The destination of a custom route cannot overlap with that of a system route.

   You can add a custom route and configure the destination, next hop type, and next hop in the route to determine where network traffic is directed. :ref:`Table 1 <en-us_topic_0038263963__en-us_topic_0118498988_en-us_topic_0121831807_table1727714140542>` lists the supported types of next hops.

   .. _en-us_topic_0038263963__en-us_topic_0118498988_en-us_topic_0121831807_table1727714140542:

   .. table:: **Table 1** Next hop type

      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Next Hop Type          | Description                                                                                                                                                  | Supported Route Table  |
      +========================+==============================================================================================================================================================+========================+
      | Server                 | Traffic intended for the destination is forwarded to an ECS in the VPC.                                                                                      | -  Default route table |
      |                        |                                                                                                                                                              | -  Custom route table  |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Extension NIC          | Traffic intended for the destination is forwarded to the extension NIC of an ECS in the VPC.                                                                 | -  Default route table |
      |                        |                                                                                                                                                              | -  Custom route table  |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | VPN connection         | Traffic intended for the destination is forwarded to a VPN gateway.                                                                                          | Custom route table     |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Direct Connect gateway | Traffic intended for the destination is forwarded to a Direct Connect gateway.                                                                               | Custom route table     |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | NAT gateway            | Traffic intended for the destination is forwarded to a NAT gateway.                                                                                          | -  Default route table |
      |                        |                                                                                                                                                              | -  Custom route table  |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | VPC peering connection | Traffic intended for the destination is forwarded to a VPC peering connection.                                                                               | -  Default route table |
      |                        |                                                                                                                                                              | -  Custom route table  |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Virtual IP address     | Traffic intended for the destination is forwarded to a virtual IP address and then sent to active and standby ECSs to which the virtual IP address is bound. | -  Default route table |
      |                        |                                                                                                                                                              | -  Custom route table  |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+

   .. note::

      If you specify the destination when creating a resource, a system route is delivered. If you do not specify a destination when creating a resource, a custom route that can be modified or deleted is delivered.

      For example, when you create a NAT gateway, the system automatically delivers a custom route without a specific destination (0.0.0.0/0 is used by default). In this case, you can change the destination. However, when you create a VPN connection or Direct Connect gateway, you need to specify the remote subnet, that is, the destination of a route. In this case, the system delivers this system route. Do not modify the route destination on the **Route Tables** page. If you do, the destination will be inconsistent with the configured remote subnet. To modify the route destination, go to the specific resource page and modify the remote subnet, then the route destination will be changed accordingly.

.. _en-us_topic_0038263963__en-us_topic_0118498988_section1155203705018:

Route Table (Old Console Edition)
---------------------------------

A route table contains a set of rules that determine where network traffic is directed. You can add routes to a route table to enable other ECSs in a VPC to access the Internet through the ECS that has a bound EIP.

You can use a route table configured in standalone mode or active/standby mode.

-  :ref:`Figure 4 <en-us_topic_0038263963__en-us_topic_0118498988_fig15091812119>` shows the route table configured in standalone mode.

   .. _en-us_topic_0038263963__en-us_topic_0118498988_fig15091812119:

   .. figure:: /_static/images/en-us_image_0209273220.png
      :alt: **Figure 4** Route table configured in standalone mode


      **Figure 4** Route table configured in standalone mode

   In standalone mode, ECSs in a VPC that do not have EIPs bound access the Internet through an ECS that has an EIP bound and has the SNAT function configured.

   You can create a route table for the VPC used by ECSs that do not have EIPs bound to enable these ECSs to access the Internet. The next hop in the route table is the private IP address of the ECS that has an EIP bound (that is the private IP address of the SNAT server).

-  :ref:`Figure 5 <en-us_topic_0038263963__en-us_topic_0118498988_fig1588016299143>` shows the route table configured in active/standby mode.

   .. _en-us_topic_0038263963__en-us_topic_0118498988_fig1588016299143:

   .. figure:: /_static/images/en-us_image_0118498947.png
      :alt: **Figure 5** Route table configured in active/standby mode


      **Figure 5** Route table configured in active/standby mode

   In active/standby mode, ECSs in a VPC that do not have EIPs bound access the Internet through two ECSs that have EIPs bound and have the SNAT function configured.

   In active/standby mode, you can add a route table for the VPC used by ECSs that do not have EIPs bound, to enable these ECSs to access the Internet. The next hop in the route table is the virtual IP address of the two ECSs that have EIPs bound.

In both the standalone and active/standby modes, the ECSs that have EIPs bound must have the SNAT function. For details about the SNAT function, see :ref:`SNAT <vpc_concepts_0004>`. For details about how to configure an ECS as the SNAT server, see :ref:`Configuring an SNAT Server <vpc_route_0004>`.

.. important::

   -  Before using the route table function, you need to deploy the SNAT server. For details, see section :ref:`Configuring an SNAT Server <vpc_route_0004>`.
   -  The ECS providing SNAT function can have only one NIC.
   -  The ECS providing SNAT function must have the source/destination check function disabled.

.. |image1| image:: /_static/images/en-us_image_0000001207093220.png
