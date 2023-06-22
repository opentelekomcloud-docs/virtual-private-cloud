:original_name: SecurityGroup_0017.html

.. _SecurityGroup_0017:

Adding Instances to and Removing Them from a Security Group
===========================================================

Scenarios
---------

After a security group is created, you can add instances to the security group to protect the instances. You can also remove them from the security group as required.

You can add multiple instances to or remove them from a security group.

Adding Instances to a Security Group
------------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.
#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.
#. On the **Security Groups** page, click **Manage Instance** in the **Operation** column.
#. On the **Servers** tab, click **Add** and add one or more servers to the current security group.
#. On the **Extension NICs** tab, click **Add** and add one or more extension NICs to the current security group.
#. Click **OK**.

Removing Instances from a Security Group
----------------------------------------

#. Log in to the management console.
#. Click |image3| in the upper left corner and select the desired region and project.
#. Click |image4| in the upper left corner and choose **Network** > **Virtual Private Cloud**.
#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.
#. On the **Security Groups** page, click **Manage Instance** in the **Operation** column.
#. On the **Servers** tab, locate the target server and click **Remove** in the **Operation** column to remove the server from current security group.
#. On the **Extension NICs** tab, locate the target extension NIC and click **Remove** in the **Operation** column to remove the NIC from the current security group.
#. Click **Yes**.

**Removing multiple instances from a security group**

-  Select multiple servers and click **Remove** above the server list to remove the selected servers from the current security group all at once.
-  Select multiple extension NICs and click **Remove** above the extension NIC list to remove the selected extension NICs from the current security group all at once.

Follow-Up Operations
--------------------

You can delete the security groups that you no longer need. Deleting a security group will also delete all security group rules in the security group. For details, see :ref:`Deleting a Security Group <vpc_securitygroup_0008>`.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001500905066.png
.. |image3| image:: /_static/images/en-us_image_0141273034.png
.. |image4| image:: /_static/images/en-us_image_0000001500905066.png
