:original_name: vpc_mirror_08.html

.. _vpc_mirror_08:

Modifying the Basic Information About a Mirror Filter
=====================================================

Scenarios
---------

You can modify basic information about a mirror filter, including its name and description.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Traffic Mirroring** > **Mirror Filters**.

   The mirror filter list page is displayed.

5. Locate the target mirror filter and click its name.

   The **Inbound Rules** tab is displayed.

6. Click the **Basic Information** tab and modify parameters as prompted.

   a. Click |image3| next to the parameter to be modified and enter information in the text box.
   b. Click |image4| to save the modification.

   .. table:: **Table 1** Parameters that can be modified

      +-----------------------+--------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                    | Example Value         |
      +=======================+================================================================================+=======================+
      | Name                  | Mandatory                                                                      | mirror-filter-01      |
      |                       |                                                                                |                       |
      |                       | Enter a different name for the mirror filter. The name:                        |                       |
      |                       |                                                                                |                       |
      |                       | -  Can contain 1 to 64 characters.                                             |                       |
      |                       | -  Can contain letters, digits, underscores (_), hyphens (-), and periods (.). |                       |
      +-----------------------+--------------------------------------------------------------------------------+-----------------------+
      | Description           | Optional                                                                       | ``-``                 |
      |                       |                                                                                |                       |
      |                       | Enter the description of the mirror filter in the text box as required.        |                       |
      +-----------------------+--------------------------------------------------------------------------------+-----------------------+

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000002581268328.png
.. |image3| image:: /_static/images/en-us_image_0000002581428240.png
.. |image4| image:: /_static/images/en-us_image_0000002611828085.png
