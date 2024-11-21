:original_name: SecurityGroup_0004.html

.. _SecurityGroup_0004:

Fast-Adding Security Group Rules
================================

Scenarios
---------

The fast-adding rule function of security groups allows you to quickly add rules with common ports and protocols for remote login, ping tests, common web services, and database services.

Procedure
---------

#. Log in to the management console.

2.  Click |image1| in the upper left corner and select the desired region and project.

3.  Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

    The **Virtual Private Cloud** page is displayed.

4.  In the navigation pane on the left, choose **Access Control** > **Security Groups**.

    The security group list is displayed.

5.  Locate the row that contains the target security group and click **Manage Rules** in the **Operation** column.

    The page for configuring security group rules is displayed.

6.  On the **Inbound Rules** tab, click **Fast-Add Rule**.

    The **Fast-Add Inbound Rule** dialog box is displayed.

7.  Configure required parameters.


    .. figure:: /_static/images/en-us_image_0000002029168046.png
       :alt: **Figure 1** Fast-Add Inbound Rule

       **Figure 1** Fast-Add Inbound Rule

    .. table:: **Table 1** Inbound rule parameter description

       +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Parameter             | Description                                                                                                                                                                  | Example Value         |
       +=======================+==============================================================================================================================================================================+=======================+
       | Protocols and Ports   | Common protocols and ports are provided for:                                                                                                                                 | SSH (22)              |
       |                       |                                                                                                                                                                              |                       |
       |                       | -  Remote login and ping                                                                                                                                                     |                       |
       |                       | -  Web services                                                                                                                                                              |                       |
       |                       | -  Databases                                                                                                                                                                 |                       |
       +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Type                  | Source IP address version. You can select:                                                                                                                                   | IPv4                  |
       |                       |                                                                                                                                                                              |                       |
       |                       | -  IPv4                                                                                                                                                                      |                       |
       |                       | -  IPv6                                                                                                                                                                      |                       |
       +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Source                | Source of the security group rule. The value can be an IP address or a security group to allow access from IP addresses or instances in the security group. You can specify: | 0.0.0.0/0             |
       |                       |                                                                                                                                                                              |                       |
       |                       | -  xxx.xxx.xxx.xxx/32 (IPv4 address)                                                                                                                                         |                       |
       |                       | -  xxx.xxx.xxx.0/24 (IPv4 address range)                                                                                                                                     |                       |
       |                       | -  0.0.0.0/0 (all IPv4 addresses)                                                                                                                                            |                       |
       |                       | -  sg-abc (security group)                                                                                                                                                   |                       |
       |                       |                                                                                                                                                                              |                       |
       |                       | If the source is a security group, this rule will apply to all instances associated with the selected security group.                                                        |                       |
       +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Action                | Allow or Deny                                                                                                                                                                | Allow                 |
       |                       |                                                                                                                                                                              |                       |
       |                       | -  If the **Action** is set to **Allow**, access from the source is allowed to ECSs in the security group over specified ports.                                              |                       |
       |                       | -  If the **Action** is set to **Deny**, access from the source is denied to ECSs in the security group over specified ports.                                                |                       |
       |                       |                                                                                                                                                                              |                       |
       |                       | Deny rules take precedence over allow rules of the same priority.                                                                                                            |                       |
       +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Priority              | Security group rule priority.                                                                                                                                                | 1                     |
       |                       |                                                                                                                                                                              |                       |
       |                       | The priority value is from 1 to 100. The default value is 1 and has the highest priority. The security group rule with a smaller value has a higher priority.                |                       |
       +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Description           | (Optional) Supplementary information about the security group rule.                                                                                                          | ``-``                 |
       |                       |                                                                                                                                                                              |                       |
       |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                          |                       |
       +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

8.  Click **OK**.

    The inbound rule list is displayed and you can view your added rule.

9.  On the **Outbound Rules** tab, click **Fast-Add Rule**.

    The **Fast-Add Outbound Rule** dialog box is displayed.

10. Configure required parameters.


    .. figure:: /_static/images/en-us_image_0000002065209133.png
       :alt: **Figure 2** Fast-Add Outbound Rule

       **Figure 2** Fast-Add Outbound Rule

    .. table:: **Table 2** Outbound rule parameter description

       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Parameter             | Description                                                                                                                                                                     | Example Value         |
       +=======================+=================================================================================================================================================================================+=======================+
       | Protocols and Ports   | Common protocols and ports are provided for:                                                                                                                                    | SSH (22)              |
       |                       |                                                                                                                                                                                 |                       |
       |                       | -  Remote login and ping                                                                                                                                                        |                       |
       |                       | -  Web services                                                                                                                                                                 |                       |
       |                       | -  Databases                                                                                                                                                                    |                       |
       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Type                  | Source IP address version. You can select:                                                                                                                                      | IPv4                  |
       |                       |                                                                                                                                                                                 |                       |
       |                       | -  IPv4                                                                                                                                                                         |                       |
       |                       | -  IPv6                                                                                                                                                                         |                       |
       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Destination           | Destination of the security group rule. The value can be an IP address or a security group to allow access to IP addresses or instances in the security group. You can specify: | 0.0.0.0/0             |
       |                       |                                                                                                                                                                                 |                       |
       |                       | -  xxx.xxx.xxx.xxx/32 (IPv4 address)                                                                                                                                            |                       |
       |                       | -  xxx.xxx.xxx.0/24 (IPv4 address range)                                                                                                                                        |                       |
       |                       | -  0.0.0.0/0 (all IPv4 addresses)                                                                                                                                               |                       |
       |                       | -  sg-abc (security group)                                                                                                                                                      |                       |
       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Priority              | Security group rule priority.                                                                                                                                                   | 1                     |
       |                       |                                                                                                                                                                                 |                       |
       |                       | The priority value is from 1 to 100. The default value is 1 and has the highest priority. The security group rule with a smaller value has a higher priority.                   |                       |
       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Action                | Allow or Deny                                                                                                                                                                   | Allow                 |
       |                       |                                                                                                                                                                                 |                       |
       |                       | -  If the **Action** is set to **Allow**, access from ECSs in the security group is allowed to the destination over specified ports.                                            |                       |
       |                       | -  If the **Action** is set to **Deny**, access from ECSs in the security group is denied to the destination over specified ports.                                              |                       |
       |                       |                                                                                                                                                                                 |                       |
       |                       | Deny rules take precedence over allow rules of the same priority.                                                                                                               |                       |
       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Description           | (Optional) Supplementary information about the security group rule.                                                                                                             | ``-``                 |
       |                       |                                                                                                                                                                                 |                       |
       |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                             |                       |
       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

11. Click **OK**.

    The outbound rule list is displayed and you can view your added rule.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818982858.png
