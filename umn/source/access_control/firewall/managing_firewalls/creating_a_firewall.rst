:original_name: en-us_topic_0051746698.html

.. _en-us_topic_0051746698:

Creating a Firewall
===================

Scenarios
---------

You can create a custom firewall. By default, a newly created firewall is disabled and has no inbound or outbound rules, or any subnets associated.

By default, you can create a maximum of 200 firewalls in a region.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

5. In the right pane displayed, click **Create Firewall**.

6. On the **Create Firewall** page, configure parameters as prompted.


   .. figure:: /_static/images/en-us_image_0000002065202201.png
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
      | Enterprise Project    | Mandatory                                                                                                                                             | default               |
      |                       |                                                                                                                                                       |                       |
      |                       | Enterprise project that the firewall belongs to.                                                                                                      |                       |
      |                       |                                                                                                                                                       |                       |
      |                       | An enterprise project facilitates project-level management and grouping of cloud resources and users. The default project is **default**.             |                       |
      |                       |                                                                                                                                                       |                       |
      |                       | For details about creating and managing enterprise projects, see the *Enterprise Management User Guide*.                                              |                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Tag                   | Optional                                                                                                                                              | **Tag key**: test     |
      |                       |                                                                                                                                                       |                       |
      |                       | When creating a firewall, you can add tags to it to help you identify and search for firewalls.                                                       | **Tag value**: 01     |
      |                       |                                                                                                                                                       |                       |
      |                       | For details, see :ref:`Managing Firewall Tags <vpc_acl_0013>`.                                                                                        |                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the firewall. This parameter is optional.                                                                             | N/A                   |
      |                       |                                                                                                                                                       |                       |
      |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                   |                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865663057.png
