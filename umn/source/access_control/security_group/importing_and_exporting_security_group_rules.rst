:original_name: vpc_SecurityGroup_0007.html

.. _vpc_SecurityGroup_0007:

Importing and Exporting Security Group Rules
============================================

Scenarios
---------

You can configure security group rules in an Excel file and import the rules to the security group. You can also export security group rules to an Excel file. You are advised to use this function in the following scenarios:

-  If you want to quickly create or restore a security group rule, you can import your exported security group rule file to the security group.
-  If you want to back up security group rules locally, you can export the rules to an Excel file.
-  If you want to quickly apply the rules of one security group to another, or if you want to modify multiple rules of the current security group at once, you can import or export existing rules.

Notes and Constraints
---------------------

-  The security group rules to be imported must be configured based on the template. Do not add parameters or change existing parameters. Otherwise, the import will fail.
-  Duplicate rules are not allowed, you can delete the rule and try again.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. On the security group list, click the name of the target security group.

   The security group details page is displayed.

#. Export and import security group rules.

   -  Click |image3| to export all rules of the current security group to an Excel file.

   -  Click |image4| to import security group rules from an Excel file into the current security group.

      :ref:`Table 1 <vpc_securitygroup_0007__table111445216564>` describes the parameters in the template for importing rules.

      .. _vpc_securitygroup_0007__table111445216564:

      .. table:: **Table 1** Template parameters

         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+
         | Parameter             | Description                                                                                                                                                                 | Example Value                      |
         +=======================+=============================================================================================================================================================================+====================================+
         | Direction             | The direction in which the security group rule takes effect.                                                                                                                | Inbound                            |
         |                       |                                                                                                                                                                             |                                    |
         |                       | -  **Inbound**: Inbound rules control incoming traffic to instances in the security group.                                                                                  |                                    |
         |                       | -  **Outbound**: Outbound rules control outgoing traffic from instances in the security group.                                                                              |                                    |
         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+
         | Protocol & Port       | The network protocol used to match traffic in a security group rule.                                                                                                        | TCP                                |
         |                       |                                                                                                                                                                             |                                    |
         |                       | Currently, the value can be **All**, **TCP**, **UDP**, **GRE**, **ICMP**, or more.                                                                                          |                                    |
         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+
         |                       | **Port**: The port or port range over which traffic can reach your ECS. The value can be from 1 to 65535.                                                                   | 22, or 22-30                       |
         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+
         | Source                | Source of the security group rule. The value can be an IP address or a security group to allow access from IP addresses or instances in the security group. For example:    | sg-test[96a8a93f-XXX-d7872990c314] |
         |                       |                                                                                                                                                                             |                                    |
         |                       | -  IP address:                                                                                                                                                              |                                    |
         |                       |                                                                                                                                                                             |                                    |
         |                       |    -  Single IP address: 192.168.10.10/32                                                                                                                                   |                                    |
         |                       |    -  All IP addresses: 0.0.0.0/0                                                                                                                                           |                                    |
         |                       |    -  IP address range: 192.168.1.0/24                                                                                                                                      |                                    |
         |                       |                                                                                                                                                                             |                                    |
         |                       | -  Security group: sg-A                                                                                                                                                     |                                    |
         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+
         | Destination           | Destination of the security group rule. The value can be an IP address or a security group to allow access to IP addresses or instances in the security group. For example: | sg-test[96a8a93f-XXX-d7872990c314] |
         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+
         | Description           | Supplementary information about the security group rule. This parameter is optional.                                                                                        | ``-``                              |
         |                       |                                                                                                                                                                             |                                    |
         |                       | The security group rule description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                     |                                    |
         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001675254013.png
.. |image3| image:: /_static/images/en-us_image_0142360062.png
.. |image4| image:: /_static/images/en-us_image_0142360094.png
