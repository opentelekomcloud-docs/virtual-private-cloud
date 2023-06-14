:original_name: en-us_topic_0051746698.html

.. _en-us_topic_0051746698:

Creating a Firewall
===================

Scenarios
---------

You can create a custom firewall. By default, a newly created firewall is disabled and has no inbound or outbound rules, or any subnets associated. Each user can create up to 200 firewalls by default.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

5. In the right pane displayed, click **Create Firewall**.

6. On the **Create Firewall** page, configure parameters as prompted.


   .. figure:: /_static/images/en-us_image_0129304042.png
      :alt: **Figure 1** Create Firewall

      **Figure 1** Create Firewall

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
.. |image2| image:: /_static/images/en-us_image_0000001500905066.png
