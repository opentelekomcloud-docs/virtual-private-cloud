:original_name: vpc_faq_0006.html

.. _vpc_faq_0006:

What Subnet CIDR Blocks Are Available?
======================================

A subnet is a unique CIDR block with a range of IP addresses in a VPC. You can divide a VPC into several subnets to help you plan IP addresses. All cloud resources in a VPC must be deployed on subnets.

A subnet CIDR block must be within its VPC CIDR block. Each subnet CIDR block in a VPC must be unique. A subnet mask can be between the netmask of its VPC CIDR block and /29 netmask. If a VPC CIDR block is 10.0.0.0/16, its subnet mask can be between 16 and 29.

For example, if the CIDR block of a VPC is 10.0.0.0/16, you can specify 10.0.0.0/24 for a subnet in this VPC, 10.0.1.0/24 for the second subnet, and 10.0.2.0/24 for the third subnet.
