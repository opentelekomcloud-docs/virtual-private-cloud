:original_name: vpc_SecurityGroup_0005.html

.. _vpc_SecurityGroup_0005:

Modifying a Security Group Rule
===============================

Scenarios
---------

You can modify the port, protocol, and IP address of your security group rules as required to ensure the security of your instances.

.. caution::

   **Before modifying a security group rule, assess its impact to avoid network disruptions or security risks.**

   Do not modify in-use security group rules directly. Before you modify a security group rule that is in use, you can clone the security group and modify the rule in the test environment to ensure that the modified rule works. For details, see :ref:`Cloning a Security Group <vpc_securitygroup_0009>`.

Constraints
-----------

Security group rules work like a whitelist. If there are no rules that explicitly allow or deny certain traffic, the security group denies such traffic to or from the instances in the security group.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. In the security group list, click the name of the security group.

   The security group details page is displayed.

#. Click the **Inbound Rules** or **Outbound Rules** tab as required.

   The security group rule list is displayed.

#. Locate the row that contains the rule and click **Modify** in the **Operation** column.

#. Modify the security group rule information as prompted and click **Confirm**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818983190.png
