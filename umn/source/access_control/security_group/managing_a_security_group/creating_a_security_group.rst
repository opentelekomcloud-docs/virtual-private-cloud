:original_name: en-us_topic_0013748715.html

.. _en-us_topic_0013748715:

Creating a Security Group
=========================

Scenarios
---------

A security group is a collection of access control rules to control the traffic that is allowed to reach and leave the cloud resources that it is associated with. The cloud resources can be cloud servers, containers, databases, and more. Cloud resources associated with the same security group have the same security requirements and are mutually trusted within a VPC. A security group consists of inbound and outbound rules.

If your instances have different Internet access requirements, you can allocate them to different security groups when creating them.

Each ECS must be associated with at least one security group. If you do not have a security group when creating an ECS, the system provides a default security group.

Preset Security Group Rules
---------------------------

The system provides several security group templates for you to create a security group. A security group template has preconfigured inbound and outbound rules. You can select a template based on your service requirements. :ref:`Table 1 <en-us_topic_0013748715__table1245448172512>` describes the security group templates.

.. _en-us_topic_0013748715__table1245448172512:

.. table:: **Table 1** Security group template description

   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Template                   | Direction | Protocol & Port & Type   | Source or Destination  | Description                                                                                                                            | Scenario                                                                                                                |
   +============================+===========+==========================+========================+========================================================================================================================================+=========================================================================================================================+
   | General-purpose web server | Inbound   | TCP: 22 (IPv4)           | 0.0.0.0/0              | Allows all IPv4 addresses to access instances in the security group over port 22 (SSH) for remotely logging in to Linux instances.     | -  Remotely logging in to an instance (such as an ECS) in the security group from an external network                   |
   |                            |           |                          |                        |                                                                                                                                        | -  Enabling external servers to ping the instances in the security group to verify network connectivity                 |
   |                            |           |                          |                        |                                                                                                                                        | -  Using instances in the security group as web servers to provide website services accessible from an external network |
   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   |                            |           | TCP: 3389 (IPv4)         | 0.0.0.0/0              | Allows all IPv4 addresses to access instances in the security group over port 3389 (RDP) for remotely logging in to Windows instances. |                                                                                                                         |
   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   |                            |           | TCP: 80 (IPv4)           | 0.0.0.0/0              | Allows all IPv4 addresses to access instances in the security group over port 80 (HTTP) for visiting websites.                         |                                                                                                                         |
   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   |                            |           | TCP: 443 (IPv4)          | 0.0.0.0/0              | Allows all IPv4 addresses to access instances in the security group over port 443 (HTTPS) for visiting websites.                       |                                                                                                                         |
   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   |                            |           | ICMP: All (IPv4)         | 0.0.0.0/0              | Allows all IPv4 addresses to access instances in the security group over any port for using the ping command to test connectivity.     |                                                                                                                         |
   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   |                            |           | All (IPv4)               | Current security group | Allows the instances in the security group to communicate with each other over an internal network over any protocol.                  |                                                                                                                         |
   |                            |           |                          |                        |                                                                                                                                        |                                                                                                                         |
   |                            |           | All (IPv6)               |                        |                                                                                                                                        |                                                                                                                         |
   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   |                            | Outbound  | All (IPv4)               | 0.0.0.0/0              | Allows all traffic from the instances in the security group to external resources over any protocol.                                   |                                                                                                                         |
   |                            |           |                          |                        |                                                                                                                                        |                                                                                                                         |
   |                            |           | All (IPv6)               |                        |                                                                                                                                        |                                                                                                                         |
   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | All ports open             | Inbound   | All (IPv4)               | Current security group | Allows the instances in the security group to communicate with each other over an internal network over any protocol.                  | This template allows any traffic to enter and leave the instances in the security group, which has security risks.      |
   |                            |           |                          |                        |                                                                                                                                        |                                                                                                                         |
   |                            |           | All (IPv6)               |                        |                                                                                                                                        |                                                                                                                         |
   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   |                            |           | All (IPv4)               | 0.0.0.0/0              | Allows any IP address to access the instances in the security group over any protocol.                                                 |                                                                                                                         |
   |                            |           |                          |                        |                                                                                                                                        |                                                                                                                         |
   |                            |           | All (IPv6)               |                        |                                                                                                                                        |                                                                                                                         |
   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   |                            | Outbound  | All (IPv4)               | 0.0.0.0/0              | Allows all traffic from the instances in the security group to external resources over any protocol.                                   |                                                                                                                         |
   |                            |           |                          |                        |                                                                                                                                        |                                                                                                                         |
   |                            |           | All (IPv6)               |                        |                                                                                                                                        |                                                                                                                         |
   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Common ports open          | Inbound   | All (IPv4)               | Current security group | Allows the instances in the security group to communicate with each other over an internal network over any protocol.                  | You can select protocols and ports that the inbound rule will apply to.                                                 |
   |                            |           |                          |                        |                                                                                                                                        |                                                                                                                         |
   |                            |           | All (IPv6)               |                        |                                                                                                                                        |                                                                                                                         |
   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   |                            |           | Custom port and protocol | 0.0.0.0/0              | Allows all IP addresses to access instances in the security group over specified ports (TCP or ICMP) for different purposes.           |                                                                                                                         |
   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   |                            | Outbound  | All (IPv4)               | 0.0.0.0/0              | Allows all traffic from the instances in the security group to external resources over any protocol.                                   |                                                                                                                         |
   |                            |           |                          |                        |                                                                                                                                        |                                                                                                                         |
   |                            |           | All (IPv6)               | ::/0                   |                                                                                                                                        |                                                                                                                         |
   +----------------------------+-----------+--------------------------+------------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+

Notes and Constraints
---------------------

If you have not created any security groups yet, the system automatically creates a default security group for you and associates it with the instance (such as an ECS) when you create it.

The default security group name is **default**. For details, see :ref:`Default Security Group and Its Rules <securitygroup_0003>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. In the upper right corner, click **Create Security Group**.

   The **Create Security Group** page is displayed.

#. Configure the parameters as prompted.


   .. figure:: /_static/images/en-us_image_0000002555381165.png
      :alt: **Figure 1** Create Security Group

      **Figure 1** Create Security Group

   .. table:: **Table 2** Parameter description

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+
      | Parameter             | Description                                                                                                                                                                          | Example Value              |
      +=======================+======================================================================================================================================================================================+============================+
      | Name                  | Mandatory                                                                                                                                                                            | sg-AB                      |
      |                       |                                                                                                                                                                                      |                            |
      |                       | Enter the security group name.                                                                                                                                                       |                            |
      |                       |                                                                                                                                                                                      |                            |
      |                       | The security group name can contain a maximum of 64 characters, which can consist of letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot contain spaces. |                            |
      |                       |                                                                                                                                                                                      |                            |
      |                       | .. note::                                                                                                                                                                            |                            |
      |                       |                                                                                                                                                                                      |                            |
      |                       |    You can change the security group name after a security group is created. It is recommended that you give each security group a different name.                                   |                            |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+
      | Enterprise Project    | Mandatory                                                                                                                                                                            | default                    |
      |                       |                                                                                                                                                                                      |                            |
      |                       | When creating a security group, you can add the security group to an enabled enterprise project.                                                                                     |                            |
      |                       |                                                                                                                                                                                      |                            |
      |                       | An enterprise project facilitates project-level management and grouping of cloud resources and users. The name of the default project is **default**.                                |                            |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+
      | Description           | Optional                                                                                                                                                                             | N/A                        |
      |                       |                                                                                                                                                                                      |                            |
      |                       | Supplementary information about the security group. This parameter is optional.                                                                                                      |                            |
      |                       |                                                                                                                                                                                      |                            |
      |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                                  |                            |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+
      | Template              | Mandatory                                                                                                                                                                            | General-purpose web server |
      |                       |                                                                                                                                                                                      |                            |
      |                       | The templates have preset inbound and outbound rules. You can select one as needed to quickly create a security group.                                                               |                            |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------+

#. Click **OK**.

Related Operations
------------------

-  After a security group is created, if its rules cannot meet your service requirements, you can add new rules to the security group or modify original rules. For details, see :ref:`Adding a Security Group Rule <en-us_topic_0030969470>`.
-  Each ECS must be associated with at least one security group. You can add an ECS to multiple security groups based on service requirements. For details, see :ref:`Adding an Instance to or Removing an Instance from a Security Group <securitygroup_0017>`.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865582681.png
