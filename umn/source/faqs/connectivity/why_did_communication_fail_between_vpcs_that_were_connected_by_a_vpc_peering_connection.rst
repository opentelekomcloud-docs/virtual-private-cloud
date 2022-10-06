:original_name: vpc_faq_0069.html

.. _vpc_faq_0069:

Why Did Communication Fail Between VPCs That Were Connected by a VPC Peering Connection?
========================================================================================

#. Check whether the VPC IDs are correctly configured for the VPC peering connection.
#. Check whether the VPCs have routes that point to the CIDR block of the other VPC.
#. Check whether the VPCs have routes that point to the subnet CIDR block of the other VPC if the two VPCs have overlapping CIDR blocks.
#. Check whether the VPCs contain overlapping subnets.
#. Check whether required security group rules have been configured for the ECSs that need to communicate with each other and whether restriction rules have been added to the iptables or firewalls used by the ECSs.
#. If a message indicating that this route already exists is displayed when you add a route for a VPC peering connection, check whether the destination of a VPN, Direct Connect, or VPC peering connection route already exists.
#. If the route destination of the VPC peering connection overlaps with that of a Direct Connect or VPN connection, the route may be invalid.
#. If VPCs in a VPC peering connection cannot communicate with each other after all these possible faults have been rectified, contact customer service.
