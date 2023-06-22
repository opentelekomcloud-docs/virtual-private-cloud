:original_name: vpc_qs_0012.html

.. _vpc_qs_0012:

Step 4: Create a Security Group
===============================

Scenarios
---------

You can create security groups and add ECSs in a VPC to different security groups to improve ECS access security. We recommend that you allocate ECSs that have different Internet access requirements to different security groups.

Each ECS must be associated with at least one security group. If you have no security group when creating an ECS, the system provides a default security group.

You have an option to create a new security group for the ECS. This section describes how to create a security group on the management console.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

#. On the **Security Groups** page, click **Create Security Group**.

#. In the **Create Security Group** area, set the parameters as prompted. :ref:`Table 1 <vpc_qs_0012__en-us_topic_0013748715_table65377617111335>` lists the parameters to be configured.


   .. figure:: /_static/images/en-us_image_0000001197426329.png
      :alt: **Figure 1** Create Security Group

      **Figure 1** Create Security Group

   .. _vpc_qs_0012__en-us_topic_0013748715_table65377617111335:

   .. table:: **Table 1** Parameter description

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+
      | Parameter             | Description                                                                                                                                                                                                                                           | Example Value              |
      +=======================+=======================================================================================================================================================================================================================================================+============================+
      | Name                  | The security group name. This parameter is mandatory.                                                                                                                                                                                                 | sg-318b                    |
      |                       |                                                                                                                                                                                                                                                       |                            |
      |                       | The security group name can contain a maximum of 64 characters, which may consist of letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot contain spaces.                                                                  |                            |
      |                       |                                                                                                                                                                                                                                                       |                            |
      |                       | .. note::                                                                                                                                                                                                                                             |                            |
      |                       |                                                                                                                                                                                                                                                       |                            |
      |                       |    You can change the security group name after a security group is created. It is recommended that you give each security group a different name.                                                                                                    |                            |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+
      | Enterprise Project    | When creating a security group, you can add the security group to an enabled enterprise project.                                                                                                                                                      | default                    |
      |                       |                                                                                                                                                                                                                                                       |                            |
      |                       | An enterprise project facilitates project-level management and grouping of cloud resources and users. The name of the default project is **default**.                                                                                                 |                            |
      |                       |                                                                                                                                                                                                                                                       |                            |
      |                       | For details about creating and managing enterprise projects, see the *Enterprise Management User Guide*.                                                                                                                                              |                            |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+
      | Template              | A template comes with default security group rules, helping you quickly create security groups. The following templates are provided:                                                                                                                 | General-purpose web server |
      |                       |                                                                                                                                                                                                                                                       |                            |
      |                       | -  **Custom**: This template allows you to create security groups with custom security group rules.                                                                                                                                                   |                            |
      |                       | -  **General-purpose web server**: The security group that you create using this template is for general-purpose web servers and includes default rules that allow all inbound ICMP traffic and allow inbound traffic on ports 22, 80, 443, and 3389. |                            |
      |                       | -  **All ports open**: The security group that you create using this template includes default rules that allow inbound traffic on any port. Note that allowing inbound traffic on any port poses security risks.                                     |                            |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+
      | Description           | Supplementary information about the security group. This parameter is optional.                                                                                                                                                                       | N/A                        |
      |                       |                                                                                                                                                                                                                                                       |                            |
      |                       | The security group description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                                                                                    |                            |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001500905066.png
