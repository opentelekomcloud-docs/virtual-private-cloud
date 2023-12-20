:original_name: vpc_vip_0010.html

.. _vpc_vip_0010:

Unbinding a Virtual IP Address from an Instance
===============================================

Scenarios
---------

This section describes how to unbind a virtual IP address from an ECS.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Subnets**.

   The **Subnets** page is displayed.

#. Click the name of the subnet that the virtual IP address belongs to.

   The **Summary** page is displayed.

#. Click the **IP Addresses** tab.

   The virtual IP address list is displayed.


   .. figure:: /_static/images/en-us_image_0000001570070841.png
      :alt: **Figure 1** Virtual IP addresses

      **Figure 1** Virtual IP addresses

#. Locate the row that contains the virtual IP address, click **More** in the **Operation** column, and select **Unbind from Server**.

   The **Bound Server** dialog box is displayed.

#. Unbind the virtual IP address from the instance.

   a. Select the type of the instance bound to the virtual IP address.

   b. Locate the row that contains the instance and click **Unbind** in the **Operation** column.

      A confirmation dialog box is displayed.

   c. Confirm the information and click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001675618277.png
