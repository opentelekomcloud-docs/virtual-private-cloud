:original_name: vpc_vip_0009.html

.. _vpc_vip_0009:

Releasing a Virtual IP Address
==============================

Scenarios
---------

If you no longer need a virtual IP address or a reserved virtual IP address, you can release it to avoid wasting resources.

Prerequisites
-------------

Before deleting a virtual IP address, ensure that the virtual IP address has been unbound from the following resources:

-  ECS
-  EIP
-  CCE cluster

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.
3. On the console homepage, under **Network**, click **Virtual Private Cloud**.

4. In the navigation pane on the left, click **Virtual Private Cloud**.
5. On the **Virtual Private Cloud** page, locate the VPC containing the subnet from which a virtual IP address is to be released, and click the VPC name.
6. On the **Subnets** tab, click the name of the subnet from which a virtual IP address is to be released.
7. Click the **Virtual IP Addresses** tab, locate the row that contains the virtual IP address to be released, click **More** in the **Operation** column, and select **Release**.
8. Click **Yes** in the displayed dialog box.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
