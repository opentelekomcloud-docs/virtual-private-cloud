:original_name: en-us_topic_0073379079.html

.. _en-us_topic_0073379079:

Security Group Overview
=======================

Security Group
--------------

A security group is a collection of access control rules for cloud resources, such as cloud servers, containers, and databases, that have the same security protection requirements and that are mutually trusted. After a security group is created, you can create various access rules for the security group, these rules will apply to all cloud resources added to this security group.

Like whitelists, security group rules work as follows:

-  Inbound rule: If an inbound request matches the source in an inbound security group rule with **Action** set to **Allow**, the request is allowed.

   Unless otherwise specified, you do not need to configure deny rules in the inbound direction because requests that do not match allow rules will be denied.

-  Outbound rule: If the destination of an outbound security group rule with **Action** set to **Allow** is 0.0.0.0/0, all outbound requests are allowed.

   IPv4 default route: 0.0.0.0/0

   IPv6 default route: ::/0

:ref:`Table 1 <en-us_topic_0073379079__table102261597217>` shows the inbound and outbound rules in security group sg-AB.

.. _en-us_topic_0073379079__table102261597217:

.. table:: **Table 1** Rules in security group sg-AB

   +-----------+--------+-----------------+------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | Direction | Action | Protocol & Port | Source or Destination  | Description                                                                                                                               |
   +===========+========+=================+========================+===========================================================================================================================================+
   | Inbound   | Allow  | All             | Source: sg-AB          | Allows access requests from security group sg-AB. This rule ensures that instances in the security group can communicate with each other. |
   +-----------+--------+-----------------+------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | Outbound  | Allow  | All             | Destination: 0.0.0.0/0 | Allows all requests in the security group to be sent out.                                                                                 |
   +-----------+--------+-----------------+------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+

The system automatically creates a default security group for each account. If the default security group does not meet your requirements, you can :ref:`modify security group rules <vpc_securitygroup_0005>` or :ref:`create a custom security group <en-us_topic_0013748715>`.

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

Each security group has its default rules. For details, see :ref:`Table 1 <securitygroup_0003__table493045171919>`. You can also customize security group rules. For details, see :ref:`Adding a Security Group Rule <en-us_topic_0030969470>`.

Security Group Constraints
--------------------------

-  By default, you can create a maximum of 100 security groups in your cloud account.
-  By default, you can add up to 50 security group rules to a security group.
-  When creating a private network load balancer, you need to select a desired security group. Do not delete the default security group rules or ensure that the following requirements are met:

   -  Outbound rules: only allow data packets to the selected security group or only data packets from the peer load balancer.
   -  Inbound rules: only allow data packets from the selected security group or only data packets from the peer load balancer.
