:original_name: vpc_IPAddressGroup_0013.html

.. _vpc_IPAddressGroup_0013:

Modifying IP Address Entries in an IP Address Group
===================================================

Scenarios
---------

This section describes how to modify IP addresses, IP address ranges, and their descriptions in an IP address group.

Constraints
-----------

If an IP address group has resources associated, modifying IP addresses in an IP address group may affect your network communications.

If an IP address group has security groups associated, the rules associated with the IP address group will change.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

4. In the navigation pane on the left, choose **IP Address Groups**.

   The IP address group list is displayed.

5. In the IP address group list, click the hyperlink of the IP address group name.

   The basic information page of the IP address group is displayed.

6. In the left corner above the IP address entry list, click **Modify**.

   The dialog box for modifying an IP address entry is displayed.

7. Modify the information as prompted.

   For details, see :ref:`Table 1 <vpc_ipaddressgroup_0013__table761416533157>`.

   .. _vpc_ipaddressgroup_0013__table761416533157:

   .. table:: **Table 1** Parameters for modifying IP address entries

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                                        | Example Value                                |
      +=======================+====================================================================================================================================================================================================================================================+==============================================+
      | Name                  | The name of the IP address group.                                                                                                                                                                                                                  | ipGroup-A                                    |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+
      | IP Address Version    | IP address version supported by an IP address group. You can select an IP address version when you create an IP address group. IP address version cannot be modified after the IP address group is created. The supported versions are as follows: | IPv4                                         |
      |                       |                                                                                                                                                                                                                                                    |                                              |
      |                       | -  IPv4                                                                                                                                                                                                                                            |                                              |
      |                       | -  IPv6                                                                                                                                                                                                                                            |                                              |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+
      | IP Addresses          | You can modify existing IP addresses, IP address ranges, and their descriptions in an IP address group.                                                                                                                                            | -  Without description: 192.168.0.0/16       |
      |                       |                                                                                                                                                                                                                                                    | -  With description: 192.168.0.0/16 \| ECS01 |
      |                       | The format is "IP address|Description". Description is optional, can contain 0 to 255 characters, and cannot contain angle brackets (< or >). You can enter:                                                                                       |                                              |
      |                       |                                                                                                                                                                                                                                                    |                                              |
      |                       | -  An IPv4 address range, for example, 192.168.0.0/16 or 192.168.0.0/16 \| ECS01                                                                                                                                                                   |                                              |
      |                       | -  A single IPv4 address, for example, 192.168.10.10 or 192.168.10.10 \| ECS01                                                                                                                                                                     |                                              |
      |                       | -  An IPv6 address range, for example, 2001:db8:a583:6e::/64 or 2001:db8:a583:6e::/64 \| ECS01                                                                                                                                                     |                                              |
      |                       | -  A single IPv6 address, for example, 2001:db8:a583:6e::5c or 2001:db8:a583:6e::5c \| ECS01                                                                                                                                                       |                                              |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+

8. Click **OK**.

   The IP address list is displayed and you can view that the IP address entry was modified.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818983502.png
