:original_name: vpc_nic_0007.html

.. _vpc_nic_0007:

Viewing Basic Information About a Network Interface
===================================================

Scenarios
---------

You can view basic information about your network interfaces on the console, including the name, ID, type, attached instance, flow logs, creation time, VPCs, subnets, IP addresses (private IP addresses, EIPs, and virtual IP addresses), and associated security groups.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Network Interfaces**.

#. On the **Network Interfaces** page, click the name of the target network interface.


   .. figure:: /_static/images/en-us_image_0000002172413782.png
      :alt: **Figure 1** Viewing the basic information about a network interface

      **Figure 1** Viewing the basic information about a network interface

Other Operations
----------------

On the network interface details page, you can also modify the following information:

-  You can edit the network interface name, bind or unbind an EIP to or from the network interface, and attach the network interface to or detach it from an instance.
-  Instance-dependent Deletion

   -  **Instance-dependent Deletion** is disabled by default. The network interface will not be deleted if it is detached from the instance or if the instance is deleted. You can attach the network interface to another instance.
   -  If **Instance-dependent Deletion** has been enabled, the network interface will be deleted after it is detached from the instance.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865583085.png
