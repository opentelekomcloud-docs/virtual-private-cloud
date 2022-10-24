:original_name: en-us_topic_0051746698.html

.. _en-us_topic_0051746698:

Creating a Firewall
===================

Scenarios
---------

You can create a custom firewall, but any newly created firewall will be disabled by default. It will not have any inbound or outbound rules, or have any subnets associated. Each user can create up to 200 firewalls by default.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. On the console homepage, under **Network**, click **Virtual Private Cloud**.

4. In the navigation pane on the left, choose **Access Control** > **firewalls**.

5. In the right pane displayed, click **Create firewall**.

6. In the displayed dialog box, enter firewall information as prompted. :ref:`Table 1 <en-us_topic_0051746698__en-us_topic_0118499011_table145313414319>` lists the parameters to be configured.


   .. figure:: /_static/images/en-us_image_0129304042.png
      :alt: **Figure 1** Create Firewall

      **Figure 1** Create Firewall

   .. _en-us_topic_0051746698__en-us_topic_0118499011_table145313414319:

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                           | Example Value         |
      +=======================+=======================================================================================================================================================+=======================+
      | Name                  | The firewall name. This parameter is mandatory.                                                                                                       | fw-92d3               |
      |                       |                                                                                                                                                       |                       |
      |                       | The name contains a maximum of 64 characters, which may consist of letters, digits, underscores (_), and hyphens (-). The name cannot contain spaces. |                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the firewall. This parameter is optional.                                                                             | N/A                   |
      |                       |                                                                                                                                                       |                       |
      |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                   |                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
