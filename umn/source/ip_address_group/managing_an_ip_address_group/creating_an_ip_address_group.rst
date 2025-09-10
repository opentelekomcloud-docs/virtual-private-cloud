:original_name: vpc_IPAddressGroup_0003.html

.. _vpc_IPAddressGroup_0003:

Creating an IP Address Group
============================

Scenarios
---------

This section describes how to create an IP address group. An IP address group is a collection of IP addresses that can be associated with security groups to simplify IP address configuration and management.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **IP Address Groups**.

   The IP address group list is displayed.

5. In the upper right corner of the IP address group list, click **Create IP Address Group**.

   The **Create IP Address Group** page is displayed.

6. Configure the parameters as prompted.

   For details, see :ref:`Table 1 <vpc_ipaddressgroup_0003__table15989174133114>`.

   .. _vpc_ipaddressgroup_0003__table15989174133114:

   .. table:: **Table 1** Parameters for creating an IP address group

      +-----------------------+------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                              | Example Value         |
      +=======================+==========================================================================================+=======================+
      | Region                | Mandatory                                                                                | Region A              |
      |                       |                                                                                          |                       |
      |                       | Select the region nearest to you to ensure the lowest latency possible.                  |                       |
      |                       |                                                                                          |                       |
      |                       | An IP address group can be associated only with resources in the same region.            |                       |
      +-----------------------+------------------------------------------------------------------------------------------+-----------------------+
      | Name                  | Mandatory                                                                                | ipGroup-A             |
      |                       |                                                                                          |                       |
      |                       | Enter the name of the IP address group. The name:                                        |                       |
      |                       |                                                                                          |                       |
      |                       | -  Can contain 1 to 64 characters.                                                       |                       |
      |                       | -  Can contain letters, digits, underscores (_), hyphens (-), and periods (.).           |                       |
      |                       |                                                                                          |                       |
      |                       | You can customize the name of an IP address group that is uniquely identified by its ID. |                       |
      +-----------------------+------------------------------------------------------------------------------------------+-----------------------+
      | IP Address Version    | Mandatory                                                                                | IPv4                  |
      |                       |                                                                                          |                       |
      |                       | Select the type of IP addresses that can be added to an IP address group.                |                       |
      |                       |                                                                                          |                       |
      |                       | -  IPv4                                                                                  |                       |
      |                       | -  IPv6                                                                                  |                       |
      +-----------------------+------------------------------------------------------------------------------------------+-----------------------+
      | IP Addresses          | Optional                                                                                 | 192.168.0.0/16        |
      |                       |                                                                                          |                       |
      |                       | Enter an IP address or IP address range on each line, and press **Enter**.               | 192.168.10.10/32      |
      |                       |                                                                                          |                       |
      |                       | You can enter:                                                                           |                       |
      |                       |                                                                                          |                       |
      |                       | -  An IPv4 address range, for example, 192.168.0.0/16                                    |                       |
      |                       | -  A single IPv4 address, for example, 192.168.10.10/32                                  |                       |
      |                       | -  An IPv6 address range, for example, 2001:db8:a583:6e::/64                             |                       |
      |                       | -  A single IPv6 address, for example, 2001:db8:a583:6e::5c/128                          |                       |
      +-----------------------+------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Optional                                                                                 | ``-``                 |
      |                       |                                                                                          |                       |
      |                       | Enter the description of the IP address group in the text box as required.               |                       |
      +-----------------------+------------------------------------------------------------------------------------------+-----------------------+

7. Click **Create Now**.

   The IP address group list is displayed. The status of the created IP address group is **Normal**.

   .. important::

      An IP address group takes effect only after it is associated with corresponding resources. For details, see :ref:`Associating an IP Address Group with Resources <vpc_ipaddressgroup_0004>`.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865582865.png
