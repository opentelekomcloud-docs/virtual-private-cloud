:original_name: en-us_topic_0051746700.html

.. _en-us_topic_0051746700:

Associating Subnets with a Firewall
===================================

Scenarios
---------

On the page showing firewall details, associate desired subnets with a firewall. After a firewall is associated with a subnet, the firewall denies all traffic to and from the subnet until you add rules to allow traffic.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.
3. On the console homepage, under **Network**, click **Virtual Private Cloud**.
4. In the navigation pane on the left, choose **Access Control** > **firewalls**.
5. Locate the target firewall and click its name to switch to the page showing details of that particular firewall.
6. On the displayed page, click the **Associated Subnets** tab.
7. On the **Associated Subnets** page, click **Associate**.
8. On the displayed page, select the subnets to be associated with the firewall, and click **OK**.

.. note::

   Subnets that have already been associated with firewalls will not be displayed on the page for you to select. One-click subnet association and disassociation are not currently supported. Furthermore, a subnet can only be associated with one firewall. If you want to reassociate a subnet that has already been associated with another firewall, you must first disassociate the subnet from the original firewall.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
