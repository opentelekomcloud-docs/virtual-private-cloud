:original_name: vpc_nic_0008.html

.. _vpc_nic_0008:

Binding a Network Interface to a Virtual IP Address
===================================================

Scenarios
---------

You can bind a network interface to a virtual IP address so that you can access the instance attached to the network interface using the virtual IP address.

Only a network interface with an instance attached can be bound to a virtual IP address.

For more information about virtual IP addresses, see :ref:`Virtual IP Address Overview <vpc_vip_0001>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Network Interfaces**.

#. In the network interface list, locate the row that contains the target network interface, and choose **More** > **Bind Virtual IP Address** in the **Operation** column.

   The **IP Addresses** page will be displayed.

#. Locate the row that contains the target virtual IP address and click **Bind to Server** in the **Operation** column.

#. Select the server and network interface, and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002206027889.png
      :alt: **Figure 1** Binding a virtual IP address to a cloud server's network interface

      **Figure 1** Binding a virtual IP address to a cloud server's network interface

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865583189.png
