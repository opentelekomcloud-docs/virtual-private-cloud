:original_name: vpc_vpc_0003.html

.. _vpc_vpc_0003:

Deleting a VPC
==============

Scenarios
---------

You can delete a VPC if the VPC is no longer required.

You can delete a VPC only if there are no resources in the VPC. If there are resources in the VPC, you must delete those resources before you can delete the VPC.

A VPC cannot be deleted if it contains subnets, Direct Connect connections, custom routes, VPC peering connections, or VPNs. To delete the VPC, you must first delete or disable the following resources.

-  Subnets. For details, see section :ref:`Deleting a Subnet <vpc_vpc_0002>`.
-  VPNs. For details, see *Virtual Private Network User Guide*.
-  Direct Connect connections. For details, see the *Direct Connect User Guide*.
-  Custom routes. For details, see section :ref:`Deleting a Route <vpc_route_0012>`.
-  VPC peering connections. For details, see section :ref:`Deleting a VPC Peering Connection <vpc_peering_0003>`.

Notes and Constraints
---------------------

If there are any EIPs or security groups, the last VPC cannot be deleted.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.
3. On the console homepage, under **Network**, click **Virtual Private Cloud**.
4. In the navigation pane on the left, click **Virtual Private Cloud**.
5. On the **Virtual Private Cloud** page, locate the row that contains the VPC to be deleted and click **Delete** in the **Operation** column.
6. Click **Yes** in the displayed dialog box.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
