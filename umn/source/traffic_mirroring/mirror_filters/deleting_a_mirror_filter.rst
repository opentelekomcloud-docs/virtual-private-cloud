:original_name: vpc_mirror_10.html

.. _vpc_mirror_10:

Deleting a Mirror Filter
========================

Scenarios
---------

If a mirror filter is no longer required, you can delete it.

Notes and Constraints
---------------------

If a mirror filter has mirror sessions associated, disassociate the mirror sessions first and then delete the mirror filter.

-  Each mirror session must have a mirror filter associated. You can change the mirror filter for the mirror sessions. For details, see :ref:`Changing the Mirror Filter for a Mirror Session <vpc_mirror_16>`.
-  If your mirror sessions are no longer required, you can also delete them. For details, see :ref:`Deleting a Mirror Session <vpc_mirror_20>`.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Traffic Mirroring** > **Mirror Filters**.

   The mirror filter list page is displayed.

5. Locate the target mirror filter and click **Delete** in the **Operation** column.

   A confirmation dialog box is displayed.

6. Confirm the information and click **OK**.

   A deleted mirror filter cannot be recovered.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000002581268330.png
