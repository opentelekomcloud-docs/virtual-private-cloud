:original_name: vpc_faq_0079.html

.. _vpc_faq_0079:

How Do I Configure Policy-Based Routes for an ECS with Multiple Network Interfaces?
===================================================================================

Background
----------

If a cloud server has multiple network interfaces, the primary network interface can communicate with external networks by default, but the extended network interfaces cannot. To enable extended network interfaces to communicate with external networks, you need to configure policy-based routes for these network interfaces.

Scenarios
---------

The following describes how to configure policy-based routes for an ECS with two network interfaces. :ref:`Figure 1 <vpc_faq_0079__en-us_topic_0000001251530747_fig39726015294>` shows the networking.

-  The primary and extended network interfaces on the source ECS are in different subnets of the same VPC.
-  The source and destination ECSs are in different subnets of the same VPC, so the two ECSs can communicate with each other through primary network interfaces without configuring policy-based routes.
-  After policy-based routes are configured for the two network interfaces of the source ECS, both the primary and extended network interfaces can be used to communicate with the destination ECS.

.. important::

   You can select a destination IP address based on service requirements. Before configuring policy-based routes, ensure that the source ECS can use its primary network interface to communicate with the destination ECS.

.. _vpc_faq_0079__en-us_topic_0000001251530747_fig39726015294:

.. figure:: /_static/images/en-us_image_0000001818983470.png
   :alt: **Figure 1** Networking of an ECS with two network interfaces

   **Figure 1** Networking of an ECS with two network interfaces

Operation Guide
---------------

This document describes how to configure policy-based routes for Linux and Windows ECSs. For details, see :ref:`Table 1 <vpc_faq_0079__table1312113714428>`.

.. _vpc_faq_0079__table1312113714428:

.. table:: **Table 1** Operation instructions

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------+
   | OS Type               | IP Address Version    | Procedure                                                                                                |
   +=======================+=======================+==========================================================================================================+
   | Linux                 | -  IPv4               | Take an ECS running CentOS 8.0 (64-bit) as an example.                                                   |
   |                       | -  IPv6               |                                                                                                          |
   |                       |                       | :ref:`Configuring Policy-based Routes for a Linux ECS with Multiple Network Interfaces <vpc_nic_0016>`   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------+
   | Windows               | -  IPv4               | Take an ECS running Windows Server 2012 (64-bit) as an example.                                          |
   |                       | -  IPv6               |                                                                                                          |
   |                       |                       | :ref:`Configuring Policy-based Routes for a Windows ECS with Multiple Network Interfaces <vpc_nic_0017>` |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------+
