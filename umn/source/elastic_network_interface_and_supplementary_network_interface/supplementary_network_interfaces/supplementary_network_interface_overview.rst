:original_name: vpc_subeni_0002.html

.. _vpc_subeni_0002:

Supplementary Network Interface Overview
========================================

Supplementary network interfaces are a supplement to elastic network interfaces. If the number of elastic network interfaces that can be attached to your ECS cannot meet your requirements, you can use supplementary network interfaces, which can be attached to VLAN subinterfaces of elastic network interfaces.

Application Scenarios
---------------------

Supplementary network interfaces are attached to VLAN subinterfaces of elastic network interfaces. :ref:`Figure 1 <vpc_subeni_0002__fig11599171211328>` shows the networking diagram.

.. _vpc_subeni_0002__fig11599171211328:

.. figure:: /_static/images/en-us_image_0000001865582849.png
   :alt: **Figure 1** Supplementary network interface networking diagram

   **Figure 1** Supplementary network interface networking diagram

The number of network interfaces that can be attached to an ECS depends on the ECS specifications. For details, see `ECS Specifications <https://docs.otc.t-systems.com/elastic-cloud-server/umn/service_overview/ecs_types_and_specifications/ecs_specifications/a_summary_list_of_ecs_specifications.html>`__. If you need more network interfaces, you can attach supplementary network interfaces to the network interface.

-  You can attach supplementary network interfaces that belong to different subnets in the same VPC to an ECS. Each supplementary network interface has its private IP address and EIP for private or Internet communication.
-  You can configure security group rules for supplementary network interfaces for network isolation.

Notes and Constraints
---------------------

-  A maximum of 256 supplementary network interfaces can be attached to an ECS of certain flavors. The number of supplementary network interfaces that can be attached to an ECS varies by ECS flavor.

   ECS: C7n, M7n, and S7n series.

-  An ECS cannot use Cloud-Init through the private IP addresses of its supplementary network interfaces.

-  A supplementary network interface cannot have a virtual IP address bound.

-  The flow logs of supplementary network interfaces cannot be collected separately. Their flow logs are generated together with their network interfaces.
