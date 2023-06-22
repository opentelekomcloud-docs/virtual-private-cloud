:original_name: vpc_SecurityGroup_0009.html

.. _vpc_SecurityGroup_0009:

Cloning a Security Group
========================

Scenarios
---------

You can clone a security group from one region to another to quickly apply the security group rules to ECSs in another region.

You can clone a security group in the following scenarios:

-  For example, you have security group **sg-A** in region A. If ECSs in region B require the same security group rules as those configured for security group **sg-A**, you can clone security group **sg-A** to region B, freeing you from creating a new security group in region B.
-  If you need new security group rules, you can clone the original security group as a backup.

   .. note::

      Security group cloning is not supported now.

Notes and Constraints
---------------------

If you clone security group across regions, the system will clone only rules whose source and destination are CIDR blocks or are in the current security group.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

#. On the **Security Groups** page, locate the row that contains the target security group and choose **More** > **Clone** in the **Operation** column.

#. Set required parameters as prompted.


   .. figure:: /_static/images/en-us_image_0000001602035305.png
      :alt: **Figure 1** Clone Security Group

      **Figure 1** Clone Security Group

#. Click **OK**. You can then switch to the required region to view the cloned security group in the security group list.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001500905066.png
