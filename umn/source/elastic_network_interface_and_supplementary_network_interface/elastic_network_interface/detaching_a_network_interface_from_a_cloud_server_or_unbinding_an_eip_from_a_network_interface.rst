:original_name: vpc_nic_0005.html

.. _vpc_nic_0005:

Detaching a Network Interface from a Cloud Server or Unbinding an EIP from a Network Interface
==============================================================================================

Scenarios
---------

This section describes how to detach a network interface from an instance or unbind a network interface from an EIP.

Notes and Constraints
---------------------

-  If **Instance-dependent Deletion** is enabled for a network interface, the network interface will be deleted if it is detached from its instance.

   -  Deleting a network interface will also delete any supplementary network interfaces and VLAN sub-interfaces attached to it.
   -  Deleting a network interface will also unbind its EIP.

-  If **Instance-dependent Deletion** is disabled for a network interface, the network interface will not be deleted if it is detached from its instance.

   If a network interface has an EIP bound, detaching the network interface from its instance will also unbind the EIP from the network interface.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Network Interfaces**.

#. In the network interface list, locate the row that contains the target network interface, and click **Detach Instance** or **Unbind EIP** in the **Operation** column.

#. Click **OK**.

   If you no longer need an EIP, you can release the EIP after unbinding it.


   .. figure:: /_static/images/en-us_image_0000002206728865.png
      :alt: **Figure 1** Detaching a network interface from a cloud server

      **Figure 1** Detaching a network interface from a cloud server


   .. figure:: /_static/images/en-us_image_0000002206574453.png
      :alt: **Figure 2** Unbinding an EIP from a network interface

      **Figure 2** Unbinding an EIP from a network interface

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823542.png
