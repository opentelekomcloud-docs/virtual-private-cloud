:original_name: vpc_vpc02_0006.html

.. _vpc_vpc02_0006:

Deleting a Subnet
=================

Scenarios
---------

You can delete a subnet to release network resources if the subnet is no longer required.

Prerequisites
-------------

You can delete a subnet only if there are no resources in the subnet. If there are resources in the subnet, you must delete those resources before you can delete the subnet.

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

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. On the console homepage, under **Network**, click **Virtual Private Cloud**.
#. In the navigation pane on the left, click **Virtual Private Cloud**.
#. On the **Virtual Private Cloud** page, locate the VPC from which a subnet is to be deleted and click the VPC name.
#. On the **Subnets** page, locate the target subnet and click **Delete**.
#. Click **Yes** in the displayed dialog box.

.. |image1| image:: /_static/images/en-us_image_0226223279.png
