:original_name: vpc_nic_0002.html

.. _vpc_nic_0002:

Creating a Network Interface
============================

Scenarios
---------

A primary network interface is created together with an instance by default. You can perform the following operations to create extended network interfaces on the **Network Interfaces** console.

Notes and Constraints
---------------------

An extended network interface created on the console can only be attached to an instance from the same VPC, but they can be associated with different security groups.

.. note::

   If you create an extended network interface using an API, the interface can be attached to an instance from a different VPC.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Network Interfaces**.

#. Click **Create Network Interface**.

#. Configure parameters for the network interface, as shown in :ref:`Table 1 <vpc_nic_0002__table145313414319>`.


   .. figure:: /_static/images/en-us_image_0000002202311621.png
      :alt: **Figure 1** Creating a network interface

      **Figure 1** Creating a network interface

   .. _vpc_nic_0002__table145313414319:

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Parameter Description                                                                                                                                                 | Example Value         |
      +=======================+=======================================================================================================================================================================+=======================+
      | Name                  | (Mandatory) Specifies the network interface name.                                                                                                                     | networkInterface-891e |
      |                       |                                                                                                                                                                       |                       |
      |                       | The name can contain a maximum of 64 characters, which can consist of letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot contain spaces. |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | VPC                   | (Mandatory) Select the VPC to which the network interface belongs.                                                                                                    | vpc-001               |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Subnet                | (Mandatory) Select the subnet that the network interface belongs to.                                                                                                  | subnet-001            |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Private IP Address    | Select whether to automatically or manually assign a private IP address.                                                                                              | xxx.xxx.xx.2          |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Security Group        | (Mandatory) Select the security group that will be associated with the network interface.                                                                             | sg-001                |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823734.png
