:original_name: overview_0003.html

.. _overview_0003:

Notes and Constraints
=====================

Security Group
--------------

-  By default, you can create a maximum of 100 security groups in your cloud account.
-  By default, you can add up to 50 security group rules to a security group.
-  When creating a private network load balancer, you need to select a desired security group. Do not delete the default security group rules or ensure that the following requirements are met:

   -  Outbound rules: only allow data packets to the selected security group or only data packets from the peer load balancer.
   -  Inbound rules: only allow data packets from the selected security group or only data packets from the peer load balancer.

Firewall
--------

-  By default, you can create a maximum of 200 firewalls in your cloud account.
-  You can associate a firewall with multiple subnets. However, a subnet can only be associated with one firewall at a time.
-  A firewall can contain no more than 20 rules in one direction, or performance will deteriorate.
-  For optimal performance, import no more than 40 firewall rules at a time. Existing rules will still be available after new rules are imported. Each rule can be imported only once.

Route Table
-----------

-  You can add routes to, delete routes from, and modify routes in the default route table, but cannot delete the table.
-  When you create a VPC endpoint, VPN or Direct Connect connection, the default route table automatically delivers a route that cannot be deleted or modified.

VPC Peering Connection
----------------------

-  A VPC peering connection can only connect VPCs in the same region.
-  If the local and peer VPCs have overlapping CIDR blocks, the VPC peering connection may not take effect.
-  A VPC cannot use EIPs of its peered VPC for Internet access. For example, if VPC A is peered with VPC B that has EIPs, VPC A cannot use EIPs in VPC B to access the Internet.

VPC Flow Log
------------

-  Currently, only C3, M3, and S2 ECSs support VPC flow logs.
-  By default, you can create a maximum of 10 VPC flow logs.
-  By default, a maximum of 400,000 flow log records are supported.

Virtual IP Address
------------------

-  Virtual IP addresses are not recommended when multiple NICs in the same subnet are configured on an ECS. It is too easy for there to be route conflicts on the ECS, which would cause communication failure using the virtual IP address.

EIP
---

-  Each EIP can only be bound to one cloud resource.
-  An EIP that has already been bound to a cloud resource cannot be bound to another resource without first being unbound from the current resource.
-  You can only release EIPs that are not bound to any resources.
-  The system preferentially assigns EIPs to you from the ones you released, if any. However, if any of these EIPs is already assigned to another user, it cannot be re-assigned to you.
-  EIPs cannot be transferred across accounts.

Bandwidth
---------

-  A dedicated bandwidth can control how much data can be transferred using a single EIP.
-  A shared bandwidth cannot control how much data can be transferred using a single EIP. Data transfer rate on EIPs cannot be customized.
-  A shared bandwidth or dedicated bandwidth can only be used by resources owned by the same account.

.. note::

   -  Inbound bandwidth is the bandwidth consumed when data is transferred from the Internet to the cloud. Outbound bandwidth is the bandwidth consumed when data is transferred from the cloud to the Internet.
