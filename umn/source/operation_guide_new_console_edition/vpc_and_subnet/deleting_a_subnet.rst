:original_name: vpc_vpc_0002.html

.. _vpc_vpc_0002:

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

2. Click |image1| in the upper left corner and select the desired region and project.

3. On the console homepage, under **Network**, click **Virtual Private Cloud**.

4. In the navigation pane on the left, click **Virtual Private Cloud**.

5. In the subnet list, locate the row that contains the subnet you want to delete and click **Delete** in the **Operation** column.

   A confirmation dialog box is displayed.

6. Click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
