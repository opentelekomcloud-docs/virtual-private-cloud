:original_name: vpc_IPAddressGroup_0007.html

.. _vpc_IPAddressGroup_0007:

Adding IP Address Entries to an IP Address Group
================================================

Scenarios
---------

This section describes how to add IP address entries to an IP address group.

Constraints
-----------

If an IP address group has resources associated, adding IP addresses to the group may affect your network communications.

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

6. In the left corner above the IP address entry list, click **Add**.

   The dialog box for adding IP address entries is displayed.

7. Add IP address entries to the IP address group as prompted.

   .. table:: **Table 1** IP address group parameters

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                        | Example Value         |
      +=======================+====================================================================================================================================================================================================================================================+=======================+
      | Name                  | The name of the IP address group.                                                                                                                                                                                                                  | ipGroup-A             |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | IP Address Version    | IP address version supported by an IP address group. You can select an IP address version when you create an IP address group. IP address version cannot be modified after the IP address group is created. The supported versions are as follows: | IPv4                  |
      |                       |                                                                                                                                                                                                                                                    |                       |
      |                       | -  IPv4                                                                                                                                                                                                                                            |                       |
      |                       | -  IPv6                                                                                                                                                                                                                                            |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | IP Address Entries    | Mandatory                                                                                                                                                                                                                                          | 192.168.0.0/16        |
      |                       |                                                                                                                                                                                                                                                    |                       |
      |                       | Enter an IP address or IP address range on each line, and press **Enter**.                                                                                                                                                                         | 192.168.10.10/32      |
      |                       |                                                                                                                                                                                                                                                    |                       |
      |                       | You can enter:                                                                                                                                                                                                                                     |                       |
      |                       |                                                                                                                                                                                                                                                    |                       |
      |                       | -  An IPv4 address range, for example, 192.168.0.0/16                                                                                                                                                                                              |                       |
      |                       | -  A single IPv4 address, for example, 192.168.10.10/32                                                                                                                                                                                            |                       |
      |                       | -  An IPv6 address range, for example, 2001:db8:a583:6e::/64                                                                                                                                                                                       |                       |
      |                       | -  A single IPv6 address, for example, 2001:db8:a583:6e::5c/128                                                                                                                                                                                    |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823122.png
