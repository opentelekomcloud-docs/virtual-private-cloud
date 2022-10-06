:original_name: en-us_topic_0046809840.html

.. _en-us_topic_0046809840:

VPC Peering Connection Configuration Plans
==========================================

To enable two VPCs in the same region to communicate with each other, you can create a VPC peering connection between them. The VPC and subnet CIDR blocks must meet the requirements in :ref:`Table 1 <en-us_topic_0046809840__en-us_topic_0118499087_table461583720304>`.

.. _en-us_topic_0046809840__en-us_topic_0118499087_table461583720304:

.. table:: **Table 1** Requirements for VPC and subnet CIDR blocks

   +-----------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Requirement                                                                 | Description                                                                                                                                         |
   +=============================================================================+=====================================================================================================================================================+
   | -  VPC CIDR blocks do not overlap.                                          | A VPC peering connection can enable communications between the entire VPC CIDR blocks. The destination of a route is a VPC CIDR block.              |
   | -  There are no requirements on subnet CIDR blocks.                         |                                                                                                                                                     |
   |                                                                             | For details, see :ref:`Route Configurations for Connecting Entire VPCs <en-us_topic_0046809840__en-us_topic_0118499087_section11900751101219>`.     |
   +-----------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | -  VPC CIDR blocks overlap.                                                 | A VPC peering connection can enable communications between subnets in the VPCs. The destination of a route is a subnet CIDR block.                  |
   | -  Subnet CIDR blocks connected by a VPC peering connection cannot overlap. |                                                                                                                                                     |
   |                                                                             | For details, see :ref:`Route Configurations for Connecting Specific Subnets <en-us_topic_0046809840__en-us_topic_0118499087_section1370341061310>`. |
   +-----------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0046809840__en-us_topic_0118499087_section11900751101219:

Route Configurations for Connecting Entire VPCs
-----------------------------------------------

-  Connections can be:

   -  Between two VPCs
   -  Among multiple VPCs

-  If you need to configure routes that point to entire VPCs, none of the VPCs involved in VPC peering connections can overlap. Otherwise, VPC peering connections will not take effect because the routes will be unreachable.
-  The destination of the route that points to an entire VPC is the CIDR block of the peer VPC, and the next hop is the VPC peering connection ID.

.. _en-us_topic_0046809840__en-us_topic_0118499087_section1370341061310:

Route Configurations for Connecting Specific Subnets
----------------------------------------------------

If VPCs connected by a VPC peering connection have overlapping CIDR blocks, the connection can only enable communications between non-overlapping subnets in the VPCs. If subnets in the two VPCs of a VPC peering connection overlap with each other, the connection will not take effect. When you create a VPC peering connection, ensure that the VPCs involved do not contain overlapping subnets.

For example, VPC 1 and VPC 2 have matching CIDR blocks, but the subnets in the two VPCs do not overlap. A VPC peering connection can be created between pairs of subnets that do not overlap with each other. The route table is used to control the specific subnets that the VPC peering connection is created for. :ref:`Figure 1 <en-us_topic_0046809840__en-us_topic_0118499087_fig95191521148>` shows a VPC peering connection created between two subnets. Routes are required to enable communication between Subnet A in VPC 1 and Subnet X in VPC 2.

.. _en-us_topic_0046809840__en-us_topic_0118499087_fig95191521148:

.. figure:: /_static/images/en-us_image_0194358487.png
   :alt: **Figure 1** VPC peering connection between Subnet A and Subnet X


   **Figure 1** VPC peering connection between Subnet A and Subnet X

:ref:`Figure 2 <en-us_topic_0046809840__en-us_topic_0118499087_fig13211186151514>` shows the routes configured for the VPC peering connection between Subnet A and Subnet X. After the routes are configured, Subnet A and Subnet X can communicate with each other.

.. _en-us_topic_0046809840__en-us_topic_0118499087_fig13211186151514:

.. figure:: /_static/images/en-us_image_0194358495.png
   :alt: **Figure 2** Route tables for the VPC peering connection between Subnet A and Subnet X


   **Figure 2** Route tables for the VPC peering connection between Subnet A and Subnet X

If two VPCs have overlapping subnets, a VPC peering connection created between the two subnets will not take effect, and the subnets cannot communicate with each other.

As shown in :ref:`Figure 3 <en-us_topic_0046809840__en-us_topic_0118499087_fig1253173812157>`, a VPC peering connection is created between subnet A of VPC1 and subnet X of VPC2. Subnet B of VPC1 and subnet X of VPC2 overlap with each other. If the destination of a route in the route table of VPC1 is set to the CIDR block of subnet X in VPC2, this route will conflict with the system route of subnet B in VPC1. Subnet A preferentially accesses subnet B and the VPC peering connection does not take effect.

.. _en-us_topic_0046809840__en-us_topic_0118499087_fig1253173812157:

.. figure:: /_static/images/en-us_image_0194358504.png
   :alt: **Figure 3** Invalid VPC peering connection


   **Figure 3** Invalid VPC peering connection

If peering connections are used to link VPC 1 to multiple VPCs, for example, VPC 2, VPC 3, and VPC 4, the subnets of VPC 1 cannot overlap with those of VPC 2, VPC 3, and VPC 4. If VPC 2, VPC 3, and VPC 4 have overlapping subnets, a VPC peering connection can be created between only one of these overlapping subnets and a subnet of VPC 1. If a VPC peering connection is created between a subnet and the other *N* subnets, none of the subnets can overlap.
