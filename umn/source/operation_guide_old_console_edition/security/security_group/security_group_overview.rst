:original_name: vpc_SecurityGroup02_0001.html

.. _vpc_SecurityGroup02_0001:

Security Group Overview
=======================

Security Group
--------------

A security group is a collection of access control rules for cloud resources, such as cloud servers, containers, and databases, that have the same security protection requirements and that are mutually trusted within a VPC. After a security group is created, you can create various access rules for the security group, these rules will apply to all cloud resources added to this security group.

Your account automatically comes with a default security group. The default security group allows all outbound traffic, denies all inbound traffic, and allows all traffic between cloud resources in the group. Your cloud resources in this security group can communicate with each other already without adding additional rules. You can directly use the default security group. For details, see :ref:`Default Security Groups and Security Group Rules <vpc_securitygroup02_0002>`.

You can also create custom security groups to meet your specific service requirements. For details, see :ref:`Creating a Security Group <vpc_securitygroup02_0004>`.

Security Group Basics
---------------------

-  You can associate instances, such as servers and extension NICs, with one or more security groups.

   You can change the security groups that are associated with instances, such as servers or extension NICs. By default, when you create an instance, it is associated with the default security group of its VPC unless you specify another security group.

-  You need to add security group rules to allow instances in the same security group to communicate with each other.

-  Security groups are stateful. If you send a request from your instance and the outbound traffic is allowed, the response traffic for that request is allowed to flow in regardless of inbound security group rules. Similarly, if inbound traffic is allowed, responses to allowed inbound traffic are allowed to flow out, regardless of outbound rules.

   Security groups use connection tracking to track traffic to and from instances that they contain and security group rules are applied based on the connection status of the traffic to determine whether to allow or deny traffic. If you add, modify, or delete a security group rule, or create or delete an instance in the security group, the connection tracking of all instances in the security group will be automatically cleared. In this case, the inbound or outbound traffic of the instance will be considered as new connections, which need to match the inbound or outbound security group rules to ensure that the rules take effect immediately and the security of incoming traffic.

   In addition, if the inbound or outbound traffic of an instance has no packets for a long time, the traffic will be considered as new connections after the connection tracking times out, and the connections need to match the outbound and inbound rules. The timeout period of connection tracking varies according to the protocol. The timeout period of a TCP connection in the established state is 600s, and the timeout period of an ICMP connection is 30s. For other protocols, if packets are received in both directions, the connection tracking timeout period is 180s. If one or more packets are received in one direction but no packet is received in the other direction, the connection tracking timeout period is 30s. For protocols other than TCP, UDP, and ICMP, only the IP address and protocol number are tracked.

.. note::

   If two ECSs are in the same security group but in different VPCs, the ECSs cannot communicate with each other. To enable communications between the ECSs, use a VPC peering connection to connect the two VPCs.

Security Group Rules
--------------------

After you create a security group, you can add rules to the security group. A rule applies either to inbound traffic or outbound traffic. After you add cloud resources to the security group, they are protected by the rules of the group.

Each security group has its default rules. For details, see :ref:`Table 1 <vpc_securitygroup02_0002__en-us_topic_0118534003_table493045171919>`. You can also customize security group rules. For details, see :ref:`Adding a Security Group Rule <vpc_securitygroup02_0005>`.

Security Group Constraints
--------------------------

-  By default, you can create a maximum of 100 security groups in your cloud account.
-  By default, you can add up to 50 security group rules to a security group.
-  By default, you can add an ECS or an extension NIC to a maximum of five security groups. In such a case, the rules of all the selected security groups are aggregated to take effect.
-  When creating a private network load balancer, you need to select a desired security group. Do not delete the default security group rules or ensure that the following requirements are met:

   -  Outbound rules: only allow data packets to the selected security group or only data packets from the peer load balancer.
   -  Inbound rules: only allow data packets from the selected security group or only data packets from the peer load balancer.
