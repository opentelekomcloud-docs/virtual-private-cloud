:original_name: vpc_nic_0014.html

.. _vpc_nic_0014:

Overview
========

Background
----------

If a cloud server has multiple network interfaces, the primary network interface can communicate with external networks by default, but the extended network interfaces cannot. To enable extended network interfaces to communicate with external networks, you need to configure policy-based routes for these network interfaces.

Scenarios
---------

This example describes how to configure policy-based routes for an ECS with two network interfaces. :ref:`Figure 1 <vpc_nic_0014__en-us_topic_0000001251530747_fig39726015294>` shows the networking.

-  The primary and extended network interfaces on the source ECS are in different subnets of the same VPC.
-  The source and destination ECSs are in different subnets of the same VPC and the two ECSs can communicate with each other through primary network interfaces without configuring policy-based routes.
-  After policy-based routes are configured for the two network interfaces of the source ECS, both the primary and extended network interfaces can be used to communicate with the destination ECS.

.. important::

   You can select a destination IP address based on service requirements. Before configuring policy-based routes, ensure that the source ECS can use its primary network interface to communicate with the destination ECS.

.. _vpc_nic_0014__en-us_topic_0000001251530747_fig39726015294:

.. figure:: /_static/images/en-us_image_0000002207352857.png
   :alt: **Figure 1** Networking of an ECS with two network interfaces

   **Figure 1** Networking of an ECS with two network interfaces
