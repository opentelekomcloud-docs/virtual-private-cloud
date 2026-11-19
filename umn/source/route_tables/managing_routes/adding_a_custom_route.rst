:original_name: vpc_route01_0006.html

.. _vpc_route01_0006:

Adding a Custom Route
=====================

Scenarios
---------

Each route table comes with a default route to allow instances in a subnet to access public services on the cloud or to allow different subnets in a VPC to communicate with each other. You can also add custom routes as required to control traffic routing.

If a route table is associated with a subnet, adding rules to the route table may affect how and where traffic is directed. Be careful with this operation as it may interrupt services.

Constraints
-----------

-  A maximum of 200 routes can be added to each route table.

-  Generally, the destination of a custom route cannot overlap with that of a local route. The destination of a local route can be a subnet CIDR block or CIDR blocks that are used for internal communications.

   For example, if VPC-A has a subnet that supports IPv4/IPv6 dual stack. Its IPv4 CIDR block is 192.168.2.0/24 and IPv6 CIDR block is 2407:c080:802:be7::/64. The system automatically adds the local routes in :ref:`Table 1 <vpc_route01_0006__en-us_topic_0214585021_table656811322585>` to the route table of VPC-A. In this case, the destinations of the custom routes you set cannot overlap with those of the existing local routes.

   .. _vpc_route01_0006__en-us_topic_0214585021_table656811322585:

   .. table:: **Table 1** VPC-A local routes

      +-------------------------+-----------------------------------------------------------+
      | Local Route Destination | Destination Description                                   |
      +=========================+===========================================================+
      | 192.168.2.0/24          | IPv4 CIDR block of the subnet                             |
      +-------------------------+-----------------------------------------------------------+
      | 2407:c080:802:be7::/64  | IPv6 CIDR block of the subnet                             |
      +-------------------------+-----------------------------------------------------------+
      | 100.64.0.0/10           | Network used by public services on the cloud, such as DNS |
      +-------------------------+-----------------------------------------------------------+
      | 198.19.128.0/20         | Network used by internal services, such as VPC Endpoint   |
      +-------------------------+-----------------------------------------------------------+
      | 127.0.0.0/8             | Loopback address                                          |
      +-------------------------+-----------------------------------------------------------+

-  You cannot add two routes with the same destination to a VPC route table even if their next hop types are different.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

4. In the navigation pane on the left, choose **Virtual Private Cloud** > **Route Tables**.

5. In the route table list, click the name of the route table that you want to add a route to.

6. Click **Add Route** and set parameters as prompted.

   You can click **+** to add more routes.


   .. figure:: /_static/images/en-us_image_0000002065093369.png
      :alt: **Figure 1** Add Route

      **Figure 1** Add Route

   .. table:: **Table 2** Parameter descriptions

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Parameter             | Description                                                                                                                                                          | Example Value          |
      +=======================+======================================================================================================================================================================+========================+
      | Destination Type      | Mandatory                                                                                                                                                            | IP address             |
      |                       |                                                                                                                                                                      |                        |
      |                       | The destination can be:                                                                                                                                              |                        |
      |                       |                                                                                                                                                                      |                        |
      |                       | IP address: single IP address or IP address range                                                                                                                    |                        |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Destination           | Mandatory                                                                                                                                                            | IPv4: 192.168.0.0/16   |
      |                       |                                                                                                                                                                      |                        |
      |                       | Enter the destination of the route. You can enter a single IP address or an IP address range in CIDR notation.                                                       |                        |
      |                       |                                                                                                                                                                      |                        |
      |                       | The destination of the default route is 0.0.0.0/0, which indicates any traffic.                                                                                      |                        |
      |                       |                                                                                                                                                                      |                        |
      |                       | The destination of each route in a route table must be unique. The destination cannot overlap with any subnet in the VPC.                                            |                        |
      |                       |                                                                                                                                                                      |                        |
      |                       | .. note::                                                                                                                                                            |                        |
      |                       |                                                                                                                                                                      |                        |
      |                       |    If there is an IP address range in the format of *Start IP address-End IP address*, it is not supported.                                                          |                        |
      |                       |                                                                                                                                                                      |                        |
      |                       |    For example, you need to change 192.168.0.1-192.168.0.62 to 192.168.0.0/26.                                                                                       |                        |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Next Hop Type         | Mandatory                                                                                                                                                            | VPC peering connection |
      |                       |                                                                                                                                                                      |                        |
      |                       | Set the type of the next hop.                                                                                                                                        |                        |
      |                       |                                                                                                                                                                      |                        |
      |                       | .. note::                                                                                                                                                            |                        |
      |                       |                                                                                                                                                                      |                        |
      |                       |    When you add or modify a custom route in a default route table, the next hop type of the route cannot be set to **VPN connection** or **Direct Connect gateway**. |                        |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Next Hop              | Mandatory                                                                                                                                                            | peer-AB                |
      |                       |                                                                                                                                                                      |                        |
      |                       | Set the next hop. The resources in the drop-down list box are displayed based on the selected next hop type.                                                         |                        |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
      | Description           | Optional                                                                                                                                                             | ``-``                  |
      |                       |                                                                                                                                                                      |                        |
      |                       | Enter the description of the route in the text box as required.                                                                                                      |                        |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+

7. Click **OK**.

   You can view the new route in the route list.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865662989.png
