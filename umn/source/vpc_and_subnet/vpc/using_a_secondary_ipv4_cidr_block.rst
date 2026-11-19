:original_name: vpc_vpc_0007.html

.. _vpc_vpc_0007:

Using a Secondary IPv4 CIDR Block
=================================

Scenarios
---------

Generally, the number of IP addresses in a VPC CIDR block determines how many cloud resources that can be deployed in the VPC. If there are no sufficient IP addresses in a VPC CIDR block, you can add a secondary IPv4 CIDR block to expand the VPC CIDR block and increase the number of IP addresses.

The IPv4 CIDR block you specify when you create a VPC is the primary one. The primary CIDR block cannot be changed after the VPC is created. If IP addresses in the primary CIDR block are insufficient, you can add secondary CIDR blocks to the VPC. A secondary CIDR block can be used in the same way as the primary CIDR block. A VPC supports up to five secondary CIDR blocks to a VPC.

.. note::

   If the :ref:`secondary IPv4 CIDR block <vpc_vpc_0007>` function is available in a region, the CIDR block of a VPC in this region cannot be modified through the console. You can call an API to modify VPC CIDR block by referring to `Updating VPC Information <https://docs.otc.t-systems.com/virtual-private-cloud/api-ref/apis/virtual_private_cloud/updating_vpc_information.html#vpc-api01-0004>`__.

Configuration Example
---------------------

As services develop, the IP addresses in VPC-A (primary CIDR block: 192.168.10.0/24) were insufficient. To solve this problem, you can add a secondary CIDR block (172.17.10.0/24) to this VPC and create two subnets (Subnet-A03 and Subnet-A04) in the secondary CIDR block to support future resource deployment and service expansion.


.. figure:: /_static/images/en-us_image_0000002556053279.png
   :alt: **Figure 1** Configuration example with a secondary IPv4 CIDR block

   **Figure 1** Configuration example with a secondary IPv4 CIDR block

Constraints
-----------

-  You can allocate a subnet from either a primary or a secondary CIDR block of a VPC. A subnet cannot use both the primary and the secondary CIDR blocks.

   Subnets in the same VPC can communicate with each other by default, even if some subnets are allocated from the primary CIDR block and some are from the secondary CIDR block of a VPC.

-  If a subnet in a secondary CIDR block of your VPC is the same as or overlaps with the destination of an existing route in the VPC route table, the existing route does not take effect.

   If you create a subnet in a secondary CIDR block of your VPC, a route (the destination is the subnet CIDR block and the next hop is **Local**) is automatically added to your VPC route table. This route allows communications within the VPC and has a higher priority than any other routes in the VPC route table. For example, if a VPC route table has a route with the VPC peering connection as the next hop and 100.20.0.0/24 as the destination, and a route for the subnet in the secondary CIDR block has a destination of 100.20.0.0/16, 100.20.0.0/16 and 100.20.0.0/24 overlaps and traffic will be forwarded through the route of the subnet.

-  :ref:`Table 1 <vpc_vpc_0007__table1060431941314>` lists the secondary CIDR blocks that are not supported.

   .. _vpc_vpc_0007__table1060431941314:

   .. table:: **Table 1** Restricted secondary CIDR blocks

      +-----------------------------------+-----------------------------------+
      | Type                              | CIDR Block (Not Supported)        |
      +===================================+===================================+
      | Reserved private CIDR blocks      | -  172.31.0.0/16                  |
      |                                   | -  192.168.0.0/16                 |
      |                                   | -  In-use primary CIDR blocks     |
      +-----------------------------------+-----------------------------------+
      | Reserved system CIDR blocks       | -  100.64.0.0/10                  |
      |                                   | -  214.0.0.0/7                    |
      |                                   | -  198.18.0.0/15                  |
      |                                   | -  169.254.0.0/16                 |
      +-----------------------------------+-----------------------------------+
      | Reserved public CIDR blocks       | -  0.0.0.0/8                      |
      |                                   | -  127.0.0.0/8                    |
      |                                   | -  240.0.0.0/4                    |
      |                                   | -  255.255.255.255/32             |
      +-----------------------------------+-----------------------------------+

Adding a Secondary IPv4 CIDR Block
----------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

#. In the VPC list, locate the target VPC and click **Edit CIDR Block** in the **Operation** column.

   The **Edit CIDR Block** dialog box is displayed.

#. Click **Add Secondary IPv4 CIDR Block**.

#. Enter a secondary IPv4 CIDR block in the text box and click **OK**.

   Do not specify a secondary CIDR block listed in :ref:`Table 1 <vpc_vpc_0007__table1060431941314>`.

Deleting a Secondary IPv4 CIDR Block
------------------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select the desired region and project.

#. In the upper left corner of the page, click |image4| to expand the service list and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

#. In the VPC list, locate the target VPC and click **Edit CIDR Block** in the **Operation** column.

   The **Edit CIDR Block** dialog box is displayed.

#. Locate the row that contains the secondary IPv4 CIDR block to be deleted and click **Delete** in the **Operation** column.

   -  **A secondary IPv4 CIDR block of a VPC can be deleted, but the primary CIDR block cannot be deleted.**
   -  **If you want to delete a secondary CIDR block that contains subnets, you need to delete the subnets first.**

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818983054.png
.. |image2| image:: /_static/images/en-us_image_0000001865663001.png
.. |image3| image:: /_static/images/en-us_image_0000002556173247.png
.. |image4| image:: /_static/images/en-us_image_0000002556053281.png
