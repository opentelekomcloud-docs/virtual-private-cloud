:original_name: vpc_peering_0012.html

.. _vpc_peering_0012:

Unsupported VPC Peering Configurations
======================================

Scenarios
---------

The VPC peering connection configurations are not supported in :ref:`Table 1 <vpc_peering_0012__en-us_topic_0000001252180225_table187875614582>`.

.. _vpc_peering_0012__en-us_topic_0000001252180225_table187875614582:

.. table:: **Table 1** Scenarios that VPC peering connections are invalid

   +-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scenario                                                                                                                                                                          | Example                                                                                                                                                |
   +===================================================================================================================================================================================+========================================================================================================================================================+
   | -  If VPCs with the same CIDR block also include subnets that overlap, VPC peering connections are not usable.                                                                    | :ref:`Invalid VPC Peering for Overlapping VPC CIDR Blocks <vpc_peering_0012__en-us_topic_0000001252180225_section8761814191518>`                       |
   | -  If two VPCs have overlapping CIDR blocks but some of their subnets do not overlap, you cannot create a VPC peering connection to connect specific subnets that do not overlap. |                                                                                                                                                        |
   |                                                                                                                                                                                   | -  :ref:`VPCs with overlapping CIDR blocks also have all their subnets that overlap. <vpc_peering_0012__en-us_topic_0000001252180225_li1850597123311>` |
   |                                                                                                                                                                                   | -  :ref:`Two VPCs have overlapping CIDR blocks and some of their subnets overlap. <vpc_peering_0012__en-us_topic_0000001252180225_li2200181714258>`    |
   +-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | VPC peering connections cannot enable ECSs in their VPCs to share an EIP to access the Internet.                                                                                  | :ref:`Invalid VPC Peering for Sharing an EIP <vpc_peering_0012__en-us_topic_0000001252180225_section633272018142>`                                     |
   |                                                                                                                                                                                   |                                                                                                                                                        |
   | If VPC-A and VPC-B are peered and ECS-A01 in VPC-A has an EIP, ECS-B01 in VPC-B cannot access the Internet using the EIP bound to ECS-A01.                                        |                                                                                                                                                        |
   +-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_peering_0012__en-us_topic_0000001252180225_section8761814191518:

Invalid VPC Peering for Overlapping VPC CIDR Blocks
---------------------------------------------------

If two VPCs have overlapping CIDR blocks, the VPC peering connection may not take effect due to route conflicts. The following describes the reasons and configuration suggestions.

-  .. _vpc_peering_0012__en-us_topic_0000001252180225_li1850597123311:

   VPCs with overlapping CIDR blocks also have all their subnets that overlap.

   VPC peering connections are not usable. As shown in :ref:`Figure 1 <vpc_peering_0012__en-us_topic_0000001252180225_fig465519155457>`, VPC-A and VPC-B, and their subnets have the same CIDR block. If you create a VPC peering connection between VPC-A and VPC-B, their route tables are shown in :ref:`Table 2 <vpc_peering_0012__en-us_topic_0000001252180225_table117301117101418>`.

   In the rtb-VPC-A route table, the custom route for routing traffic from VPC-A to VPC-B and the local route have overlapping destinations. The local route has a higher priority and traffic will be forwarded within VPC-A and cannot reach VPC-B.

   .. _vpc_peering_0012__en-us_topic_0000001252180225_fig465519155457:

   .. figure:: /_static/images/en-us_image_0000002555955821.png
      :alt: **Figure 1** Networking diagram (IPv4)

      **Figure 1** Networking diagram (IPv4)

   .. _vpc_peering_0012__en-us_topic_0000001252180225_table117301117101418:

   .. table:: **Table 2** VPC route table details

      +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+
      | Route Table | Destination         | Next Hop   | Route Type | Description                                                                                 |
      +=============+=====================+============+============+=============================================================================================+
      | rtb-VPC-A   | 10.0.0.0/24         | Local      | System     | Local routes are automatically added by the system for communications within a VPC.         |
      +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+
      |             | 10.0.1.0/24         | Local      | System     |                                                                                             |
      +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+
      |             | 10.0.0.0/16 (VPC-B) | Peering-AB | Custom     | Add a route with the CIDR block of VPC-B as the destination and Peering-AB as the next hop. |
      +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+
      | rtb-VPC-B   | 10.0.0.0/24         | Local      | System     | Local routes are automatically added by the system for communications within a VPC.         |
      +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+
      |             | 10.0.1.0/24         | Local      | System     |                                                                                             |
      +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+
      |             | 10.0.0.0/16 (VPC-A) | Peering-AB | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AB as the next hop. |
      +-------------+---------------------+------------+------------+---------------------------------------------------------------------------------------------+

   If two VPCs want to use their IPv6 CIDR blocks for communication by a VPC peering connection but the IPv4 CIDR blocks of the VPCs or subnets overlap, the connection is not usable.


   .. figure:: /_static/images/en-us_image_0000002524875914.png
      :alt: **Figure 2** Networking diagram (IPv6)

      **Figure 2** Networking diagram (IPv6)

-  .. _vpc_peering_0012__en-us_topic_0000001252180225_li2200181714258:

   Two VPCs have overlapping CIDR blocks and some of their subnets overlap.

   VPC peering connections will not take effect in the following scenarios:

   -  Connecting overlapping CIDR blocks of VPCs

      As shown in :ref:`Figure 3 <vpc_peering_0012__en-us_topic_0000001252180225_fig10553152375617>`, if you create a VPC peering connection between VPC-A and VPC-B, the VPC peering connection will not take effect because the two VPCs have the same CIDR block.

   -  Connecting overlapping subnets from different VPCs

      As shown in :ref:`Figure 3 <vpc_peering_0012__en-us_topic_0000001252180225_fig10553152375617>`, if you create a VPC peering connection between Subnet-A01 and Subnet-B02, the route tables are shown in :ref:`Table 3 <vpc_peering_0012__en-us_topic_0000001252180225_table45541823135611>`. In the rtb-VPC-B route table, the custom route for routing traffic from Subnet-B02 to Subnet-A01 and the local route have overlapping destinations. The local route has a higher priority and traffic will be forwarded within Subnet-B02 and cannot reach Subnet-A01.

      .. _vpc_peering_0012__en-us_topic_0000001252180225_fig10553152375617:

      .. figure:: /_static/images/en-us_image_0000002555955823.png
         :alt: **Figure 3** Networking diagram (IPv4)

         **Figure 3** Networking diagram (IPv4)

      .. _vpc_peering_0012__en-us_topic_0000001252180225_table45541823135611:

      .. table:: **Table 3** VPC route table details

         +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
         | Route Table | Destination              | Next Hop   | Route Type | Description                                                                                      |
         +=============+==========================+============+============+==================================================================================================+
         | rtb-VPC-A   | 10.0.0.0/24              | Local      | System     | Local routes are automatically added by the system for communications within a VPC.              |
         +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
         |             | 10.0.1.0/24              | Local      | System     |                                                                                                  |
         +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
         |             | 10.0.2.0/24 (Subnet-B02) | Peering-AB | Custom     | Add a route with the CIDR block of Subnet-B02 as the destination and Peering-AB as the next hop. |
         +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
         | rtb-VPC-B   | 10.0.0.0/24              | Local      | System     | Local routes are automatically added by the system for communications within a VPC.              |
         +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
         |             | 10.0.2.0/24              | Local      | System     |                                                                                                  |
         +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
         |             | 10.0.0.0/24 (Subnet-A01) | Peering-AB | Custom     | Add a route with the CIDR block of Subnet-A01 as the destination and Peering-AB as the next hop. |
         +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+

   If the subnets connected by a VPC peering connection do not overlap, the connection will take effect. As shown in :ref:`Figure 4 <vpc_peering_0012__en-us_topic_0000001252180225_fig6706153617587>`, you can create a VPC peering connection between Subnet-A02 and Subnet-B02. In this case, the routes do not conflict and the VPC peering connection takes effect.

   .. _vpc_peering_0012__en-us_topic_0000001252180225_fig6706153617587:

   .. figure:: /_static/images/en-us_image_0000002524875918.png
      :alt: **Figure 4** Networking diagram (IPv4)

      **Figure 4** Networking diagram (IPv4)

   If two VPCs want to use their IPv6 CIDR blocks for communication by a VPC peering connection but the IPv4 CIDR blocks of the VPCs or subnets overlap, the connection is not usable.


   .. figure:: /_static/images/en-us_image_0000002555955825.png
      :alt: **Figure 5** Networking diagram (IPv6)

      **Figure 5** Networking diagram (IPv6)

.. _vpc_peering_0012__en-us_topic_0000001252180225_section633272018142:

Invalid VPC Peering for Sharing an EIP
--------------------------------------

As shown in :ref:`Figure 6 <vpc_peering_0012__en-us_topic_0000001252180225_fig18332152061410>`, although VPC-A and VPC-B are peered and ECS-A01 in VPC-A has an EIP, ECS-B01 in VPC-B cannot access the Internet using the EIP bound to ECS-A01.

.. _vpc_peering_0012__en-us_topic_0000001252180225_fig18332152061410:

.. figure:: /_static/images/en-us_image_0000002524875922.png
   :alt: **Figure 6** Networking diagram

   **Figure 6** Networking diagram
