:original_name: SecurityGroup_0004.html

.. _SecurityGroup_0004:

Fast-Adding Security Group Rules
================================

Scenarios
---------

You can add multiple security group rules with different protocols and ports at the same time.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

4. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

5. On the **Security Groups** page, locate the target security group and click **Manage Rule** in the **Operation** column to switch to the page for managing inbound and outbound rules.

6. On the **Inbound Rules** tab, click **Fast-Add Rule**. In the displayed dialog box, select the protocols and ports you wish to add all at once.


   .. figure:: /_static/images/en-us_image_0211552164.png
      :alt: **Figure 1** Fast-Add Inbound Rule

      **Figure 1** Fast-Add Inbound Rule

   .. table:: **Table 1** Inbound rule parameter description

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                              | Example Value         |
      +=======================+==========================================================================================================================================================================+=======================+
      | Protocols and Ports   | Common protocols and ports are provided for:                                                                                                                             | SSH (22)              |
      |                       |                                                                                                                                                                          |                       |
      |                       | -  Remote login and ping                                                                                                                                                 |                       |
      |                       | -  Web services                                                                                                                                                          |                       |
      |                       | -  Databases                                                                                                                                                             |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source                | Source of the security group rule. The value can be an IP address or a security group to allow access from IP addresses or instances in the security group. For example: | 0.0.0.0/0             |
      |                       |                                                                                                                                                                          |                       |
      |                       | -  xxx.xxx.xxx.xxx/32 (IPv4 address)                                                                                                                                     |                       |
      |                       | -  xxx.xxx.xxx.0/24 (IPv4 address range)                                                                                                                                 |                       |
      |                       | -  0.0.0.0/0 (all IPv4 addresses)                                                                                                                                        |                       |
      |                       | -  sg-abc (security group)                                                                                                                                               |                       |
      |                       |                                                                                                                                                                          |                       |
      |                       | If the source is a security group, this rule will apply to all instances associated with the selected security group.                                                    |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | (Optional) Supplementary information about the security group rule.                                                                                                      | ``-``                 |
      |                       |                                                                                                                                                                          |                       |
      |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                      |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7. On the **Outbound Rules** tab, click **Fast-Add Rule**. In the displayed dialog box, select required protocols and ports to add multiple rules at a time.


   .. figure:: /_static/images/en-us_image_0211560998.png
      :alt: **Figure 2** Fast-Add Outbound Rule

      **Figure 2** Fast-Add Outbound Rule

   .. table:: **Table 2** Outbound rule parameter description

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                 | Example Value         |
      +=======================+=============================================================================================================================================================================+=======================+
      | Protocols and Ports   | Common protocols and ports are provided for:                                                                                                                                | SSH (22)              |
      |                       |                                                                                                                                                                             |                       |
      |                       | -  Remote login and ping                                                                                                                                                    |                       |
      |                       | -  Web services                                                                                                                                                             |                       |
      |                       | -  Databases                                                                                                                                                                |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination           | Destination of the security group rule. The value can be an IP address or a security group to allow access to IP addresses or instances in the security group. For example: | 0.0.0.0/0             |
      |                       |                                                                                                                                                                             |                       |
      |                       | -  xxx.xxx.xxx.xxx/32 (IPv4 address)                                                                                                                                        |                       |
      |                       | -  xxx.xxx.xxx.0/24 (IPv4 address range)                                                                                                                                    |                       |
      |                       | -  0.0.0.0/0 (all IPv4 addresses)                                                                                                                                           |                       |
      |                       | -  sg-abc (security group)                                                                                                                                                  |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | (Optional) Supplementary information about the security group rule.                                                                                                         | ``-``                 |
      |                       |                                                                                                                                                                             |                       |
      |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                         |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

8. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001500905066.png
