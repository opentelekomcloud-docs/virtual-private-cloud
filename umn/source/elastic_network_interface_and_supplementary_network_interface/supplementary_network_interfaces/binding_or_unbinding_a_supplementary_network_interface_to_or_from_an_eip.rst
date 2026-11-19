:original_name: vpc_subeni_0004.html

.. _vpc_subeni_0004:

Binding or Unbinding a Supplementary Network Interface to or from an EIP
========================================================================

Scenarios
---------

You can bind a supplementary network interface to an EIP.

A supplementary network interface has a private IP address. You can also bind an EIP to the interface. The binding between a supplementary network interface and an EIP does not change when the network interface of the supplementary network interface is detached from an ECS and then attached to another ECS. The supplementary network interface still has its private IP address and EIP.

A network interface can have multiple supplementary network interfaces attached. If each supplementary network interface has an EIP, the ECS with the network interface attached can have multiple EIPs for flexible Internet access.

If you do not need an EIP or want to delete a supplementary network interface, you can unbind the EIP from the interface.

Binding a Supplementary Network Interface to an EIP
---------------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Network Interfaces**.

#. On the **Network Interfaces** page, click **Supplementary Network Interfaces** tab.

#. Locate the row that contains the supplementary network interface, click **Bind EIP** in the **Operation** column, and select the EIP to be bound.

#. Click **OK**.


   .. figure:: /_static/images/en-us_image_0000002206688401.png
      :alt: **Figure 1** Binding an EIP to a supplementary network interface

      **Figure 1** Binding an EIP to a supplementary network interface

Unbinding a Supplementary Network Interface from an EIP
-------------------------------------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select the desired region and project.

#. Click |image4| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Network Interfaces**.

#. On the **Network Interfaces** page, click **Supplementary Network Interfaces** tab.

#. Locate the row that contains the supplementary network interface and click **Unbind EIP** in the **Operation** column.

#. Click **OK**.


   .. figure:: /_static/images/en-us_image_0000002206537137.png
      :alt: **Figure 2** Unbinding an EIP from a supplementary network interface

      **Figure 2** Unbinding an EIP from a supplementary network interface

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865663501.png
.. |image3| image:: /_static/images/en-us_image_0000001818982734.png
.. |image4| image:: /_static/images/en-us_image_0000001818823774.png
