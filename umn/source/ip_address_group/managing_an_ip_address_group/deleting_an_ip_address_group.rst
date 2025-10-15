:original_name: vpc_IPAddressGroup_0011.html

.. _vpc_IPAddressGroup_0011:

Deleting an IP Address Group
============================

Scenarios
---------

This section describes how to delete an IP address group.

Notes and Constraints
---------------------

If you want to delete an IP address group with resources associated, you need to :ref:`disassociate the IP address group from the resources first <vpc_ipaddressgroup_0006>`.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **IP Address Groups**.

   The IP address group list is displayed.

5. Perform the following operations to delete IP address groups.

   -  Delete a single IP address group:

      a. In the IP address group list, locate the row that contains the IP address group and click **Delete** in the **Operation** column.

         A confirmation dialog box is displayed.

      b. Enter **DELETE** as prompted and click **OK**.

   -  Delete IP address groups in a batch.

      a. In the IP address group list, select the IP address groups to be deleted.

      b. Click the **Delete** button above the IP address entry list.

         A confirmation dialog box is displayed.

      c. Enter **DELETE** as prompted and click **OK**.

         If a message indicating that IP address groups with associated resources cannot be deleted is displayed, go to the resource details page and :ref:`disassociate the IP address group from the resources first <vpc_ipaddressgroup_0006>`.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818983350.png
