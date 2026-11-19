:original_name: vpc_vip_0002.html

.. _vpc_vip_0002:

Assigning a Virtual IP Address
==============================

Scenarios
---------

A virtual IP address is an IP address assigned from a VPC subnet. It can be assigned and released independently. You can follow the instructions in this section to assign a virtual IP address.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Subnets**.

#. In the subnet list, click the name of the subnet where a virtual IP address is to be assigned.

   The subnet details page is displayed.

#. Click the **IP Addresses** tab and click **Assign Virtual IP Address**.

   The **Assign Virtual IP Address** page is displayed.


   .. figure:: /_static/images/en-us_image_0000002029118468.png
      :alt: **Figure 1** Assigning a virtual IP address

      **Figure 1** Assigning a virtual IP address

#. Configure the parameters as prompted.

   .. table:: **Table 1** Virtual IP address parameters

      +-----------------------+------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                      | Example Value         |
      +=======================+==================================================================================================================+=======================+
      | Subnet                | Subnet from which a virtual IP address will be assigned. The current subnet is selected by default.              | Subnet-A01            |
      +-----------------------+------------------------------------------------------------------------------------------------------------------+-----------------------+
      | IP Address Version    | IP address version. This parameter is available only when IPv6 is enabled for the subnet. There are two options: | IPv4                  |
      |                       |                                                                                                                  |                       |
      |                       | -  IPv4                                                                                                          |                       |
      |                       | -  IPv6                                                                                                          |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Assignment Mode       | How a virtual IP address is assigned. There are two options:                                                     | Manual                |
      |                       |                                                                                                                  |                       |
      |                       | -  **Automatic**: The system assigns a virtual IP address from the subnet.                                       |                       |
      |                       | -  **Manual**: You can specify a virtual IP address from the subnet.                                             |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------+-----------------------+
      | IP Address            | This parameter is required if **Assignment Mode** is set to **Manual**.                                          | 192.168.0.15          |
      |                       |                                                                                                                  |                       |
      |                       | Specify an available IP address from the subnet CIDR block.                                                      |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------+-----------------------+

#. After configuring the parameters, click **OK**.

   You can then query the assigned virtual IP address in the IP address list.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865663157.png
