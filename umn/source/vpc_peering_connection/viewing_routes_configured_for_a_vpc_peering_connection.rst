:original_name: vpc_peering_0004.html

.. _vpc_peering_0004:

Viewing Routes Configured for a VPC Peering Connection
======================================================

Scenarios
---------

This section describes how to view the routes added to the route tables of local and peer VPCs of a VPC peering connection.

-  :ref:`Viewing Routes of a VPC Peering Connection Between VPCs in the Same Account <vpc_peering_0004__section1865779319727>`
-  :ref:`Viewing Routes of a VPC Peering Connection Between VPCs in Different Accounts <vpc_peering_0004__section92403501475>`

If two VPCs cannot communicate through a VPC peering connection, you can check the routes added for the local and peer VPCs by following the instructions provided in this section.

.. _vpc_peering_0004__section1865779319727:

Viewing Routes of a VPC Peering Connection Between VPCs in the Same Account
---------------------------------------------------------------------------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Virtual Private Cloud** > **VPC Peering Connections**.

   The VPC peering connection list is displayed.

5. In the VPC peering connection list, click the name of the target VPC peering connection.

   The page showing the VPC peering connection details is displayed.

6. View the routes added for the VPC peering connection:

   a. Click the **Local Routes** tab to view the local route added for the VPC peering connection.
   b. Click the **Peer Routes** tab to view the peer route added for the VPC peering connection.

.. _vpc_peering_0004__section92403501475:

Viewing Routes of a VPC Peering Connection Between VPCs in Different Accounts
-----------------------------------------------------------------------------

Only the account owner of a VPC in a VPC peering connection can view the routes added for the connection.

#. .. _vpc_peering_0004__li4105938135810:

   Log in to the management console using the account of the local VPC and view the route of the local VPC:

   a. Click |image3| in the upper left corner and select the desired region and project.

   b. Click |image4| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

      The **Virtual Private Cloud** page is displayed.

   c. In the navigation pane on the left, choose **Virtual Private Cloud** > **VPC Peering Connections**.

      The VPC peering connection list is displayed.

   d. In the VPC peering connection list, click the name of the target VPC peering connection.

      The page showing the VPC peering connection details is displayed.

   e. Click the **Local Routes** tab to view the local route added for the VPC peering connection.

#. Log in to the management console using the account of the peer VPC and view the route of the peer VPC by referring to :ref:`1 <vpc_peering_0004__li4105938135810>`.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865662765.png
.. |image3| image:: /_static/images/en-us_image_0000001818982734.png
.. |image4| image:: /_static/images/en-us_image_0000001818982826.png
