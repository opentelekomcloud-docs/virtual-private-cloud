:original_name: acl_0001.html

.. _acl_0001:

Firewall Overview
=================

Firewall
--------

A firewall is an optional layer of protection for your subnets. After you add inbound and outbound rules to a firewall and associate subnets with it, you can control traffic in and out of the subnets.

A firewall is different from a security group. A security group protects the instances in it, such as ECSs, databases, and containers, while a firewall protects the entire subnet. Security groups are a mandatory layer of protection but firewalls are optional. They can work together for fine-grained and comprehensive access control.

A firewall contains inbound and outbound rules. You can specify the protocol, source port and address, and destination port and address for each rule. Suppose you have two subnets in **VPC-X** of region A, as shown in :ref:`Figure 1 <acl_0001__fig8518231453>`. **Subnet-X01** is associated with firewall **Fw-A**, and ECSs deployed in this subnet provide web services accessible from the Internet. **Subnet-X02** is associated with firewall **Fw-B**. **Subnet-X02** and **Subnet-Y01** are connected through a VPC peering connection. You also need inbound and outbound rules to allow **ECS-C01** in **Subnet-Y01** to remotely log in to ECSs in **Subnet-X02**.

-  Inbound and outbound rules of **Fw-A**:

   The custom inbound rule allows any IP address to access the ECSs in **Subnet-X01** over port 80 using TCP (HTTP). If the traffic does not match the custom rule, the default rule is applied and the traffic is denied to enter the subnet.

   Stateful firewalls allow responses to inbound requests to leave the subnet without being controlled by rules. The responses from ECSs in **Subnet-X01** can leave the subnet. Other outbound traffic is denied to leave **Subnet-X01** because the default rule is applied.

-  Inbound and outbound rules of **Fw-B**:

   The custom rule in the inbound direction allows access from **Subnet-Y01** to ECSs in **Subnet-X02** over port 22 using TCP (SSH).

   The custom rule in the outbound direction allows all ICMP traffic over any port. The ping traffic from ECSs in **Subnet-X02** can be routed to ECSs in **Subnet-Y01** to test the network connectivity.

.. _acl_0001__fig8518231453:

.. figure:: /_static/images/en-us_image_0000002524443086.png
   :alt: **Figure 1** Architecture and firewall rules

   **Figure 1** Architecture and firewall rules

.. _acl_0001__section31493412299:

Firewall Rules
--------------

-  firewall has inbound and outbound rules that are used to control traffic in and out of subnets.

   -  **Inbound rules** control traffic sent to the instances in a subnet.
   -  **Outbound rules** control traffic from the instances in a subnet to external networks.

-  You need to define the protocol, source and destination ports, source and destination addresses, and other information for firewall rules.

   -  **Rule Number**: Rules of a firewall are matched in ascending order, from the lowest to highest rule number.

      The default firewall rule is marked with an asterisk (``*``) and is the very last rule that will be used for matching.

   -  **Type**: **IPv4** or **IPv6**.

   -  **Action**: **Allow** or **Deny**. If the protocol, source or destination port, and source or destination address of the traffic matches a firewall rule, the action defined in the rule is taken to allow or deny the traffic.

   -  **Protocol**: The protocol to match traffic. The value can be **TCP**, **UDP**, or **ICMP**.

      -  **TCP** is ideal for applications that require reliable connections and high data integrity, such as remote login, web browsing, email, and file transfers.
      -  **UDP** is ideal for applications demanding high speed and low latency, such as online gaming and video meetings.
      -  **ICMP** can be used for monitoring or network diagnostic purposes. For example, ping can be used to test the connectivity between network devices, error reports can be generated for O&M, and diagnosis information can be transmitted for network analysis and optimization.

   -  **Source**/**Destination**: The source or destination of the traffic.

      The source or destination can be an IP address or IP address group.

      -  **IP address**: An IP address or CIDR block. Both IPv4 and IPv6 addresses are supported. For example, 192.168.10.10/32 (IPv4 address), 192.168.1.0/24 (IPv4 CIDR block), or 2407:c080:802:469::/64 (IPv6 CIDR block).

         To control the traffic from the Internet to an ECS with an EIP bound, you only need to set the destination in a firewall rule to the private IP address of the ECS. When the firewall rule takes effect, the system automatically translates the EIP to the private IP address of the ECS.

      -  **IP address group**: You can add multiple IP addresses with the same security requirements to an IP address group and select this IP address group when you configure a rule. This helps you manage them in an easier way. For details, see :ref:`IP Address Group Overview <vpc_ipaddressgroup_0002>`.

   -  **Source Port Range**/**Destination Port Range**: The source or destination ports and port ranges. The value ranges from 1 to 65535.

.. _acl_0001__section1952742625114:

How Firewall Rules Work
-----------------------

-  After a firewall is created, you can associate it with one or more subnets to control traffic in and out of the subnets. You can associate a firewall with multiple subnets. However, a subnet can only be associated with one firewall at a time.

-  Firewalls use connection tracking to track traffic to and from instances. Changes to inbound and outbound rules do not take effect immediately for the existing traffic.

   If you add, modify, or delete a firewall rule, or associate or disassociate a subnet with or from a firewall, all the inbound and outbound persistent connections will remain connected. New rules will only be applied for the new connections.

.. note::

   **After a persistent connection is disconnected, new connections will not be established immediately until the timeout period of connection tracking expires.** For example, after an ICMP persistent connection is disconnected, a new connection will be established and a new rule will be applied when the timeout period (30s) expires.

   -  **The timeout period of connection tracking varies by protocol.** The timeout period of a TCP connection in the established state is 600s. For an ICMP connection, it is 30s. For other protocols, if packets are received in both inbound and outbound directions, the connection tracking timeout period is 180s. If packets are received only in one direction, the connection tracking timeout period is 30s.
   -  **The timeout period of TCP connections varies by connection status.** The timeout period of a TCP connection in the established state is 600s, and that of a TCP connection in the FIN-WAIT state is 30s.

-  Each firewall has default rules, as shown in :ref:`Table 1 <acl_0001__table206881417172215>`. If a firewall has no custom rules, the default inbound and outbound rules are applied, denying all traffic in and out of a subnet. You can use the default rules only when there is no need for traffic to go in and out of a subnet. If the traffic needs to go in and out of the subnet, you need to add custom rules to control traffic as required.

   .. _acl_0001__table206881417172215:

   .. table:: **Table 1** Default rules of firewall

      +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+
      | Direction | Rule Number | Action | Protocol | Source    | Source Port Range | Destination | Destination Port Range |
      +===========+=============+========+==========+===========+===================+=============+========================+
      | Inbound   | \*          | Deny   | All      | 0.0.0.0/0 | All               | 0.0.0.0/0   | All                    |
      +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+
      | Outbound  | \*          | Deny   | All      | 0.0.0.0/0 | All               | 0.0.0.0/0   | All                    |
      +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+

-  The default and custom rules of a firewall do not apply to the traffic described in :ref:`Table 2 <acl_0001__table12313111113716>`.

   .. _acl_0001__table12313111113716:

   .. table:: **Table 2** Traffic not limited by firewall rules

      +-----------+----------------------------------------------------------------------------------------------------------------------------------------+
      | Direction | Description                                                                                                                            |
      +===========+========================================================================================================================================+
      | Inbound   | Traffic between the instances in the same subnet                                                                                       |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------+
      |           | Broadcast traffic to 255.255.255.255/32                                                                                                |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------+
      |           | Multicast traffic to 224.0.0.0/24                                                                                                      |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------+
      | Outbound  | Traffic between the instances in the same subnet                                                                                       |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------+
      |           | Broadcast traffic to 255.255.255.255/32                                                                                                |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------+
      |           | Multicast traffic to 224.0.0.0/24                                                                                                      |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------+
      |           | TCP metadata traffic to 169.254.169.254/32 over port 80                                                                                |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------+
      |           | Traffic to 100.125.0.0/16 that is reserved for public services on the cloud, such as the DNS server addresses and NTP server addresses |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------+

How Traffic Matches Firewall Rules
----------------------------------

A subnet can be associated with only one firewall. If there are multiple rules in a firewall, rules are matched in ascending order, from the lowest to highest rule number. The default firewall rule is marked with an asterisk (``*``) and is the very last rule that will be used for matching.

The matching sequence of inbound traffic is the same as that of outbound traffic. The following takes inbound traffic as an example to describe how the firewall rules are applied.

-  If a custom rule is matched and the **Action** of the rule is set to:

   -  **Deny**, the traffic is denied to enter the subnet.
   -  **Allow**, the traffic is allowed to enter the subnet.

-  If no custom rule is matched, the default rule is applied, denying traffic from entering the subnet.

Firewall Application Scenarios
------------------------------

-  If the application layer needs to provide services for external users, traffic from all IP addresses must be allowed to reach the application layer. However, you also need to prevent illegal access from malicious users.

   Solution: You can add firewall rules to deny access from malicious IP addresses.

-  How can I isolate ports with identified vulnerabilities? For example, how do I isolate port 445 that can be exploited by WannaCry worm?

   Solution: You can add firewall rules to deny access over a specific port and protocol, for example, port 445 and TCP.

-  There is no need to control the communications between instances within a subnet, but there is a need to control the communications between subnets.

   Solution: You can add firewall rules to control the communications between subnets.

-  For frequently accessed applications, rule sequences may need to be adjusted to improve performance.

   Solution: A firewall allows you to adjust the rule sequence so that frequently used rules are applied before other rules.

Firewall Configuration Procedure
--------------------------------

.. table:: **Table 3** Firewall configuration procedure description

   +-----------------+--------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+
   | No.             | Step                                             | Description                                                                                                                                                                           | Reference                                                           |
   +=================+==================================================+=======================================================================================================================================================================================+=====================================================================+
   | 1               | Create a firewall.                               | A firewall comes with default inbound and outbound rules that deny all traffic in and out of associated subnets.                                                                      | :ref:`Creating a Firewall <en-us_topic_0051746698>`                 |
   +-----------------+--------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+
   | 2               | Add firewall rules.                              | The default rules cannot be deleted or modified. You can add custom rules to control traffic in and out of a subnet. Traffic will be preferentially matched against the custom rules. | :ref:`Adding a Firewall Rule <en-us_topic_0051746702>`              |
   +-----------------+--------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+
   | 3               | Associate the firewall with one or more subnets. | You need to associate the firewall with one or more subnets. If the firewall is enabled, the firewall rules control the traffic in and out of the subnets.                            | :ref:`Associating Subnets with a Firewall <en-us_topic_0051746700>` |
   |                 |                                                  |                                                                                                                                                                                       |                                                                     |
   |                 |                                                  | A subnet can be associated with only one firewall.                                                                                                                                    |                                                                     |
   +-----------------+--------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+

Constraints on Using Firewalls
------------------------------

-  By default, each account can have up to 200 firewalls in a region.

-  A firewall can have no more than 20 rules in each direction, or the performance will deteriorate.

-  A firewall can have up to 124 rules to be associated with IP address groups in each direction.

-  For inbound rules of a firewall, the sum of the rules with **Source** set to **IP address group**, rules with **Destination** set to **IP address group**, rules with **Source Port Range** set to inconsecutive ports, and rules with **Destination Port Range** set to inconsecutive ports, cannot exceed 120. Excess rules will not take effect. If there are both IPv4 and IPv6 firewall rules, up to 120 rules can be added for each type.

   For outbound rules of a firewall, the sum of the rules with **Source** set to **IP address group**, rules with **Destination** set to **IP address group**, rules with **Source Port Range** set to inconsecutive ports, and rules with **Destination Port Range** set to inconsecutive ports, cannot exceed 120. Excess rules will not take effect.

   For example, to add inbound IPv4 rules to firewall **Fw-A**, you can refer to :ref:`Table 4 <acl_0001__table7602920143013>` for rules that meet the constraints. Of these rules, rule A02 uses inconsecutive ports as the source port range and IP address group as the source. In this case, only one quota is occupied.

   .. _acl_0001__table7602920143013:

   .. table:: **Table 4** Inbound firewall rules

      +----------+-------------+------+--------+----------+-----------------------------+-------------------+-----------------------------+------------------------+
      | Rule     | Rule Number | Type | Action | Protocol | Source                      | Source Port Range | Destination                 | Destination Port Range |
      +==========+=============+======+========+==========+=============================+===================+=============================+========================+
      | Rule A01 | 1           | IPv4 | Deny   | TCP      | 0.0.0.0/0                   | 22,25,27          | 0.0.0.0/0                   | 1-65535                |
      +----------+-------------+------+--------+----------+-----------------------------+-------------------+-----------------------------+------------------------+
      | Rule A02 | 2           | IPv4 | Allow  | TCP      | IP address group: ipGroup-A | 22-24,25          | 0.0.0.0/0                   | 1-65535                |
      +----------+-------------+------+--------+----------+-----------------------------+-------------------+-----------------------------+------------------------+
      | Rule A03 | 3           | IPv4 | Allow  | All      | 0.0.0.0/0                   | All               | IP address group: ipGroup-B | All                    |
      +----------+-------------+------+--------+----------+-----------------------------+-------------------+-----------------------------+------------------------+
      | Rule A04 | 4           | IPv4 | Allow  | UDP      | 0.0.0.0/0                   | 1-65535           | 0.0.0.0/0                   | 80-83,87               |
      +----------+-------------+------+--------+----------+-----------------------------+-------------------+-----------------------------+------------------------+

-  Traffic from load balancers is not limited by firewall and security group rules if:

   **Transfer Client IP Address** is enabled for the listeners of a load balancer.

   The load balancer can still forward traffic to backend servers, even if there is a rule that denies traffic from the load balancer to the backend servers.
