:original_name: vpc_vpc_0005.html

.. _vpc_vpc_0005:

Managing Subnet Tags
====================

Scenarios
---------

You can add tags to subnets to help you identify and organize them.

You can add a tag to a subnet when creating the subnet, or you can add a tag to a created subnet on the subnet details page. A maximum of 20 tags can be added to each subnet.

A tag consists of a key and value pair. :ref:`Table 1 <vpc_vpc_0005__ted9687ca14074ef785241145365a6175>` lists the tag key and value requirements.

.. _vpc_vpc_0005__ted9687ca14074ef785241145365a6175:

.. table:: **Table 1** Subnet tag key and value requirements

   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Requirements                                                                                     | Example Value         |
   +=======================+==================================================================================================+=======================+
   | Key                   | -  For each resource, each tag key must be unique, and each tag key can only have one tag value. | subnet_key1           |
   |                       | -  Cannot be left blank.                                                                         |                       |
   |                       | -  Can contain a maximum of 128 characters.                                                      |                       |
   |                       | -  Cannot start or end with a space.                                                             |                       |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------+
   | Value                 | -  Can be left blank.                                                                            | subnet-01             |
   |                       | -  Can contain a maximum of 255 characters.                                                      |                       |
   |                       | -  Cannot start or end with a space.                                                             |                       |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------+

Procedure
---------

**Search for subnets by tag key or value on the subnet list page.**

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Subnets**.

   The subnet list page is displayed.

#. Click the search box above the subnet list.

   Click the tag key and then the value as required. The system filters resources based on the tag you select.

   Click anywhere in the search box to add the next tag key and value.

   You can add multiple tag keys and values to refine your search results. If you add more than one tag to search for VPCs, the VPCs containing all specified tags will be displayed.

**Add, delete, edit, and view tags on the Tags tab of a subnet.**

#. Log in to the management console.

#. Click |image3| in the upper left corner and select the desired region and project.

#. Click |image4| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Subnets**.

   The subnet list page is displayed.

#. In the subnet list, locate the target subnet and click its name.

#. Click the **Tags** tab and then click **Edit Tag** in the upper left corner above the tag list.

   The **Edit Tag** page is displayed.

#. Perform the following operations on the tags as required:

   -  Adding a tag: Click |image5|, enter a tag key and value, and click **OK**.
   -  Modifying a tag: Click |image6| next to the target tag key or value to delete the original value, enter a new value, and click **OK**.
   -  Deleting a tag: Click **Delete** next to the target tag and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818983406.png
.. |image3| image:: /_static/images/en-us_image_0000001818982734.png
.. |image4| image:: /_static/images/en-us_image_0000001865583165.png
.. |image5| image:: /_static/images/en-us_image_0000002555651817.png
.. |image6| image:: /_static/images/en-us_image_0000002555531839.png
