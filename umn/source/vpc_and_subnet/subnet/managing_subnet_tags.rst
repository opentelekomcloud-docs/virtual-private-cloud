:original_name: vpc_vpc_0005.html

.. _vpc_vpc_0005:

Managing Subnet Tags
====================

Scenarios
---------

A subnet tag identifies a subnet. Tags can be added to subnets to facilitate subnet identification and administration. You can add a tag to a subnet when creating the subnet, or you can add a tag to a created subnet on the subnet details page. A maximum of 20 tags can be added to each subnet.

A tag consists of a key and value pair. :ref:`Table 1 <vpc_vpc_0005__ted9687ca14074ef785241145365a6175>` lists the tag key and value requirements.

.. _vpc_vpc_0005__ted9687ca14074ef785241145365a6175:

.. table:: **Table 1** Subnet tag key and value requirements

   +-----------------------+---------------------------------------------------------------------+-----------------------+
   | Parameter             | Requirements                                                        | Example Value         |
   +=======================+=====================================================================+=======================+
   | Key                   | -  Cannot be left blank.                                            | subnet_key1           |
   |                       | -  Must be unique for each subnet.                                  |                       |
   |                       | -  Can contain a maximum of 36 characters.                          |                       |
   |                       | -  Can contain only the following character types:                  |                       |
   |                       |                                                                     |                       |
   |                       |    -  Uppercase letters                                             |                       |
   |                       |    -  Lowercase letters                                             |                       |
   |                       |    -  Digits                                                        |                       |
   |                       |    -  Special characters, including hyphens (-) and underscores (_) |                       |
   +-----------------------+---------------------------------------------------------------------+-----------------------+
   | Value                 | -  Can contain a maximum of 43 characters.                          | subnet-01             |
   |                       | -  Can contain only the following character types:                  |                       |
   |                       |                                                                     |                       |
   |                       |    -  Uppercase letters                                             |                       |
   |                       |    -  Lowercase letters                                             |                       |
   |                       |    -  Digits                                                        |                       |
   |                       |    -  Special characters, including hyphens (-) and underscores (_) |                       |
   +-----------------------+---------------------------------------------------------------------+-----------------------+

Procedure
---------

**Search for subnets by tag key and value on the page showing the subnet list.**

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Subnets**.

   The **Subnets** page is displayed.

#. In the upper right corner of the subnet list, click **Search by Tag**.

#. Enter the tag key of the subnet to be queried.

   Both the tag key and value must be specified. The system automatically displays the subnets you are looking for if both the tag key and value are matched.

#. Click **+** to add another tag key and value.

   You can add multiple tag keys and values to refine your search results. If you add more than one tag to search for subnets, the subnets containing all specified tags will be displayed.

#. Click **Search**.

   The system displays the subnets you are looking for based on the entered tag keys and values.

**Add, delete, edit, and view tags on the Tags tab of a subnet.**

#. Log in to the management console.

#. Click |image3| in the upper left corner and select the desired region and project.

#. Click |image4| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Subnets**.

   The **Subnets** page is displayed.

#. In the subnet list, locate the target subnet and click its name.

#. On the subnet details page, click the **Tags** tab and perform desired operations on tags.

   -  View tags.

      On the **Tags** tab, you can view details about tags added to the current subnet, including the number of tags and the key and value of each tag.

   -  Add a tag.

      Click **Add Tag** in the upper left corner. In the displayed **Add Tag** dialog box, enter the tag key and value, and click **OK**.

   -  Edit a tag.

      Locate the row that contains the tag you want to edit, and click **Edit** in the **Operation** column. Enter the new tag key and value, and click **OK**.

   -  Delete a tag.

      Locate the row that contains the tag you want to delete, and click **Delete** in the **Operation** column. In the displayed dialog box, click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001500905066.png
.. |image3| image:: /_static/images/en-us_image_0141273034.png
.. |image4| image:: /_static/images/en-us_image_0000001500905066.png