:original_name: SecurityGroup_0006.html

.. _SecurityGroup_0006:

Changing the Security Group of an ECS
=====================================

Scenarios
---------

Change the security group associated with an ECS NIC.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select your region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the ECS list, locate the row that contains the target ECS. Click **More** in the **Operation** column and select **Manage Network** > **Change Security Group**.

   The **Change Security Group** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0162733894.png
      :alt: **Figure 1** Change Security Group

      **Figure 1** Change Security Group

#. Select the target NIC and security groups.

   You can select multiple security groups. In such a case, the rules of all the selected security groups will be aggregated to apply on the ECS.

   To create a security group, click **Create Security Group**.

   .. note::

      Using multiple security groups may deteriorate ECS network performance. You are suggested to select no more than five security groups.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0093507575.png
