:original_name: vpc_mirror_12.html

.. _vpc_mirror_12:

Creating a Mirror Session
=========================

Scenarios
---------

To use Traffic Mirroring, you need to create a mirror session, associate a mirror filter, multiple mirror sources, and a mirror target with the mirror session. A mirror session mirrors traffic from a mirror source to a mirror target that meets the mirror filter.

For details about mirror sessions, see :ref:`Traffic Mirroring Overview <vpc_mirror_02>`.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the region and project.

3.  Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

    The **Virtual Private Cloud** page is displayed.

4.  In the navigation pane on the left, choose **Traffic Mirroring** > **Mirror Sessions**.

    The **Mirror Sessions** page is displayed.

5.  In the upper right corner of the mirror session list, click **Create Mirror Session**.

    The **Create Mirror Session** page is displayed.

6.  Set basic information about the mirror session as prompted.

    .. table:: **Table 1** Parameters for configuring basic information about a mirror session

       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Parameter             | Description                                                                                                                                                   | Example Value         |
       +=======================+===============================================================================================================================================================+=======================+
       | Name                  | Mandatory                                                                                                                                                     | mirror-session-01     |
       |                       |                                                                                                                                                               |                       |
       |                       | Enter the name of the mirror session. The name:                                                                                                               |                       |
       |                       |                                                                                                                                                               |                       |
       |                       | -  Must contain 1 to 64 characters.                                                                                                                           |                       |
       |                       | -  Can contain letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                |                       |
       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Priority              | Mandatory                                                                                                                                                     | 1                     |
       |                       |                                                                                                                                                               |                       |
       |                       | Priority of the mirror session.                                                                                                                               |                       |
       |                       |                                                                                                                                                               |                       |
       |                       | -  A priority value can be from 1 to 32766. A smaller value indicates a higher priority.                                                                      |                       |
       |                       | -  Priorities must be unique for each mirror session of the same account in a region.                                                                         |                       |
       |                       |                                                                                                                                                               |                       |
       |                       | A mirror source can be associated with multiple mirror sessions at the same time. The mirror sessions are matched from the lowest value to the highest value. |                       |
       |                       |                                                                                                                                                               |                       |
       |                       | For details, see :ref:`the matching process of mirror sessions <vpc_mirror_02__en-us_topic_0000001651378981_li167114161324>`.                                 |                       |
       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | VNI                   | Optional                                                                                                                                                      | 1                     |
       |                       |                                                                                                                                                               |                       |
       |                       | VXLAN Network Identifiers (VNIs) are used to distinguish different mirror sessions for a mirror target. A VNI can be from 0 to 16777215.                      |                       |
       |                       |                                                                                                                                                               |                       |
       |                       | If not specified, the default value is 1.                                                                                                                     |                       |
       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Packet Length         | Optional                                                                                                                                                      | 96                    |
       |                       |                                                                                                                                                               |                       |
       |                       | The number of bytes that meet the mirror filter and will be mirrored. The value can be from 1 to 1460.                                                        |                       |
       |                       |                                                                                                                                                               |                       |
       |                       | If not specified, the default value is 96.                                                                                                                    |                       |
       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Mirror Session        | Optional                                                                                                                                                      | Enable                |
       |                       |                                                                                                                                                               |                       |
       |                       | -  If the mirror session is disabled, traffic of mirror sources cannot be monitored.                                                                          |                       |
       |                       | -  If the mirror session is enabled, traffic of mirror sources can be monitored.                                                                              |                       |
       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
       | Description           | Optional                                                                                                                                                      | ``-``                 |
       |                       |                                                                                                                                                               |                       |
       |                       | Enter the description of the mirror session in the text box as required.                                                                                      |                       |
       +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7.  Click **Next**.

    The **Associate Mirror Filter** page is displayed.

8.  In the mirror filter list, select a mirror filter.

    Each mirror session can be associated with only one mirror filter.

    If there is no mirror filter you want, create one by referring to :ref:`Creating a Mirror Filter <vpc_mirror_04>`.

9.  Click **Next**.

    The **Associate Mirror Sources** page is displayed.

10. In the mirror source list, select mirror sources.

    When associating mirror sources with a mirror session, learn about the constraints on mirror sources in :ref:`Table 5 <vpc_mirror_02__en-us_topic_0000001651378981_table553191774316>`.

11. Click **Next**.

    The **Associate Mirror Target** page is displayed.

12. In the mirror target list, select a mirror target.

    -  A mirror target is a network interface of an ECS or a load balancer, which is used to receive mirrored traffic.

    -  Each mirror session can be associated with only one mirror target.

       For details about the constraints on mirror targets, see :ref:`Table 6 <vpc_mirror_02__en-us_topic_0000001651378981_table66725225618>`.

13. Click **Next**.

    The **Confirm** page is displayed.

14. After confirming that the configuration is correct, click **Create Now**.

    You can view the created mirror session in the mirror session list.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000002581428242.png
