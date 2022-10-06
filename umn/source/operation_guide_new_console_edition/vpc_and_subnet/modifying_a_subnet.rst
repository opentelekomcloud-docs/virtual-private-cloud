:original_name: vpc_vpc_0001.html

.. _vpc_vpc_0001:

Modifying a Subnet
==================

Scenarios
---------

Modify the subnet name, NTP server address, and DNS server address.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. On the console homepage, under **Network**, click **Virtual Private Cloud**.
#. In the navigation pane on the left, click **Subnets**.
#. In the subnet list, locate the target subnet and click its name.
#. On the subnet details page, modify required parameters.

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                 | Example Value         |
      +=======================+=============================================================================================================================================================================================================================================+=======================+
      | Name                  | The subnet name.                                                                                                                                                                                                                            | Subnet                |
      |                       |                                                                                                                                                                                                                                             |                       |
      |                       | The name can contain a maximum of 64 characters, which may consist of letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot contain spaces.                                                                       |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | DNS Server Address    | By default, two DNS server addresses are configured. You can change them as required. A maximum of five DNS server addresses can be configured. Multiple IP addresses must be separated using commas (,).                                   | 100.125.x.x           |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | NTP Server Address    | The IP address of the NTP server. This parameter is optional.                                                                                                                                                                               | 192.168.2.1           |
      |                       |                                                                                                                                                                                                                                             |                       |
      |                       | You can configure the NTP server IP addresses to be added to the subnet as required. The IP addresses are added in addition to the default NTP server addresses. If this parameter is left empty, no IP address of the NTP server is added. |                       |
      |                       |                                                                                                                                                                                                                                             |                       |
      |                       | A maximum of four IP addresses can be configured. Multiple IP addresses must be separated using commas (,).                                                                                                                                 |                       |
      |                       |                                                                                                                                                                                                                                             |                       |
      |                       | .. note::                                                                                                                                                                                                                                   |                       |
      |                       |                                                                                                                                                                                                                                             |                       |
      |                       |    -  If you add or change the NTP server addresses of a subnet, you need to renew the DHCP lease for or restart all the ECSs in the subnet to make the change take effect immediately.                                                     |                       |
      |                       |    -  If the NTP server addresses have been cleared out, restarting the ECSs will not help. You must renew the DHCP lease for all ECSs to make the change take effect immediately.                                                          |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
