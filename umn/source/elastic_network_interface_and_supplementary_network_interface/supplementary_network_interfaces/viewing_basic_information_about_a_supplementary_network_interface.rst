:original_name: vpc_subeni_0007.html

.. _vpc_subeni_0007:

Viewing Basic Information About a Supplementary Network Interface
=================================================================

Scenarios
---------

You can view basic information about your supplementary network interface on the management console, including its ID, network interface, VLAN ID, creation time, description, VPC, subnet, private IP address, EIP, MAC address, and security groups.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Network Interfaces**.

#. On the **Network Interfaces** page, click **Supplementary Network Interfaces** tab.

#. Click the private IP address of the supplementary network interface whose details you want to view.

   -  On the **Summary** tab, you can view its ID, network interface, VLAN ID, creation time, description, VPC, subnet, private IP address, EIP, and MAC address.
   -  On the **Associated Security Groups** tab, you can view its associated security groups and their rules.


   .. figure:: /_static/images/en-us_image_0000002171069826.png
      :alt: **Figure 1** Viewing the basic information about a supplementary network interface

      **Figure 1** Viewing the basic information about a supplementary network interface

Other Operations
----------------

On the supplementary network interface details page, you can also modify the following information:

-  On the **Summary** tab, you can modify the description of the interface and change its bound EIP.
-  On the **Associated Security Groups** tab, you can change the associated security groups of the interface. For details, see :ref:`Changing Security Groups That Are Associated with a Supplementary Network Interface <vpc_subeni_0005>`.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818983266.png
