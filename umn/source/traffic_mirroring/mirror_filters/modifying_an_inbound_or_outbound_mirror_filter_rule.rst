:original_name: vpc_mirror_06.html

.. _vpc_mirror_06:

Modifying an Inbound or Outbound Mirror Filter Rule
===================================================

Scenarios
---------

You can modify inbound and outbound rules of a mirror filter.

-  Inbound rules match the traffic received by a mirror source.
-  Outbound rules match the traffic sent by a mirror source.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Traffic Mirroring** > **Mirror Filters**.

   The mirror filter list page is displayed.

5. Locate the target mirror filter and click the number in the **Inbound and Outbound Rules** column.

   The **Inbound Rules** tab page is displayed.

6. In the inbound rule list, locate the target rule and click **Modify** in the **Operation** column.

   .. table:: **Table 1** Inbound rule parameter description

      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter              | Description                                                                                                                                  | Example Value         |
      +========================+==============================================================================================================================================+=======================+
      | Priority               | Priority of a mirror filter rule.                                                                                                            | 1                     |
      |                        |                                                                                                                                              |                       |
      |                        | -  A priority value can be from 1 to 65535. A smaller value indicates a higher priority.                                                     |                       |
      |                        | -  Priorities of inbound rules must be unique for each mirror filter.                                                                        |                       |
      |                        |                                                                                                                                              |                       |
      |                        | A mirror filter can contain multiple rules and the rules are matched in ascending order of priority.                                         |                       |
      |                        |                                                                                                                                              |                       |
      |                        | For details, see :ref:`the matching process of mirror filter rules <vpc_mirror_02__en-us_topic_0000001651378981_li5449543173013>`.           |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Protocol               | Select a network protocol.                                                                                                                   | TCP                   |
      |                        |                                                                                                                                              |                       |
      |                        | -  If you select TCP, you can customize the source and destination port ranges.                                                              |                       |
      |                        | -  If you select UDP, you can customize the source and destination port ranges.                                                              |                       |
      |                        | -  If you set **Type** to **IPv4** and select ICMP, all ports are specified for source and destination port ranges by default.               |                       |
      |                        | -  If you set **Type** to **IPv6** and select ICMPv6, all ports are specified for source and destination port ranges by default.             |                       |
      |                        | -  If you select **All**, all network protocols are supported and all ports are specified for source and destination port ranges by default. |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Action                 | Whether to accept or reject inbound traffic of a mirror source.                                                                              | Accept                |
      |                        |                                                                                                                                              |                       |
      |                        | -  If you set **Action** to **Accept**, the traffic will be mirrored to the mirror target.                                                   |                       |
      |                        | -  If you set **Action** to **Reject**, the traffic will not be mirrored to the mirror target.                                               |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Type                   | IP address version of inbound traffic. You can specify:                                                                                      | IPv4                  |
      |                        |                                                                                                                                              |                       |
      |                        | -  **IPv4**                                                                                                                                  |                       |
      |                        | -  **IPv6**                                                                                                                                  |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source                 | Source of inbound traffic. You can enter:                                                                                                    | 10.0.0.0/24           |
      |                        |                                                                                                                                              |                       |
      |                        | -  A single IP address: IP address/mask                                                                                                      |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv4 address: 192.168.10.10/32                                                                                                    |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv6 address: 2002:50::44/128                                                                                                     |                       |
      |                        |                                                                                                                                              |                       |
      |                        | -  An IP address range in CIDR notation: IP address/mask                                                                                     |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv4 address range: 192.168.52.0/24                                                                                               |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv6 address range: 2407:c080:802:469::/64                                                                                        |                       |
      |                        |                                                                                                                                              |                       |
      |                        | -  All IP addresses                                                                                                                          |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    0.0.0.0/0 represents all IPv4 addresses.                                                                                                  |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    ::/0 represents all IPv6 addresses.                                                                                                       |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source Port Range      | Source port range of inbound traffic.                                                                                                        | 22-23                 |
      |                        |                                                                                                                                              |                       |
      |                        | -  Port range: 1 to 65535                                                                                                                    |                       |
      |                        | -  Use a hyphen (-) to connect the start port and the end port, for example, 22-23. The end port cannot be smaller than the start port.      |                       |
      |                        | -  If not specified or **1-65535** is specified, all ports are used.                                                                         |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination            | Destination of inbound traffic. You can enter:                                                                                               | 0.0.0.0/0             |
      |                        |                                                                                                                                              |                       |
      |                        | -  A single IP address: IP address/mask                                                                                                      |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv4 address: 192.168.10.10/32                                                                                                    |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv6 address: 2002:50::44/128                                                                                                     |                       |
      |                        |                                                                                                                                              |                       |
      |                        | -  An IP address range in CIDR notation: IP address/mask                                                                                     |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv4 address range: 192.168.52.0/24                                                                                               |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv6 address range: 2407:c080:802:469::/64                                                                                        |                       |
      |                        |                                                                                                                                              |                       |
      |                        | -  All IP addresses                                                                                                                          |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    0.0.0.0/0 represents all IPv4 addresses.                                                                                                  |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    ::/0 represents all IPv6 addresses.                                                                                                       |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination Port Range | Destination port range of inbound traffic.                                                                                                   | 1-65535               |
      |                        |                                                                                                                                              |                       |
      |                        | -  Port range: 1 to 65535                                                                                                                    |                       |
      |                        | -  Use a hyphen (-) to connect the start port and the end port, for example, 22-23. The end port cannot be smaller than the start port.      |                       |
      |                        | -  If not specified or **1-65535** is specified, all ports are used.                                                                         |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description            | Enter the description of the mirror filter rule in the text box as required.                                                                 | ``-``                 |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7. Click **OK**.

   You can view the modified inbound rule in the list.

8. On the **Outbound Rules** tab page, locate the row that contains the rule in the outbound rule list and click **Modify** in the **Operation** column.

   .. table:: **Table 2** Outbound rule parameter description

      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter              | Description                                                                                                                                  | Example Value         |
      +========================+==============================================================================================================================================+=======================+
      | Priority               | Priority of a mirror filter rule.                                                                                                            | 1                     |
      |                        |                                                                                                                                              |                       |
      |                        | -  A priority value can be from 1 to 65535. A smaller value indicates a higher priority.                                                     |                       |
      |                        | -  Priorities of inbound rules must be unique for each mirror filter.                                                                        |                       |
      |                        |                                                                                                                                              |                       |
      |                        | A mirror filter can contain multiple rules and the rules are matched in ascending order of priority.                                         |                       |
      |                        |                                                                                                                                              |                       |
      |                        | For details, see :ref:`the matching process of mirror filter rules <vpc_mirror_02__en-us_topic_0000001651378981_li5449543173013>`.           |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Protocol               | Select a network protocol.                                                                                                                   | All                   |
      |                        |                                                                                                                                              |                       |
      |                        | -  If you select TCP, you can customize the source and destination port ranges.                                                              |                       |
      |                        | -  If you select UDP, you can customize the source and destination port ranges.                                                              |                       |
      |                        | -  If you set **Type** to **IPv4** and select ICMP, all ports are specified for source and destination port ranges by default.               |                       |
      |                        | -  If you set **Type** to **IPv6** and select ICMPv6, all ports are specified for source and destination port ranges by default.             |                       |
      |                        | -  If you select **All**, all network protocols are supported and all ports are specified for source and destination port ranges by default. |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Action                 | Whether to accept or reject outbound traffic of a mirror source.                                                                             | Reject                |
      |                        |                                                                                                                                              |                       |
      |                        | -  If you set **Action** to **Accept**, the traffic will be mirrored to the mirror target.                                                   |                       |
      |                        | -  If you set **Action** to **Reject**, the traffic will not be mirrored to the mirror target.                                               |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Type                   | IP address version of outbound traffic. You can specify:                                                                                     | IPv4                  |
      |                        |                                                                                                                                              |                       |
      |                        | -  **IPv4**                                                                                                                                  |                       |
      |                        | -  **IPv6**                                                                                                                                  |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source                 | Source of outbound traffic. You can enter:                                                                                                   | 192.168.0.0/24        |
      |                        |                                                                                                                                              |                       |
      |                        | -  A single IP address: IP address/mask                                                                                                      |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv4 address: 192.168.10.10/32                                                                                                    |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv6 address: 2002:50::44/128                                                                                                     |                       |
      |                        |                                                                                                                                              |                       |
      |                        | -  An IP address range in CIDR notation: IP address/mask                                                                                     |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv4 address range: 192.168.52.0/24                                                                                               |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv6 address range: 2407:c080:802:469::/64                                                                                        |                       |
      |                        |                                                                                                                                              |                       |
      |                        | -  All IP addresses                                                                                                                          |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    0.0.0.0/0 represents all IPv4 addresses.                                                                                                  |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    ::/0 represents all IPv6 addresses.                                                                                                       |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source Port Range      | Source port range of outbound traffic.                                                                                                       | All                   |
      |                        |                                                                                                                                              |                       |
      |                        | -  Port range: 1 to 65535                                                                                                                    |                       |
      |                        | -  Use a hyphen (-) to connect the start port and the end port, for example, 22-23. The end port cannot be smaller than the start port.      |                       |
      |                        | -  If not specified or **1-65535** is specified, all ports are used.                                                                         |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination            | Destination of outbound traffic. You can enter:                                                                                              | 10.2.0.0/24           |
      |                        |                                                                                                                                              |                       |
      |                        | -  A single IP address: IP address/mask                                                                                                      |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv4 address: 192.168.10.10/32                                                                                                    |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv6 address: 2002:50::44/128                                                                                                     |                       |
      |                        |                                                                                                                                              |                       |
      |                        | -  An IP address range in CIDR notation: IP address/mask                                                                                     |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv4 address range: 192.168.52.0/24                                                                                               |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    Example IPv6 address range: 2407:c080:802:469::/64                                                                                        |                       |
      |                        |                                                                                                                                              |                       |
      |                        | -  All IP addresses                                                                                                                          |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    0.0.0.0/0 represents all IPv4 addresses.                                                                                                  |                       |
      |                        |                                                                                                                                              |                       |
      |                        |    ::/0 represents all IPv6 addresses.                                                                                                       |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Destination Port Range | Destination port range of outbound traffic.                                                                                                  | All                   |
      |                        |                                                                                                                                              |                       |
      |                        | -  Port range: 1 to 65535                                                                                                                    |                       |
      |                        | -  Use a hyphen (-) to connect the start port and the end port, for example, 22-23. The end port cannot be smaller than the start port.      |                       |
      |                        | -  If not specified or **1-65535** is specified, all ports are used.                                                                         |                       |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description            | Enter the description of the mirror filter rule in the text box as required.                                                                 | ``-``                 |
      +------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

9. Click **OK**.

   You can view the modified outbound rule in the list.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000002611828083.png
