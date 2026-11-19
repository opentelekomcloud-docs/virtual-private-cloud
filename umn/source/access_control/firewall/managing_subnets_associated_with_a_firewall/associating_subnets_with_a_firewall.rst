:original_name: en-us_topic_0051746700.html

.. _en-us_topic_0051746700:

Associating Subnets with a Firewall
===================================

Scenarios
---------

You can associate a firewall with a subnet to protect resources in the subnet.

Notes and Constraints
---------------------

-  You can associate a firewall with multiple subnets. However, a subnet can only be associated with one firewall at a time.
-  After a firewall is associated with a subnet, the default firewall rules deny all traffic to and from the subnet until you add custom rules to allow traffic. For details, see :ref:`Adding a Firewall Rule <en-us_topic_0051746702>`.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. Associate a subnet with a firewall using either of the following methods:

   -  Method 1

      a. In the navigation pane on the left, click **Subnets**.

         The **Subnets** page is displayed.

      b. In the subnet list, locate the row that contains the subnet and click **Associate** under the **Firewall** column.

         The **Associate Firewall** page is displayed.

      c. Select a firewall from the drop-down list.

         If there is no firewall, click |image3| in the drop-down list to create one.

      d. Click **OK**.

         The subnet list is displayed. You can view the associated firewall of the subnet.

   -  Method 2

      a. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

         The firewall list is displayed.

      b. In the subnet list, locate the row that contains the firewall and click **Associate Subnet** in the **Operation** column.

         The **Associated Subnets** tab is displayed.

      c. On the **Associated Subnets** tab, click **Associate**.

         The **Associate Subnet** dialog box is displayed.

      d. In the **Associate Subnet** dialog box, select the subnet from the subnet list and click **OK**.

         In the associated subnet list, you can view all subnets associated with the firewall.

         .. note::

            A subnet with a firewall associated will not be displayed in the subnet list of the **Associate Subnet** dialog box for you to select. If you want to associate such a subnet with another firewall, you must first disassociate the subnet from the original firewall.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865663185.png
.. |image3| image:: /_static/images/en-us_image_0000001865582985.png
