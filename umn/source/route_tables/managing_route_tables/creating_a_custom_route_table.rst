:original_name: vpc_route01_0005.html

.. _vpc_route01_0005:

Creating a Custom Route Table
=============================

Scenarios
---------

A VPC automatically comes with a default route table. If the default route table cannot meet your service requirements, you can create a custom route table with required rules and associate subnets with it to control traffic in and out of the subnets. The detailed operations are as follows:

-  :ref:`Step 1: Create a Custom Route Table and Associate Subnets with It <vpc_route01_0005__en-us_topic_0212076960_section1413101810288>`
-  :ref:`Step 2: Add Routes to the Custom Route Table <vpc_route01_0005__section3894133913464>`

Constraints
-----------

By default, each VPC can have up to 10 route tables, including the default route table.

.. _vpc_route01_0005__en-us_topic_0212076960_section1413101810288:

Step 1: Create a Custom Route Table and Associate Subnets with It
-----------------------------------------------------------------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

4. In the navigation pane on the left, choose **Virtual Private Cloud** > **Route Tables**.

5. In the upper right corner, click **Create Route Table**. On the displayed page, configure parameters as prompted.


   .. figure:: /_static/images/en-us_image_0000002065082501.png
      :alt: **Figure 1** Create Route Table

      **Figure 1** Create Route Table

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                           | Example Value         |
      +=======================+=======================================================================================================================================================================+=======================+
      | Name                  | The name of the route table. This parameter is mandatory.                                                                                                             | rtb-001               |
      |                       |                                                                                                                                                                       |                       |
      |                       | The name can contain a maximum of 64 characters, which can consist of letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot contain spaces. |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | VPC                   | The VPC that the route table belongs to. This parameter is mandatory.                                                                                                 | vpc-001               |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the route table. This parameter is optional.                                                                                          | ``-``                 |
      |                       |                                                                                                                                                                       |                       |
      |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                   |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Route Settings        | The route information. This parameter is optional.                                                                                                                    | ``-``                 |
      |                       |                                                                                                                                                                       |                       |
      |                       | You can add a route when creating the route table or after the route table is created. For details, see :ref:`Adding a Custom Route <vpc_route01_0006>`.              |                       |
      |                       |                                                                                                                                                                       |                       |
      |                       | You can click **+** to add more routes.                                                                                                                               |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

6. Click **OK**.

   A message is displayed. You can determine whether to associate the route table with subnets immediately as prompted. If you want to associate immediately, perform the following operations:

   a. Click **Associate Subnet**. The route table details page is displayed.
   b. Click **Associate Subnet** and select the target subnets to be associated.
   c. Click **OK**.

.. _vpc_route01_0005__section3894133913464:

Step 2: Add Routes to the Custom Route Table
--------------------------------------------

Each route table comes with default routes to allow instances in a subnet to access public services on the cloud or to allow different subnets in a VPC to communicate with each other. You can also add custom routes as required to control the traffic in and out of the subnets. For details, see :ref:`Adding a Custom Route <vpc_route01_0006>`.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823254.png
