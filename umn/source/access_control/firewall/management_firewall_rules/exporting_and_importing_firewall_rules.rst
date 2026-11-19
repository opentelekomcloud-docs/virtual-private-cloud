:original_name: vpc_acl_0008.html

.. _vpc_acl_0008:

Exporting and Importing Firewall Rules
======================================

Scenarios
---------

You can export inbound and outbound rules of a specific firewall as an Excel file and then import these rules to another firewall. Importing and exporting rules across regions are supported.

Notes and Constraints
---------------------

-  For optimal performance, import no more than 40 firewall rules at a time.
-  Importing rules will not delete existing rules.
-  Importing duplicate rules will fail.
-  Default rules cannot be exported.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

5. Locate the target firewall and click its name.

   The firewall details page is displayed.

6. Export or import firewall rules.

   -  Click **Export Rule** to export the firewall rules to an Excel file.
   -  Click **Import Rule** to import the firewall rules from an Excel file into the current firewall.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865663489.png
