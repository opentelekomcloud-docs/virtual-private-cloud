:original_name: vpc_qs_0013.html

.. _vpc_qs_0013:

Step 5: Add a Security Group Rule
=================================

Scenarios
---------

A security group is a collection of access control rules for cloud resources, such as cloud servers, containers, and databases, to control inbound and outbound traffic. Cloud resources associated with the same security group have the same security requirements and are mutually trusted within a VPC.

If the rules of the security group associated with your instance cannot meet your requirements, for example, you need to allow inbound traffic on a specified TCP port, you can add an inbound rule.

-  Inbound rules control incoming traffic to cloud resources in the security group.
-  Outbound rules control outgoing traffic from cloud resources in the security group.

For details about the default security group rules, see :ref:`Default Security Groups and Security Group Rules <securitygroup_0003>`. For details about security group rule configuration examples, see :ref:`Security Group Configuration Examples <en-us_topic_0081124350>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, under **Network**, click **Virtual Private Cloud**.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

#. On the **Security Groups** page, locate the target security group and click **Manage Rule** in the **Operation** column to switch to the page for managing inbound and outbound rules.

#. On the **Inbound Rules** tab, click **Add Rule**. In the displayed dialog box, set required parameters to add an inbound rule.

   You can click **+** to add more inbound rules.


   .. figure:: /_static/images/en-us_image_0284920908.png
      :alt: **Figure 1** Add Inbound Rule

      **Figure 1** Add Inbound Rule

   .. table:: **Table 1** Inbound rule parameter description

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                          | Example Value         |
      +=======================+======================================================================================================================================================================================+=======================+
      | Protocol & Port       | **Protocol**: The network protocol. Currently, the value can be **All**, **TCP**, **UDP**, **ICMP**, **GRE**, or others.                                                             | TCP                   |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      |                       | **Port**: The port or port range over which the traffic can reach your ECS. The value ranges from 1 to 65535.                                                                        | 22, or 22-30          |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source                | The source of the security group rule. The value can be a single IP address or a security group to allow access from the IP address or instances in the security group. For example: | 0.0.0.0/0             |
      |                       |                                                                                                                                                                                      |                       |
      |                       | -  xxx.xxx.xxx.xxx/32 (IPv4 address)                                                                                                                                                 |                       |
      |                       | -  xxx.xxx.xxx.0/24 (IPv4 address range)                                                                                                                                             |                       |
      |                       | -  0.0.0.0/0 (all IPv4 addresses)                                                                                                                                                    |                       |
      |                       | -  sg-abc (security group)                                                                                                                                                           |                       |
      |                       |                                                                                                                                                                                      |                       |
      |                       | If the source is a security group, this rule will apply to all instances associated with the selected security group.                                                                |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the security group rule. This parameter is optional.                                                                                                 | N/A                   |
      |                       |                                                                                                                                                                                      |                       |
      |                       | The security group rule description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                              |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. On the **Outbound Rules** tab, click **Add Rule**. In the displayed dialog box, set required parameters to add an outbound rule.

   You can click **+** to add more outbound rules.


   .. figure:: /_static/images/en-us_image_0284993717.png
      :alt: **Figure 2** Add Outbound Rule

      **Figure 2** Add Outbound Rule

   .. table:: **Table 2** Outbound rule parameter description

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                             | Example Value         |
      +=======================+=========================================================================================================================================================================================+=======================+
      | Protocol & Port       | **Protocol**: The network protocol. Currently, the value can be **All**, **TCP**, **UDP**, **ICMP**, **GRE**, or others.                                                                | TCP                   |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      |                       | **Port**: The port or port range over which the traffic can leave your ECS. The value ranges from 1 to 65535.                                                                           | 22, or 22-30          |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination           | The destination of the security group rule. The value can be a single IP address or a security group to allow access to the IP address or instances in the security group. For example: | 0.0.0.0/0             |
      |                       |                                                                                                                                                                                         |                       |
      |                       | -  xxx.xxx.xxx.xxx/32 (IPv4 address)                                                                                                                                                    |                       |
      |                       | -  xxx.xxx.xxx.0/24 (IPv4 address range)                                                                                                                                                |                       |
      |                       | -  0.0.0.0/0 (all IPv4 addresses)                                                                                                                                                       |                       |
      |                       | -  sg-abc (security group)                                                                                                                                                              |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the security group rule. This parameter is optional.                                                                                                    | N/A                   |
      |                       |                                                                                                                                                                                         |                       |
      |                       | The security group rule description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                 |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png