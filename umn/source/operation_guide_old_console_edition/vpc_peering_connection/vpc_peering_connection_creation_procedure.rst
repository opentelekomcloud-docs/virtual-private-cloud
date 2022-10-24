:original_name: vpc_peering02_0001.html

.. _vpc_peering02_0001:

VPC Peering Connection Creation Procedure
=========================================

A VPC peering connection is a network connection between two VPCs in one region that enables you to route traffic between them using private IP addresses. ECSs in either VPC can communicate with each other just as if they were in the same region. You can create a VPC peering connection between your own VPCs, or between your VPC and another account's VPC within the same region. However, you cannot create a VPC peering connection between VPCs in different regions.

-  Creating a VPC peering connection between VPCs in your account


   .. figure:: /_static/images/en-us_image_0162335561.png
      :alt: **Figure 1** Creating a VPC peering connection between VPCs in your account

      **Figure 1** Creating a VPC peering connection between VPCs in your account

   If you create a VPC peering connection between two VPCs in your account, the system accepts the connection by default. You need to add routes for the local and peer VPCs to enable communication between the two VPCs.

-  Creating a VPC peering connection with a VPC in another account


   .. figure:: /_static/images/en-us_image_0162335565.png
      :alt: **Figure 2** Creating a VPC peering connection with a VPC in another account

      **Figure 2** Creating a VPC peering connection with a VPC in another account

   If you create a VPC peering connection between your VPC and a VPC that is in another account, the VPC peering connection will be in the **Awaiting acceptance** state. After the owner of the peer account accepts the connection, the connection status changes to **Accepted**. The owners of both the local and peer accounts must configure the routes required by the VPC peering connection to enable communication between the two VPCs.

   If the local and peer VPCs have overlapping CIDR blocks, the routes added for the VPC peering connection may become invalid. Before creating a VPC peering connection between two VPCs that have overlapping CIDR blocks, ensure that none of the subnets in the two VPCs overlap. If none of the subnets in the two VPCs overlap, the VPC peering connection you created enables communication between subnets in the two VPCs.

   After a VPC peering connection is created, you can use the ping command to check whether the local network is connected. The ping command cannot be used to check whether the gateway of the peer subnet is connected.
