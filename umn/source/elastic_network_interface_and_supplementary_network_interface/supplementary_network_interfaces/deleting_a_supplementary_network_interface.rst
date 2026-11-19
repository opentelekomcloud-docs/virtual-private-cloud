:original_name: vpc_subeni_0006.html

.. _vpc_subeni_0006:

Deleting a Supplementary Network Interface
==========================================

Scenarios
---------

If you want to delete a supplementary network interface with an EIP bound, you have to first unbind the EIP from the interface.

Notes and Constraints
---------------------

-  Deleting a supplementary network interface will also detach it from its network interface.

-  Deleting a supplementary network interface will also unbind its EIP. You can choose to release the EIP if needed.

-  If a supplementary network interface has resources associated, deleting the interface will also delete any rules for associated resources that reference it.

   For example, if the next hop of a custom route in a VPC route table is a supplementary network interface, deleting the interface will also delete the route.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Network Interfaces**.

#. On the **Network Interfaces** page, click **Supplementary Network Interfaces** tab.

#. Locate the row that contains the supplementary network interface and click **Delete** in the **Operation** column.

   A confirmation dialog box is displayed.

#. Confirm the information and click **OK**.

   Deleting a supplementary network interface will also delete the VLAN sub-interfaces configured on the ECS.


   .. figure:: /_static/images/en-us_image_0000002206681137.png
      :alt: **Figure 1** Deleting a supplementary network interface

      **Figure 1** Deleting a supplementary network interface

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865583281.png
