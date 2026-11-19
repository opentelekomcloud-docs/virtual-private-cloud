:original_name: vpc_mirror_17.html

.. _vpc_mirror_17:

Changing the Mirror Target of a Mirror Session
==============================================

Scenarios
---------

A mirror session can be associated with only one mirror target. You can change the mirror target of a mirror session.

Constraints
-----------

-  A mirror target is a network interface of an ECS or a load balancer, which is used to receive mirrored traffic.

-  Each mirror session can be associated with only one mirror target.

   For details about the constraints on mirror targets, see :ref:`Table 6 <vpc_mirror_02__en-us_topic_0000001651378981_table66725225618>`.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Traffic Mirroring** > **Mirror Sessions**.

   The **Mirror Sessions** page is displayed.

5. In the mirror session list, locate the row that contains the mirror session and choose **More** > **Change Mirror Target** in the **Operation** column.

   The **Change Mirror Target** dialog box is displayed.

6. In the mirror target list, select a mirror target, and click **OK**.

   After the change, you can see the new mirror target in the **Mirror Target** column of the mirror session list.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000002611828091.png
