:original_name: vpc_vip_0010.html

.. _vpc_vip_0010:

Unbinding a Virtual IP Address from an Instance or EIP
======================================================

Scenarios
---------

For detailed operations, see:

-  :ref:`Unbinding a Virtual IP Address from an Instance <vpc_vip_0010__section11186205413818>`
-  :ref:`Unbinding a Virtual IP Address from an EIP <vpc_vip_0010__section3703996137>`

.. _vpc_vip_0010__section11186205413818:

Unbinding a Virtual IP Address from an Instance
-----------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Subnets**.

   The subnet list page is displayed.

#. Click the name of the subnet that the virtual IP address belongs to.

   The **Summary** page is displayed.

#. Click the **IP Addresses** tab.

   The virtual IP address list is displayed.


   .. figure:: /_static/images/en-us_image_0000001818982758.png
      :alt: **Figure 1** Virtual IP addresses

      **Figure 1** Virtual IP addresses

#. Locate the row that contains the virtual IP address, click **More** in the **Operation** column, and select **Unbind from Instance**.

   The **Bound To Instance** dialog box is displayed.

#. In the displayed dialog box, perform the following operations to unbind the virtual IP address from the instance:

   a. Select the type of the instance bound to the virtual IP address.

   b. Locate the row that contains the instance and click **Unbind** in the **Operation** column.

      A confirmation dialog box is displayed.

   c. Confirm the information and click **OK**.

.. _vpc_vip_0010__section3703996137:

Unbinding a Virtual IP Address from an EIP
------------------------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select the desired region and project.

#. In the upper left corner of the page, click |image4| to expand the service list and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Subnets**.

   The subnet list page is displayed.

#. In the subnet list, locate the target subnet and click its name.

   The subnet details page is displayed.

#. Click the **IP Addresses** tab.

   The virtual IP address list is displayed.


   .. figure:: /_static/images/en-us_image_0000002556160747.png
      :alt: **Figure 2** Virtual IP addresses

      **Figure 2** Virtual IP addresses

#. In the virtual IP address list, locate the target virtual IP address and click **Unbind from EIP** in the **Operation** column.

   A confirmation dialog box is displayed.

#. Confirm the information and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000002456862761.png
.. |image3| image:: /_static/images/en-us_image_0000002556040775.png
.. |image4| image:: /_static/images/en-us_image_0000002525120826.png
