:original_name: en-us_topic_0013748729.html

.. _en-us_topic_0013748729:

What Is Virtual Private Cloud?
==============================

Overview
--------

The Virtual Private Cloud (VPC) service enables you to provision logically isolated, configurable, and manageable virtual networks for Elastic Cloud Servers (ECSs), improving cloud resource security and simplifying network deployment.

Within your own VPC, you can create security groups and VPNs, configure IP address ranges, specify bandwidth sizes, manage the networks in the VPC, and make changes to these networks as needed, quickly and securely. You can also define rules for communication between ECSs in the same security group or in different security groups.


.. figure:: /_static/images/en-us_image_0209606948.png
   :alt: **Figure 1** VPC components

   **Figure 1** VPC components

Advantages
----------

-  Flexible configuration

   You can create VPCs, add subnets, specify IP address ranges, and configure route tables. You can configure the same VPC for ECSs that are in different availability zones (AZs).

-  Secure and reliable

   Each VPC is completely logically isolated from other VPCs using the tunneling technology. By default, different VPCs cannot communicate with each other. You can use firewalls to protect subnets and use security groups to protect instances, such as cloud servers, containers, and databases. The firewalls and security groups add additional layers of security to your VPCs, making your network secure.

-  Interconnectivity

   By default, instances in a VPC cannot access the Internet. You can leverage Elastic IP (EIP), Elastic Load Balancing (ELB), NAT Gateways, Virtual Private Network (VPN), and Direct Connect to enable access to or from the Internet.

   By default, instances in two VPCs cannot communicate with each other. You can create a VPC peering connection to enable the instances in the two VPCs in the same region to communicate with each other using private IP addresses.

   Multiple connectivity options are provided to meet diverse service requirements for the cloud, enabling you to deploy enterprise applications with ease and lower enterprise IT operation and maintenance (O&M) costs.

-  High-speed access

   Dynamic Border Gateway Protocol (BGP) is used to provide access to various carrier networks. For example, up to 21 dynamic BGP connections are established to multiple carriers. The dynamic BGP connections enable real-time failover based on preset routing protocols, ensuring high network stability, low network latency, and smooth access to services on the cloud.

Accessing the VPC Service
-------------------------

You can access the VPC service through the management console or using HTTPS-based APIs.

-  Management console

   You can use the console to directly perform operations on VPC resources. To access the VPC service, log in to the management console and select **Virtual Private Cloud** from the console homepage.

-  API

   If you need to integrate the VPC service provided by the cloud system into a third-party system for secondary development, you can use APIs to access the VPC service. For details, see the *Virtual Private Cloud API Reference*.
