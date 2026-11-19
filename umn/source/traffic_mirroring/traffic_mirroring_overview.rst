:original_name: vpc_mirror_02.html

.. _vpc_mirror_02:

Traffic Mirroring Overview
==========================

What Is Traffic Mirroring?
--------------------------

Traffic Mirroring can be used to mirror traffic that meets a mirror filter from mirror sources, such as elastic network interfaces. You can configure inbound and outbound rules for a mirror filter to determine which traffic will be mirrored from mirror sources to a mirror target, such as a network interface or load balancer. You can then send the traffic for inspection, audit analysis, and troubleshooting.

.. note::

   Currently, the Traffic Mirroring function is free. You will be notified in advance if the billing starts.

Concepts
--------

The following are the concepts for Traffic Mirroring:

-  A **mirror filter** is a set of inbound rules and outbound rules to determine the traffic that is mirrored. You can specify matching criteria, such as priority and action for each rule.

   -  Inbound rules match the traffic received by a mirror source.
   -  Outbound rules match the traffic sent by a mirror source.

-  A **mirror source** is an elastic network interface and traffic on an elastic network interface needs to be mirrored.
-  A **mirror target** is a network interface of a cloud server or a load balancer, which is used to receive mirrored traffic.
-  A **mirror session** can be associated with a mirror filter, multiple mirror sources, and a mirror target. A mirror session mirrors traffic from a mirror source to a mirror target that meets the mirror filter.

Working Principles
------------------

The following describes the working principles of traffic mirroring. As shown in :ref:`Figure 1 <vpc_mirror_02__en-us_topic_0000001651378981_fig98711514192716>`, a mirror session is associated with two mirror sources, one mirror filter, and one mirror target.

-  Mirror source 01 is network interface-B that is attached to ECS-B. To access ECS-A from ECS-B, the outbound and inbound traffic of network interface-B is mirrored.
-  Mirror source 02 is network interface-C that is attached to ECS-C. To access ECS-C from the Internet, the outbound and inbound traffic of network interface-C is mirrored.
-  The mirror filter contains both inbound and outbound rules.
-  The mirror target is a load balancer that receives mirrored traffic.

In :ref:`Table 1 <vpc_mirror_02__en-us_topic_0000001651378981_table198114341557>`, mirror sources network interface-B and network interface-C are used as examples to describe the traffic mirroring principle.

.. _vpc_mirror_02__en-us_topic_0000001651378981_fig98711514192716:

.. figure:: /_static/images/en-us_image_0000002581268320.png
   :alt: **Figure 1** Traffic mirroring architecture

   **Figure 1** Traffic mirroring architecture

.. _vpc_mirror_02__en-us_topic_0000001651378981_table198114341557:

.. table:: **Table 1** Mirror path of packets

   +---------------------+----------------------------+--------------------+-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mirror Source       | Access Path                | Packet             | Direction | Description                                                                                                                                                                                |
   +=====================+============================+====================+===========+============================================================================================================================================================================================+
   | Network interface-B | From ECS-B to ECS-A        | Request packet 01  | Outbound  | Request packet 01 from ECS-B is an outbound packet for network interface-B. If packet 01 matches the outbound rules of the mirror filter, packet 01 is mirrored to the load balancer.      |
   +---------------------+----------------------------+--------------------+-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                     |                            | Response packet 02 | Inbound   | Response packet 02 from ECS-A is an inbound packet for network interface-B. If packet 02 matches the inbound rules of the mirror filter, packet 02 is mirrored to the load balancer.       |
   +---------------------+----------------------------+--------------------+-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Network interface-C | From the Internet to ECS-C | Request packet 03  | Inbound   | Request packet 03 from the Internet is an inbound packet for network interface-C. If packet 03 matches the inbound rules of the mirror filter, packet 03 is mirrored to the load balancer. |
   +---------------------+----------------------------+--------------------+-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                     |                            | Response packet 04 | Outbound  | Response packet 04 from ECS-C is an outbound packet for network interface-C. If packet 04 matches the outbound rules of the mirror filter, packet 04 is mirrored to the load balancer.     |
   +---------------------+----------------------------+--------------------+-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

:ref:`Table 2 <vpc_mirror_02__en-us_topic_0000001651378981_table42954412446>` shows rules in a mirror filter and describes how the mirror session filters traffic using the mirror filter.

.. _vpc_mirror_02__en-us_topic_0000001651378981_table42954412446:

.. table:: **Table 2** Traffic filtering description

   +-----------+----------+----------+--------+------+----------------+-------------------+-------------+------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Direction | Priority | Protocol | Action | Type | Source         | Source Port Range | Destination | Destination Port Range | Filtering Description                                                                                                                |
   +===========+==========+==========+========+======+================+===================+=============+========================+======================================================================================================================================+
   | Inbound   | 1        | TCP      | Accept | IPv4 | 172.16.0.0/24  | 10000-10001       | 10.0.0.3/32 | 80-80                  | If traffic enters a network interface of the mirror source, the mirror session will mirror packets that meet the following rule:     |
   |           |          |          |        |      |                |                   |             |                        |                                                                                                                                      |
   |           |          |          |        |      |                |                   |             |                        | TCP (IPv4) packets from source 172.16.0.0/24 over port 10000 or 10001 to destination 10.0.0.3/32 over port 80                        |
   +-----------+----------+----------+--------+------+----------------+-------------------+-------------+------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Outbound  | 1        | All      | Reject | IPv4 | 192.168.0.0/24 | All               | 10.2.0.0/24 | All                    | If traffic leaves a network interface of the mirror source, the mirror session will not mirror packets that meet the following rule: |
   |           |          |          |        |      |                |                   |             |                        |                                                                                                                                      |
   |           |          |          |        |      |                |                   |             |                        | IPv4 packets from source 192.168.0.0/24 over any port to destination 10.2.0.0/24 over any port.                                      |
   +-----------+----------+----------+--------+------+----------------+-------------------+-------------+------------------------+--------------------------------------------------------------------------------------------------------------------------------------+

Application Scenarios
---------------------

-  Traffic inspection

   If there are network intrusions, you can use traffic mirroring to mirror required traffic to security software for comprehensive analysis and check. This helps to quickly locate security vulnerabilities and ensure network security.

-  Traffic auditing

   You can use traffic mirroring to mirror traffic to a specific platform for auditing and analysis. This applies to scenarios that have high security requirements, such as finance.

-  Fault locating

   O&M engineers can directly view mirrored traffic instead of capturing packets on service servers to locate faults. This prevents services from being affected during O&M.

Matching Rules
--------------

If a packet from the same mirror source meets multiple mirror filter rules, the packet is matched only once. The matching rules are described as follows:

.. table:: **Table 3** Matching rules

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Matching Rule                     | Description                                                                                                                                                                         |
   +===================================+=====================================================================================================================================================================================+
   | **Sequence match**                | Matching is performed in descending order of priority. A smaller value indicates a higher priority. For example, the priority of 1 is higher than that of 2.                        |
   |                                   |                                                                                                                                                                                     |
   |                                   | -  Mirror session priority: A mirror source can be associated with multiple mirror sessions at the same time. The mirror sessions are matched in descending order of priority.      |
   |                                   |                                                                                                                                                                                     |
   |                                   |    For details, see :ref:`the matching process of mirror sessions <vpc_mirror_02__en-us_topic_0000001651378981_li167114161324>`.                                                    |
   |                                   |                                                                                                                                                                                     |
   |                                   | -  Mirror filter rule priority: A mirror session can be associated with only one mirror filter that contains multiple rules. The rules are matched in descending order of priority. |
   |                                   |                                                                                                                                                                                     |
   |                                   |    An inbound or outbound mirror filter rule determines the traffic that is mirrored. You can specify matching criteria, such as priority and action for each rule.                 |
   |                                   |                                                                                                                                                                                     |
   |                                   |    For details, see :ref:`the matching process of mirror filter rules <vpc_mirror_02__en-us_topic_0000001651378981_li5449543173013>`.                                               |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Unique match**                  | If a packet matches a mirror filter rule, the packet does not attempt to match any other rules.                                                                                     |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _vpc_mirror_02__en-us_topic_0000001651378981_li167114161324:

   :ref:`Figure 2 <vpc_mirror_02__en-us_topic_0000001651378981_fig83763271782>` describes the matching process of mirror sessions. If a mirror source is associated with multiple mirror sessions, packets are matched in descending order of mirror session priorities. Inbound packets are used as an example here.

   -  If a packet matches an inbound mirror filter rule of a mirror session:

      -  The packet will be mirrored if the rule action is **Accept**.
      -  The packet will not be mirrored if the rule action is **Reject**.

   -  If a packet does not match any inbound mirror filter rule in a mirror session, the packet will not be mirrored.

   For example, a mirror source is associated with both mirror sessions A and B. The priority of mirror session A is 1 and that of mirror session B is 2. If a packet in the inbound direction of the mirror source meets the mirror filter rules of both mirror session A and mirror session B, the packet preferentially matches the mirror filter rules of mirror session A according to the priority, and will not match that of mirror session B.

   .. _vpc_mirror_02__en-us_topic_0000001651378981_fig83763271782:

   .. figure:: /_static/images/en-us_image_0000002611828077.png
      :alt: **Figure 2** Mirror session matching process

      **Figure 2** Mirror session matching process

-  .. _vpc_mirror_02__en-us_topic_0000001651378981_li5449543173013:

   :ref:`Figure 3 <vpc_mirror_02__en-us_topic_0000001651378981_fig1970521220173>` describes the matching process of mirror filter rules. If a mirror source is associated with only one mirror session, packets are matched in descending order of priorities of inbound mirror filter rules. Inbound packets are used as an example here.

   -  If a packet matches an inbound mirror filter rule:

      -  The packet will be mirrored if the rule action is **Accept**.
      -  The packet will not be mirrored if the rule action is **Reject**.

   -  If a packet does not match any inbound mirror filter rule, the packet will not be mirrored.

   For example, a mirror source is associated with mirror session A. The mirror filter of mirror session A has inbound rules A and B, which have the same traffic matching conditions but different priorities and actions. The priority of rule A is 1, and the action is **Reject**. The priority of rule B is 2, and the action is **Accept**. If a packet in the inbound direction of the mirror source meets the traffic matching conditions of both rule A and rule B, the packet matches rule A first according to the rule priority. The packet will be rejected and will not be mirrored or match rule B.

   .. _vpc_mirror_02__en-us_topic_0000001651378981_fig1970521220173:

   .. figure:: /_static/images/en-us_image_0000002581268322.png
      :alt: **Figure 3** Mirror filter rule matching process

      **Figure 3** Mirror filter rule matching process

Traffic Mirroring Quotas
------------------------

:ref:`Table 4 <vpc_mirror_02__en-us_topic_0000001651378981_table14258125544512>` lists the quotas about Traffic Mirroring resources. Some default quotas can be increased.

.. _vpc_mirror_02__en-us_topic_0000001651378981_table14258125544512:

.. table:: **Table 4** Quotas

   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------+------------------------------------------------------------------+
   | Item                                                                          | Default Quota                                                           | Adjustable                                                       |
   +===============================================================================+=========================================================================+==================================================================+
   | Maximum number of mirror sources that can be associated with a mirror session | 10                                                                      | Yes. For details, see :ref:`Managing VPC Quotas <vpc_faq_0051>`. |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------+------------------------------------------------------------------+
   | Maximum number of mirror sessions that can be associated with a mirror source | 3                                                                       | No                                                               |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------+------------------------------------------------------------------+
   | Maximum number of mirror targets that can be associated with a mirror session | 1                                                                       | No                                                               |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------+------------------------------------------------------------------+
   | Maximum number of mirror sessions that can be associated with a mirror target | -  10 (if the mirror target is the network interface of a cloud server) | No                                                               |
   |                                                                               | -  200 (if the mirror target is a load balancer)                        |                                                                  |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------+------------------------------------------------------------------+
   | Maximum number of mirror filters that can be associated with a mirror session | 1                                                                       | No                                                               |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------+------------------------------------------------------------------+
   | Maximum number of mirror sessions that can be associated with a mirror filter | 1,000                                                                   | No                                                               |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------+------------------------------------------------------------------+
   | Maximum number of rules that can be added to a mirror filter                  | -  10 inbound rules                                                     | No                                                               |
   |                                                                               | -  10 outbound rules                                                    |                                                                  |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------+------------------------------------------------------------------+
   | Maximum number of mirror sessions that can be created in a region             | 20,000                                                                  | No                                                               |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------+------------------------------------------------------------------+

.. _vpc_mirror_02__en-us_topic_0000001651378981_section1412134042913:

Notes and Constraints
---------------------

-  As shown in :ref:`Figure 4 <vpc_mirror_02__en-us_topic_0000001651378981_fig19131527173916>`, mirrored traffic is encapsulated in the standard VXLAN packet format. This means the original packets are encapsulated in the VXLAN headers and then transmitted as mirrored packets over the connection. To prevent a mirrored packet from being truncated when it exceeds the minimum MTU (1,500 bytes by default), you are advised to set the mirror source MTU (original packet length) to be 50 bytes less than the minimum MTU. For example, if the minimum MTU is 1,500 bytes, the mirror source MTU cannot exceed 1,450 bytes. This ensures that the total length of the original packet and the encapsulated packet does not exceed the connection MTU.

   .. _vpc_mirror_02__en-us_topic_0000001651378981_fig19131527173916:

   .. figure:: /_static/images/en-us_image_0000002611828079.png
      :alt: **Figure 4** Traffic Mirroring packet format

      **Figure 4** Traffic Mirroring packet format

-  :ref:`Table 5 <vpc_mirror_02__en-us_topic_0000001651378981_table553191774316>` and :ref:`Table 6 <vpc_mirror_02__en-us_topic_0000001651378981_table66725225618>` show the constraints on different types of mirror sources and mirror targets.

   .. _vpc_mirror_02__en-us_topic_0000001651378981_table553191774316:

   .. table:: **Table 5** Constraints on mirror sources

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Mirror Source Type                | Constraints                                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================================+
      | Elastic network interface         | -  If the mirror source is an elastic network interface, the network interface needs to be attached to an ECS. Only the network interfaces of ECSs with certain flavors (such as 9 series) can be used as mirror sources. |
      |                                   | -  An elastic network interface cannot be used as both a mirror source and a mirror target at the same time.                                                                                                              |
      |                                   | -  Traffic Mirroring occupies the bandwidth of instances attached to elastic network interfaces and does not have bandwidth limits.                                                                                       |
      |                                   | -  Elastic network interfaces can be used as mirror sources, but supplementary network interfaces cannot.                                                                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _vpc_mirror_02__en-us_topic_0000001651378981_table66725225618:

   .. table:: **Table 6** Constraints on mirror targets

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Mirror Target Type                | Constraints                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================+
      | Network interface                 | -  If a mirror target needs to receive mirrored traffic from multiple mirror sources, ensure that the mirror target has proper specifications based on service requirements. |
      |                                   | -  An elastic network interface cannot be used as both a mirror source and a mirror target at the same time.                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Load balancer                     | The encapsulated mirrored packet uses the IPv4 UDP protocol. So the dedicated load balancer used as the mirror target must support IPv4 UDP.                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  If a packet from a mirror source meets multiple mirror filter rules, the packet will be matched only once and will be accepted or rejected to a mirror target according to the rule action.

-  If a packet from a mirror source is discarded by a security group or network ACL, the packet will not be mirrored.

-  If a packet from a mirror source meets a mirror filter, the packet will be mirrored and will not be restricted by outbound rules of a security group or network ACL of the mirror source. This means you do not need to configure the security group or network ACL for the mirror source. However, if you want to mirror the packet to the mirror target, you need to configure the following rules for the security group and network ACL of the mirror target:

   -  Add a security group rule to allow UDP packets from the mirror source to the mirror target over port 4789.

      :ref:`Table 7 <vpc_mirror_02__en-us_topic_0000001651378981_table102261597217>` shows a rule example where the private IP address of the mirror source is 192.168.0.27. To learn about how to add a rule, see :ref:`Adding a Security Group Rule <en-us_topic_0030969470>`.

      .. _vpc_mirror_02__en-us_topic_0000001651378981_table102261597217:

      .. table:: **Table 7** Security group rule configuration example (a network interface as the mirror source)

         +-------------+-------------+-------------+-----------------+--------------------------------------------------+
         | Direction   | Action      | Type        | Protocol & Port | Source                                           |
         +=============+=============+=============+=================+==================================================+
         | Inbound     | Allow       | IPv4        | UDP: 4789       | 192.168.0.27/32                                  |
         |             |             |             |                 |                                                  |
         |             |             |             |                 | Set the source based on the actual requirements. |
         +-------------+-------------+-------------+-----------------+--------------------------------------------------+

   -  Add a network ACL rule to allow UDP packets from the mirror source to the mirror target over port 4789.

      :ref:`Table 8 <vpc_mirror_02__en-us_topic_0000001651378981_table20893171232719>` shows a rule example where the IP address of the mirror source is 192.168.0.27. To learn about how to add a rule, see :ref:`Adding a Firewall Rule <en-us_topic_0051746702>`.

      .. _vpc_mirror_02__en-us_topic_0000001651378981_table20893171232719:

      .. table:: **Table 8** Network ACL rule configuration example (a network interface as the mirror source)

         +-----------+--------+--------+----------+--------------------------------------------------+---------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
         | Direction | Type   | Action | Protocol | Source                                           | Source Port Range                     | Destination                                                                                                                                 | Destination Port Range                                                       |
         +===========+========+========+==========+==================================================+=======================================+=============================================================================================================================================+==============================================================================+
         | Inbound   | IPv4   | Allow  | UDP      | 192.168.0.27/32                                  | If not specified, all ports are used. | -  If the mirror target is a network interface, configure its private IPv4 address as the destination, for example, 192.168.1.24/32.        | 4789                                                                         |
         |           |        |        |          |                                                  |                                       | -  If the mirror target is a load balancer, configure its private IPv4 address as the destination, for example, 192.168.1.25/32.            |                                                                              |
         |           |        |        |          | Set the source based on the actual requirements. |                                       |                                                                                                                                             | Port 4789 must be opened. Open other ports based on the actual requirements. |
         |           |        |        |          |                                                  |                                       | Set the destination based on the actual requirements. Ensure that the IP address of the mirror target is within the destination CIDR block. |                                                                              |
         +-----------+--------+--------+----------+--------------------------------------------------+---------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------+

-  Resources from different VPCs cannot communicate with each other. If a mirror source and a mirror target are not in the same VPC, you need to use a VPC peering connection or an enterprise router to connect their VPCs first.

Usage Process
-------------

To use the traffic mirroring function, you need to create a mirror session and associate a mirror filter, mirror sources, and a mirror target with the mirror session. :ref:`Figure 5 <vpc_mirror_02__en-us_topic_0000001651378981_en-us_topic_0000001154868962_fig10285152624918>` shows the process.

.. _vpc_mirror_02__en-us_topic_0000001651378981_en-us_topic_0000001154868962_fig10285152624918:

.. figure:: /_static/images/en-us_image_0000002581268324.png
   :alt: **Figure 5** Process of using Traffic Mirroring

   **Figure 5** Process of using Traffic Mirroring

.. table:: **Table 9** Description of the Traffic Mirroring process

   +-----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | Step                                                | Description                                                                                                                                                                                                                       | Reference                                        |
   +=====================================================+===================================================================================================================================================================================================================================+==================================================+
   | Configure basic information about a mirror session. | Set parameters such as the name and priority of the mirror session.                                                                                                                                                               | :ref:`Creating a Mirror Session <vpc_mirror_12>` |
   +-----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | Associate a mirror filter.                          | Select a mirror filter and associate it with the mirror session.                                                                                                                                                                  |                                                  |
   |                                                     |                                                                                                                                                                                                                                   |                                                  |
   |                                                     | Each mirror session can have one mirror filter associated. If there is no mirror filter required, you can create one by referring to :ref:`Creating a Mirror Filter <vpc_mirror_04>`.                                             |                                                  |
   +-----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | Associate mirror sources.                           | Select an elastic network interface as the mirror source and associate it with the mirror session.                                                                                                                                |                                                  |
   |                                                     |                                                                                                                                                                                                                                   |                                                  |
   |                                                     | Each mirror session can be associated with multiple mirror sources.                                                                                                                                                               |                                                  |
   +-----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | Associate a mirror target.                          | Select the network interface of a cloud server or load balancer as the mirror target and associate it with the mirror session.                                                                                                    |                                                  |
   +-----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | Finish                                              | If the mirror session is enabled, the traffic that meets the mirror filter from the mirror source will be mirrored to the mirror target.                                                                                          |                                                  |
   |                                                     |                                                                                                                                                                                                                                   |                                                  |
   |                                                     | If you do not enable the mirror session when creating it, the traffic of the mirror source will not be mirrored. You can enable the mirror session by referring to :ref:`Enabling or Disabling a Mirror Session <vpc_mirror_13>`. |                                                  |
   +-----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------+
