:original_name: vpc_peering_0006.html

.. _vpc_peering_0006:

Deleting Routes Configured for a VPC Peering Connection
=======================================================

Scenarios
---------

This section describes how to delete routes from the route tables of the local and peer VPCs connected by a VPC peering connection.

-  :ref:`Deleting Routes of a VPC Peering Connection Between VPCs in the Same Account <vpc_peering_0006__section26541722111813>`
-  :ref:`Deleting Routes of a VPC Peering Connection Between VPCs in Different Accounts <vpc_peering_0006__section47866392497>`

.. _vpc_peering_0006__section26541722111813:

Deleting Routes of a VPC Peering Connection Between VPCs in the Same Account
----------------------------------------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **VPC Peering Connections**.

   The VPC peering connection list is displayed.

#. In the VPC peering connection list, click the name of the target VPC peering connection.

   The page showing the VPC peering connection details is displayed.

#. Delete the route added to the route table of the local VPC:

   a. Click the **Local Routes** tab and then click the **Route Tables** hyperlink.

      The **Summary** tab of the default route table for the local VPC is displayed.

   b. Locate the row that contains the route to be deleted and click **Delete** in the **Operation** column.

      A confirmation dialog box is displayed.

   c. Click **Yes**.

#. Delete the route added to the route table of the peer VPC:

   a. Click the **Peer Routes** tab and then click the **Route Tables** hyperlink.

      The **Summary** tab of the default route table for the peer VPC is displayed.

   b. Locate the row that contains the route to be deleted and click **Delete** in the **Operation** column.

      A confirmation dialog box is displayed.

   c. Click **Yes**.

.. _vpc_peering_0006__section47866392497:

Deleting Routes of a VPC Peering Connection Between VPCs in Different Accounts
------------------------------------------------------------------------------

Only the account owner of a VPC in a VPC peering connection can delete the routes added for the connection.

#. .. _vpc_peering_0006__li4105938135810:

   Log in to the management console using the account of the local VPC and delete the route of the local VPC:

   a. Click |image3| in the upper left corner and select the desired region and project.

   b. Click |image4| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   c. In the navigation pane on the left, choose **Virtual Private Cloud** > **VPC Peering Connections**.

      The VPC peering connection list is displayed.

   d. In the VPC peering connection list, click the name of the target VPC peering connection.

      The page showing the VPC peering connection details is displayed.

   e. Delete the route added to the route table of the local VPC:

      #. Click the **Local Routes** tab and then click the **Route Tables** hyperlink.

         The **Summary** tab of the default route table for the local VPC is displayed.

      #. Locate the row that contains the route to be deleted and click **Delete** in the **Operation** column.

         A confirmation dialog box is displayed.

      #. Click **Yes**.

#. Log in to the management console using the account of the peer VPC and delete the route of the peer VPC by referring to :ref:`1 <vpc_peering_0006__li4105938135810>`.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001503330858.png
.. |image3| image:: /_static/images/en-us_image_0141273034.png
.. |image4| image:: /_static/images/en-us_image_0000001553770737.png
