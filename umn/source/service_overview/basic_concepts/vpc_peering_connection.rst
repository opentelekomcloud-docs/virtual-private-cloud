:original_name: vpc_Concepts_0011.html

.. _vpc_Concepts_0011:

VPC Peering Connection
======================

A VPC peering connection is a network connection between two VPCs in one region that enables you to route traffic between them using private IP addresses. ECSs in either VPC can communicate with each other just as if they were in the same region. You can create a VPC peering connection between your own VPCs, or between your VPC and another account's VPC within the same region. However, you cannot create a VPC peering connection between VPCs in different regions.

Each account can have a maximum of 50 VPC peering connections in each region by default.

-  VPC peering connections between VPCs in one account: Each account can create a maximum of 50 VPC peering connections in one region.

-  VPC peering connections between VPCs of different accounts: Accepted VPC peering connections use the quotas of both accounts. To-be-accepted VPC peering connections only use the quotas of accounts that request the connections.

   An account can create VPC peering connections with different accounts if the account has enough quota.

For details about VPC peering connections, see :ref:`VPC Peering Connection <vpc_peering_0000>`.
