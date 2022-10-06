:original_name: vpc_faq_0068.html

.. _vpc_faq_0068:

Are There Any Constraints on Using VPC Peering Connections?
===========================================================

-  If two VPCs connected by a VPC peering connection overlap with each other, there will be route conflicts and the VPC peering connection may not be usable.

   After a VPC peering connection is created, the ping command can be used to check whether two VPCs can communicate with each other, but cannot be used to check whether the gateway of the peer subnet is connected.

-  If two VPCs overlap with each other, you can only create a VPC peering connection to enable communication between specific (non-overlapping) subnets in the VPCs. Ensure that the subnets to be peered do not overlap.

-  If there are three VPCs, A, B, and C, and VPC A is peered with both VPC B and VPC C, but VPC B and VPC C overlap with each other, you cannot configure routes with the same destinations for VPC A.

-  You cannot have more than one VPC peering connection between the same two VPCs at the same time.

-  A VPC peering connection between VPCs in different regions will not take effect.

-  You cannot use the EIPs in a VPC to access resources in a peered VPC. For example, VPC A is peered with VPC B, and VPC B has EIPs that can be used to access the Internet, you cannot use EIPs in VPC B to access the Internet from VPC A.

-  If you request a VPC peering connection with a VPC of another account, the connection takes effect only after the peer account accept the request. If you request a VPC peering connection with a VPC of your own, the system automatically accepts the request and activates the connection.

-  To ensure security, do not accept VPC peering connections from unknown accounts.

-  The owner either of a VPC in a peering connection can delete the VPC peering connection at any time. If a VPC peering connection is deleted by one of its owners, all information about this connection will also be deleted immediately, including routes added for the VPC peering connection.

-  After a VPC peering connection is established, the local and peer accounts must add routes to the route tables of the local and peer VPCs to enable communication between the two VPCs.

-  You cannot delete a VPC that has routes configured for a VPC peering connection.
