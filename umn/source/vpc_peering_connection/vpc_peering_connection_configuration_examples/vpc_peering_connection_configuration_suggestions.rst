:original_name: en-us_topic_0046809840.html

.. _en-us_topic_0046809840:

VPC Peering Connection Configuration Suggestions
================================================

A VPC peering connection is a networking connection between two VPCs in the same region and enables them to communicate. :ref:`Table 1 <en-us_topic_0046809840__table18339193642913>` lists different scenarios of using VPC peering connections.

.. _en-us_topic_0046809840__table18339193642913:

.. table:: **Table 1** VPC peering connection usage examples

   +-------------------------+-----------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | Location                | CIDR Block                                    | Description                                                                                                                                    | Usage Example                                                                              |
   +=========================+===============================================+================================================================================================================================================+============================================================================================+
   | VPCs in the same region | -  VPC CIDR blocks do not overlap.            | You can create VPC peering connections to connect entire CIDR blocks of VPCs. Then, all resources in the VPCs can communicate with each other. | :ref:`Using a VPC Peering Connection to Connect Two VPCs <vpc_peering_0009>`               |
   |                         | -  Subnet CIDR blocks of VPCs do not overlap. |                                                                                                                                                |                                                                                            |
   +-------------------------+-----------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | VPCs in the same region | -  VPC CIDR blocks overlap.                   | You can create VPC peering connections to connect specific subnets or ECSs from different VPCs.                                                | -  :ref:`Using a VPC Peering Connection to Connect Subnets in Two VPCs <vpc_peering_0010>` |
   |                         | -  Some subnet CIDR blocks overlap.           |                                                                                                                                                | -  :ref:`Using a VPC Peering Connection to Connect ECSs in Two VPCs <vpc_peering_0011>`    |
   |                         |                                               | -  To connect specific subnets from two VPCs, the subnet CIDR blocks cannot overlap.                                                           |                                                                                            |
   |                         |                                               | -  To connect specific ECSs from two VPCs, each ECS must have a unique private IP address.                                                     |                                                                                            |
   +-------------------------+-----------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | VPCs in the same region | -  VPC CIDR blocks overlap.                   | VPC peering connections are not usable.                                                                                                        | :ref:`Unsupported VPC Peering Configurations <vpc_peering_0012>`                           |
   |                         | -  All subnet CIDR blocks overlap.            |                                                                                                                                                |                                                                                            |
   +-------------------------+-----------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
