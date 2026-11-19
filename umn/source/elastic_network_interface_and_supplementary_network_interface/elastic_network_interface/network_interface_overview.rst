:original_name: vpc_nic_0001.html

.. _vpc_nic_0001:

Network Interface Overview
==========================

An elastic network interface (referred to as a network interface in this documentation) is a virtual network card. You can create and configure network interfaces and attach them to your instances (ECSs and BMSs) to obtain flexible and highly available network configurations.

Network Interface Types
-----------------------

-  A primary network interface is created together with an instance by default, and cannot be detached from the instance.
-  An extended network interface is created on the **Network Interfaces** console, and can be attached to or detached from an instance.

Application Scenarios
---------------------

-  Flexible migration

   You can detach a network interface from an instance and then attach it to another instance. The network interface retains its private IP address, EIP, and security group rules. In this way, service traffic on the faulty instance can be quickly migrated to the standby instance, implementing quick service recovery.

-  Traffic management

   You can attach multiple network interfaces that belong to different subnets in a VPC to the same instance, and configure the network interfaces to carry the private network traffic, public network traffic, and management network traffic of the instance. You can configure access control policies and routing policies for each subnet, and configure security group rules for each network interface to isolate networks and service traffic.

Notes and Constraints
---------------------

The number of extended network interfaces that can be attached to an ECS is determined by the ECS specifications. For details, see `ECS Specifications <https://docs.otc.t-systems.com/elastic-cloud-server/umn/service_overview/ecs_types_and_specifications/ecs_specifications/a_summary_list_of_ecs_specifications.html>`__.
