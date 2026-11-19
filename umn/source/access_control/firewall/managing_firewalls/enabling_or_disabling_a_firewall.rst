:original_name: vpc_acl_0011.html

.. _vpc_acl_0011:

Enabling or Disabling a Firewall
================================

Scenarios
---------

After a firewall is created, you can enable or disable it based on network requirements. Before enabling a firewall, ensure that subnets have been associated with the firewall and that inbound and outbound rules have been added to the firewall.

When a firewall is disabled, custom rules will become invalid while default rules still take effect. Disabling a firewall may interrupt network traffic. For details about the default rules of a firewall, see :ref:`Firewall Rules <acl_0001__section31493412299>`.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

5. In the firewall list, enable or disable the target firewall.

   -  Enabling a Firewall

      a. Locate the target firewall and choose **More** > **Enable** in the **Operation** column.

         A confirmation dialog box is displayed.

      b. Confirm the information and click **OK**.

   -  Disabling a Firewall

      a. Locate the target firewall and choose **More** > **Disable** in the **Operation** column.

         A confirmation dialog box is displayed.

      b. Confirm the information and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823714.png
