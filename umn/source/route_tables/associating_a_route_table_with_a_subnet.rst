:original_name: vpc_route01_0007.html

.. _vpc_route01_0007:

Associating a Route Table with a Subnet
=======================================

Scenarios
---------

After a route table is associated with a subnet, its routes control the routing for the subnet and apply to all cloud resources in the subnet.

Notes and Constraints
---------------------

A subnet can only be associated with one route table.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

4. In the navigation pane on the left, choose **Virtual Private Cloud** > **Route Tables**.

5. In the route table list, locate the row that contains the target route table and click **Associate Subnet** in the **Operation** column.

6. Select the subnet to be associated.


   .. figure:: /_static/images/en-us_image_0000001540846821.png
      :alt: **Figure 1** Associate Subnet

      **Figure 1** Associate Subnet

7. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001500905066.png
