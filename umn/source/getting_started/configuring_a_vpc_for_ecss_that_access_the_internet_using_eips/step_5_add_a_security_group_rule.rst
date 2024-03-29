:original_name: vpc_qs_0013.html

.. _vpc_qs_0013:

Step 5: Add a Security Group Rule
=================================

Scenarios
---------

A security group is a collection of access control rules to control the traffic that is allowed to reach and leave the cloud resources that it is associated with. The cloud resources can be cloud servers, containers, databases, and more. Cloud resources associated with the same security group have the same security requirements and are mutually trusted within a VPC. A security group consists of inbound and outbound rules.

Each ECS must be associated with at least one security group. If you do not have a security group when creating an ECS, the system provides a default security group.

Like whitelists, security group rules work as follows:

-  Inbound rules control incoming traffic to instances in the security group.

   If an inbound request matches the source in an inbound security group rule, the request is allowed and other requests are denied.

   By default, you do not need to configure deny rules in the inbound direction because requests that do not match allow rules will be denied.

-  Outbound rules control outgoing traffic from instances in the security group.

   If the destination of an outbound security group rule is 0.0.0.0/0, all outbound requests are allowed.

   0.0.0.0/0 represents all IPv4 addresses.

   ::/0 represents all IPv6 addresses.

If the rules of the security group associated with your instance cannot meet your requirements, for example, you need to allow inbound traffic on a specific TCP port, you can add an inbound rule to allow traffic on the TCP port.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. Locate the row that contains the target security group, and click **Manage Rule** in the **Operation** column.

   The page for configuring security group rules is displayed.

#. On the **Inbound Rules** tab, click **Add Rule**.

   The **Add Inbound Rule** dialog box is displayed.

#. Configure required parameters.

   You can click **+** to add more inbound rules.


   .. figure:: /_static/images/en-us_image_0284920908.png
      :alt: **Figure 1** Add Inbound Rule

      **Figure 1** Add Inbound Rule

   .. table:: **Table 1** Inbound rule parameter description

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                                                        | Example Value         |
      +=======================+====================================================================================================================================================================================================================================================================================================================================================================================================================+=======================+
      | Protocol & Port       | The network protocol used to match traffic in a security group rule.                                                                                                                                                                                                                                                                                                                                               | TCP                   |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      |                       | Currently, the value can be **All**, **TCP**, **UDP**, **GRE**, **ICMP**, or more.                                                                                                                                                                                                                                                                                                                                 |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      |                       | **Port**: The port or port range over which traffic can reach your ECS. The value can be from 1 to 65535.                                                                                                                                                                                                                                                                                                          | 22, or 22-30          |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Type                  | Source IP address version. You can select:                                                                                                                                                                                                                                                                                                                                                                         | IPv4                  |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      |                       | -  IPv4                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                       | -  IPv6                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source                | Source of the security group rule. The value can be an IP address, a security group, or an IP address group to allow access from IP addresses or instances in the security group. For example:                                                                                                                                                                                                                     | 0.0.0.0/0             |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      |                       | -  IP address:                                                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      |                       |    -  Single IP address: 192.168.10.10/32                                                                                                                                                                                                                                                                                                                                                                          |                       |
      |                       |    -  All IP addresses: 0.0.0.0/0                                                                                                                                                                                                                                                                                                                                                                                  |                       |
      |                       |    -  IP address range: 192.168.1.0/24                                                                                                                                                                                                                                                                                                                                                                             |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      |                       | -  **Security group**: The source is from another security group. You can select a security group in the same region under the current account from the drop-down list. Instance A is in security group A and instance B is in security group B. If security group A has an inbound rule with **Action** set to **Allow** and **Source** set to security group B, access from instance B is allowed to instance A. |                       |
      |                       | -  **IP address group**: An IP address group is a collection of one or more IP addresses. You can select an available IP address group from the drop-down list. An IP address group can help you manage IP address ranges and IP addresses with same security requirements in a more simple way.                                                                                                                   |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      |                       | If the source is a security group, this rule will apply to all instances associated with the selected security group.                                                                                                                                                                                                                                                                                              |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the security group rule. This parameter is optional.                                                                                                                                                                                                                                                                                                                               | N/A                   |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      |                       | The security group rule description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                                                                                                                                                                                                                                            |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

   The inbound rule list is displayed.

#. On the **Outbound Rules** tab, click **Add Rule**.

   The **Add Outbound Rule** dialog box is displayed.

#. Configure required parameters.

   You can click **+** to add more outbound rules.


   .. figure:: /_static/images/en-us_image_0284993717.png
      :alt: **Figure 2** Add Outbound Rule

      **Figure 2** Add Outbound Rule

   .. table:: **Table 2** Outbound rule parameter description

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                                                        | Example Value         |
      +=======================+====================================================================================================================================================================================================================================================================================================================================================================================================================+=======================+
      | Protocol & Port       | The network protocol used to match traffic in a security group rule.                                                                                                                                                                                                                                                                                                                                               | TCP                   |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      |                       | Currently, the value can be **All**, **TCP**, **UDP**, **GRE**, **ICMP**, or more.                                                                                                                                                                                                                                                                                                                                 |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      |                       | **Port**: The port or port range over which traffic can leave your ECS. The value can be from 1 to 65535.                                                                                                                                                                                                                                                                                                          | 22, or 22-30          |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Type                  | Source IP address version. You can select:                                                                                                                                                                                                                                                                                                                                                                         | IPv4                  |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      |                       | -  IPv4                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      |                       | -  IPv6                                                                                                                                                                                                                                                                                                                                                                                                            |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination           | Destination of the security group rule. The value can be an IP address or a security group to allow access to IP addresses or instances in the security group. For example:                                                                                                                                                                                                                                        | 0.0.0.0/0             |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      |                       | -  IP address:                                                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      |                       |    -  Single IP address: 192.168.10.10/32                                                                                                                                                                                                                                                                                                                                                                          |                       |
      |                       |    -  All IP addresses: 0.0.0.0/0                                                                                                                                                                                                                                                                                                                                                                                  |                       |
      |                       |    -  IP address range: 192.168.1.0/24                                                                                                                                                                                                                                                                                                                                                                             |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      |                       | -  **Security group**: The source is from another security group. You can select a security group in the same region under the current account from the drop-down list. Instance A is in security group A and instance B is in security group B. If security group A has an inbound rule with **Action** set to **Allow** and **Source** set to security group B, access from instance B is allowed to instance A. |                       |
      |                       | -  **IP address group**: An IP address group is a collection of one or more IP addresses. You can select an available IP address group from the drop-down list. An IP address group can help you manage IP address ranges and IP addresses with same security requirements in a more simple way.                                                                                                                   |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the security group rule. This parameter is optional.                                                                                                                                                                                                                                                                                                                               | N/A                   |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      |                       | The security group rule description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                                                                                                                                                                                                                                            |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

   The outbound rule list is displayed.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001626734166.png
