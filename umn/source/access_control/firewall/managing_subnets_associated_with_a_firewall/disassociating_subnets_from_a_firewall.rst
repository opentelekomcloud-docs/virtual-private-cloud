:original_name: vpc_acl_0003.html

.. _vpc_acl_0003:

Disassociating Subnets from a Firewall
======================================

Scenarios
---------

You can disassociate a subnet from its firewall based on your network requirements.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. Disassociate a subnet with a Network using either of the following methods:

   -  Method 1

      a. In the navigation pane on the left, click **Subnets**.

         The **Subnets** page is displayed.

      b. In the subnet list, click the subnet name with a hyperlink.

         The subnet details page is displayed.

      c. In the upper right corner of the subnet details page, click **Disassociate** next to the firewall.

         A confirmation dialog box is displayed.

      d. Confirm the information and click **OK**.

         On the subnet details page, you can see that no firewall is associated with the subnet.

   -  Method 2

      a. In the navigation pane on the left, click **Subnets**.

         The **Subnets** page is displayed.

      b. In the subnet list, locate the row that contains the subnet and click hyperlink under the **Firewall** column.

         The firewall details page is displayed.

      c. Click the **Associated Subnets** tab, select one or more subnets, and click **Disassociate**.

         A confirmation dialog box is displayed.

      d. Click **Yes** in the displayed dialog box.

         On the **Associated Subnets** tab, you can see that the disassociated subnets are not displayed in the subnet list.

   -  Method 3

      a. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

         The firewall list is displayed.

      b. Locate the row that contains the firewall and click **Associate Subnet** in the **Operation** column.

         The **Associated Subnets** tab is displayed.

      c. Select one or more subnets and click **Disassociate**.

         A confirmation dialog box is displayed.

      d. Click **OK**.

         On the **Associated Subnets** tab, you can see that the disassociated subnets are not displayed in the subnet list.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818822966.png
