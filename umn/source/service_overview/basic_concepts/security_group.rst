:original_name: vpc_Concepts_0005.html

.. _vpc_Concepts_0005:

Security Group
==============

A security group is a collection of access control rules for cloud resources, such as cloud servers, containers, and databases, that have the same security protection requirements and that are mutually trusted. After a security group is created, you can create various access rules for the security group, these rules will apply to all cloud resources added to this security group.

Like whitelists, security group rules work as follows:

-  Inbound rule: If an inbound request matches the source in an inbound security group rule with **Action** set to **Allow**, the request is allowed.

   Unless otherwise specified, you do not need to configure deny rules in the inbound direction because requests that do not match allow rules will be denied.

-  Outbound rule: If the destination of an outbound security group rule with **Action** set to **Allow** is 0.0.0.0/0, all outbound requests are allowed.

   IPv4 default route: 0.0.0.0/0

   IPv6 default route: ::/0

:ref:`Table 1 <vpc_concepts_0005__en-us_topic_0073379079_table102261597217>` shows the inbound and outbound rules in security group sg-AB.

.. _vpc_concepts_0005__en-us_topic_0073379079_table102261597217:

.. table:: **Table 1** Rules in security group sg-AB

   +-----------+--------+-----------------+------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | Direction | Action | Protocol & Port | Source or Destination  | Description                                                                                                                               |
   +===========+========+=================+========================+===========================================================================================================================================+
   | Inbound   | Allow  | All             | Source: sg-AB          | Allows access requests from security group sg-AB. This rule ensures that instances in the security group can communicate with each other. |
   +-----------+--------+-----------------+------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | Outbound  | Allow  | All             | Destination: 0.0.0.0/0 | Allows all requests in the security group to be sent out.                                                                                 |
   +-----------+--------+-----------------+------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
