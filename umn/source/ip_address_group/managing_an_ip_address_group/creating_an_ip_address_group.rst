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


   .. figure:: /_static/images/en-us_image_0000002524311502.png
      :alt: **Figure 1** Creating an IP address group

      **Figure 1** Creating an IP address group

   .. _vpc_ipaddressgroup_0003__table15989174133114:

   .. table:: **Table 1** Parameters for creating an IP address group

      +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter                               | Description                                                                                                                                                               | Example Value         |
      +=========================================+===========================================================================================================================================================================+=======================+
      | Region                                  | Mandatory                                                                                                                                                                 | Region A              |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | Select the region nearest to you to ensure the lowest latency possible.                                                                                                   |                       |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | An IP address group can be associated only with resources in the same region.                                                                                             |                       |
      +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Name                                    | Mandatory                                                                                                                                                                 | ipGroup-A             |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | Enter the name of the IP address group. The name:                                                                                                                         |                       |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | -  Can contain 1 to 64 characters.                                                                                                                                        |                       |
      |                                         | -  Can contain letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                            |                       |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | You can customize the name of an IP address group that is uniquely identified by its ID.                                                                                  |                       |
      +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Enterprise Project                      | Mandatory                                                                                                                                                                 | default               |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | When creating an IP address group, you can add the group to an enabled enterprise project.                                                                                |                       |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | An enterprise project facilitates project-level management and grouping of cloud resources and users. The default project is **default**.                                 |                       |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | For details about creating and managing enterprise projects, see the *Enterprise Management User Guide*.                                                                  |                       |
      +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description                             | Optional                                                                                                                                                                  | ``-``                 |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | Enter the description of the IP address group in the text box as required.                                                                                                |                       |
      +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | IP Address Version                      | Mandatory                                                                                                                                                                 | IPv4                  |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | Select the type of IP addresses that can be added to an IP address group.                                                                                                 |                       |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | -  IPv4                                                                                                                                                                   |                       |
      |                                         | -  IPv6                                                                                                                                                                   |                       |
      +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Creation Method                         | Mandatory                                                                                                                                                                 | Create new            |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | How an IP address group is created. There are two options:                                                                                                                |                       |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | -  **Create new**: You need to enter IP address entries.                                                                                                                  |                       |
      |                                         | -  **Copy from another group**: You can copy all IP address entries from another IP address group to the current IP address group. Cross-region replication is supported. |                       |
      +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Region of IP Address Group to Be Copied | This parameter is mandatory if **Creation Method** is set to **Copy from another group**.                                                                                 | Region A              |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | Select the region where the IP address group to be copied is located from the drop-down list.                                                                             |                       |
      +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | IP Address Group to Be Copied           | This parameter is mandatory if **Creation Method** is set to **Copy from another group**.                                                                                 | ipGroup-B             |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | Select the IP address group to be copied from the drop-down list.                                                                                                         |                       |
      +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | IP Addresses                            | Optional                                                                                                                                                                  | 192.168.0.0/16        |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | Enter an IP address or IP address range on each line, and press **Enter**.                                                                                                | 192.168.10.10/32      |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | You can enter:                                                                                                                                                            |                       |
      |                                         |                                                                                                                                                                           |                       |
      |                                         | -  An IPv4 address range, for example, 192.168.0.0/16                                                                                                                     |                       |
      |                                         | -  A single IPv4 address, for example, 192.168.10.10/32                                                                                                                   |                       |
      |                                         | -  An IPv6 address range, for example, 2001:db8:a583:6e::/64                                                                                                              |                       |
      |                                         | -  A single IPv6 address, for example, 2001:db8:a583:6e::5c/128                                                                                                           |                       |
      +-----------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7. Click **Create Now**.

   The IP address group list is displayed. The status of the created IP address group is **Normal**.

   IP address groups need to be associated with resources. For example, if an IP address group is associated with a security group, the IP address group can be selected as the source or destination when you add a security group rule. For details, see :ref:`Associating an IP Address Group with a Security Group or Firewall <vpc_ipaddressgroup_0004>`.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865582865.png
