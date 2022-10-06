:original_name: vpc_FlowLog02_0005.html

.. _vpc_FlowLog02_0005:

Deleting a VPC Flow Log
=======================

Scenarios
---------

Delete a VPC flow log that is not required. Deleting a VPC flow log will not delete the existing flow log records in LTS.

.. note::

   If a NIC that uses a VPC flow log is deleted, the flow log will be automatically deleted. However, the flow log records are not deleted.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. On the console homepage, under **Network**, click **Virtual Private Cloud**.

4. In the navigation pane on the left, choose **VPC Flow Logs**.

5. Locate the row that contains the VPC flow log to be deleted and click **Delete** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0191594527.png
      :alt: **Figure 1** Deleting a VPC flow log


      **Figure 1** Deleting a VPC flow log

6. Click **Yes** in the displayed dialog box.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
