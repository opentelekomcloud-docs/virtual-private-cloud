:original_name: vpc_acl_0013.html

.. _vpc_acl_0013:

Managing Firewall Tags
======================

Scenarios
---------

Tags help you identify, classify, and search for firewalls.

For details about tag key and value requirements, see :ref:`Table 1 <vpc_acl_0013__table126332192572>`.

.. _vpc_acl_0013__table126332192572:

.. table:: **Table 1** Requirements of firewall tag keys and values

   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Requirement                                                                                      | Example Value         |
   +=======================+==================================================================================================+=======================+
   | Key                   | -  For each resource, each tag key must be unique, and each tag key can only have one tag value. | test                  |
   |                       | -  Cannot be left blank.                                                                         |                       |
   |                       | -  Can contain a maximum of 128 characters.                                                      |                       |
   |                       | -  Cannot start or end with a space.                                                             |                       |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------+
   | Value                 | -  Can be left blank.                                                                            | 01                    |
   |                       | -  Can contain a maximum of 255 characters.                                                      |                       |
   |                       | -  Cannot start or end with a space.                                                             |                       |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------+

Constraints
-----------

Each cloud resource can have up to 20 tags.

Procedure
---------

**Search for subnets by tag key or value on the subnet list page.**

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. In the upper left corner of the page, click |image2| to expand the service list and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

#. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

   The firewall list page is displayed.

#. In the search box above the firewall list, click anywhere in the search box.

   Click the tag key and then the value as required. The system filters resources based on the tag you select.

   Click anywhere in the search box to add the next tag key and value.

   You can add multiple tag keys and values to refine your search results. If you add more than one tag to search for VPCs, the VPCs containing all specified tags will be displayed.

**Add, delete, edit, and view tags on the Tags tab of a firewall.**

#. Log in to the management console.

#. Click |image3| in the upper left corner and select the desired region and project.

#. In the upper left corner of the page, click |image4| to expand the service list and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

#. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

   The firewall list page is displayed.

#. In the firewall list, click the name of the firewall to be queried.

#. Click the **Tags** tab and then click **Edit Tag** in the upper left corner above the tag list.

   The **Edit Tag** page is displayed.

#. Perform the following operations on the tags as required:

   -  Adding a tag: Click |image5|, enter a tag key and value, and click **OK**.
   -  Modifying a tag: Click |image6| next to the target tag key or value to delete the original value, enter a new value, and click **OK**.
   -  Deleting a tag: Click **Delete** next to the target tag and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002555846085.png
.. |image2| image:: /_static/images/en-us_image_0000002555686117.png
.. |image3| image:: /_static/images/en-us_image_0000002524606206.png
.. |image4| image:: /_static/images/en-us_image_0000002524766160.png
.. |image5| image:: /_static/images/en-us_image_0000002555651817.png
.. |image6| image:: /_static/images/en-us_image_0000002555531839.png
