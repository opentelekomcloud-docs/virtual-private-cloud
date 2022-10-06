:original_name: vpc_peering_0006.html

.. _vpc_peering_0006:

Deleting a VPC Peering Route
============================

Scenarios
---------

After routes are added for a VPC peering connection, the owners of both the local and peer accounts can delete the routes on the **Route Tables** page.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. On the console homepage, under **Network**, click **Virtual Private Cloud**.
#. In the connection list, locate the VPC peering connection that you need to delete routes.
#. Click the name of the VPC peering connection to switch to the page showing details about the connection.
#. Delete the route added to the route table of the local VPC:

   a. Click the **Local Routes** tab and then click the **Route Tables** hyperlink.

      The **Summary** tab of the default route table for the local VPC is displayed.

   b. Locate the row that contains the route to be deleted and click **Delete** in the **Operation** column.

   c. Click **Yes**.

#. Delete the route added to the route table of the peer VPC:

   a. Click the **Peer Routes** tab and then click the **Route Tables** hyperlink.

      The **Summary** tab of the default route table for the peer VPC is displayed.

   b. Locate the row that contains the route to be deleted and click **Delete** in the **Operation** column.

   c. Click **Yes** in the displayed dialog box.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
