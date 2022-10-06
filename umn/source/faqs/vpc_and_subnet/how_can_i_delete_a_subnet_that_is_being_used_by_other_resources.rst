:original_name: vpc_faq_0075.html

.. _vpc_faq_0075:

How Can I Delete a Subnet That Is Being Used by Other Resources?
================================================================

The VPC service allows you to create private, isolated virtual networks. In a VPC, you can manage private IP address ranges, subnets, route tables, and gateways. ECSs, BMSs, databases, and some applications can use subnets created in VPCs.

A subnet cannot be deleted if it is being used by other resources. You must delete all resources in the subnet before you can delete the subnet.

You can view all resources of your account on the console homepage and check the resources that are in the subnet you want to delete.

The resources may include:

-  ECS
-  BMS
-  CCE cluster
-  RDS instance
-  MRS cluster
-  DCS instance
-  Load balancer
-  VPN
-  Private IP address
-  Custom route
-  NAT gateway
