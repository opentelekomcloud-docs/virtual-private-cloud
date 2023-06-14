:original_name: vpc_SecurityGroup_0007.html

.. _vpc_SecurityGroup_0007:

Importing and Exporting Security Group Rules
============================================

Scenarios
---------

-  If you want to quickly create or restore security group rules, you can import existing rules to the security group.
-  If you want to back up security group rules locally, you can export the rules to an Excel file.
-  If you want to quickly apply the rules of one security group to another, or if you want to modify multiple rules of the current security group at once, you can import or export existing rules.

Notes and Constraints
---------------------

-  When modifying exported security group rules, you can only modify existing fields in the exported file based on the template and cannot add new fields or modify the field names. Otherwise, the file will fail to be imported.
-  Duplicate rules are not allowed.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.
#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.
#. On the **Security Groups** page, click the security group name.
#. Export and import security group rules.

   -  Click |image3| to export all rules of the current security group to an Excel file.

   -  Click |image4| to import security group rules from an Excel file into the current security group.

      :ref:`Table 1 <vpc_securitygroup_0007__table111445216564>` describes the parameters in the template for importing rules.

      .. _vpc_securitygroup_0007__table111445216564:

      .. table:: **Table 1** Template parameters

         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Parameter             | Description                                                                                                                                                                 | Example Value         |
         +=======================+=============================================================================================================================================================================+=======================+
         | Direction             | The direction in which the security group rule takes effect.                                                                                                                | Inbound               |
         |                       |                                                                                                                                                                             |                       |
         |                       | -  Inbound rules control incoming traffic to cloud resources in the security group.                                                                                         |                       |
         |                       | -  Outbound rules control outgoing traffic from cloud resources in the security group.                                                                                      |                       |
         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Protocol & Port       | **Protocol**: The network protocol. Currently, the value can be **All**, **TCP**, **UDP**, **ICMP**, **GRE**, or others.                                                    | TCP                   |
         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         |                       | **Port**: The port or port range over which the traffic can reach your ECS. The value ranges from 1 to 65535.                                                               | 22, or 22-30          |
         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Source                | Source of the security group rule. The value can be an IP address or a security group to allow access from IP addresses or instances in the security group. For example:    | 0.0.0.0/0             |
         |                       |                                                                                                                                                                             |                       |
         |                       | -  IP address:                                                                                                                                                              |                       |
         |                       |                                                                                                                                                                             |                       |
         |                       |    -  Single IP address: 192.168.10.10/32                                                                                                                                   |                       |
         |                       |    -  All IP addresses: 0.0.0.0/0                                                                                                                                           |                       |
         |                       |    -  IP address range: 192.168.1.0/24                                                                                                                                      |                       |
         |                       |                                                                                                                                                                             |                       |
         |                       | -  Security group: sg-A                                                                                                                                                     |                       |
         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Destination           | Destination of the security group rule. The value can be an IP address or a security group to allow access to IP addresses or instances in the security group. For example: | 0.0.0.0/0             |
         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Description           | Supplementary information about the security group rule. This parameter is optional.                                                                                        | ``-``                 |
         |                       |                                                                                                                                                                             |                       |
         |                       | The security group rule description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                     |                       |
         +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001500905066.png
.. |image3| image:: /_static/images/en-us_image_0142360062.png
.. |image4| image:: /_static/images/en-us_image_0142360094.png
