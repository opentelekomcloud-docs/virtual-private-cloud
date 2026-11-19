:original_name: vpc_nic_0010.html

.. _vpc_nic_0010:

Deleting a Network Interface
============================

Scenarios
---------

This section describes how to delete a network interface.

Notes and Constraints
---------------------

-  A primary network interface is created together with an instance by default, and cannot be detached from the instance. If you want to delete a primary network interface, you need to delete its instance first, which will also delete the primary network interface.

-  If you want to delete an extended network interface that is attached to an instance, :ref:`detach the interface from the instance <vpc_nic_0005>` first.

-  Deleting a network interface will also delete its supplementary network interfaces.

-  Deleting a network interface will also unbind its EIP. You can choose to release the EIP if needed.

-  If a network interface has resources associated, deleting the interface will also delete any rules for associated resources that reference it.

   For example, if the next hop of a custom route in a VPC route table is an extended network interface, deleting the network interface will also delete the route.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Network Interfaces**.

#. Locate the row that contains the network interface, click **More** in the **Operation** column, and click **Delete**.

   A confirmation dialog box is displayed.

#. Confirm the information and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002206730977.png
      :alt: **Figure 1** Deleting a network interface

      **Figure 1** Deleting a network interface

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818983258.png
