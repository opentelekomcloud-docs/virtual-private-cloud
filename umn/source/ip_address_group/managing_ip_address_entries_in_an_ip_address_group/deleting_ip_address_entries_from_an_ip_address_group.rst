:original_name: vpc_IPAddressGroup_0008.html

.. _vpc_IPAddressGroup_0008:

Deleting IP Address Entries from an IP Address Group
====================================================

Scenarios
---------

This section describes how to delete IP address entries from an IP address group.

Constraints
-----------

If an IP address group has resources associated, deleting IP address entries from the group may affect your network communications.

If an IP address group has security groups associated, the rules associated with the IP address group will change.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

4. In the navigation pane on the left, choose **IP Address Groups**.

   The IP address group list is displayed.

5. In the IP address group list, click the hyperlink of the IP address group name.

   The basic information page of the IP address group is displayed.

6. Delete IP address entries:

   -  Delete a single IP address entry.

      a. In the IP address entry list, locate the target IP address entry and click **Delete** in the **Operation** column.

         A confirmation dialog box is displayed.

      b. Confirm the information and click **OK**.

   -  Delete IP address entries in batches.

      a. In the IP address entry list, select the IP address entries to be deleted.

      b. Click the **Delete** button above the IP address entry list.

         A confirmation dialog box is displayed.

      c. Confirm the information and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865582581.png
