:original_name: en-us_topic_0030969462.html

.. _en-us_topic_0030969462:

Modifying a VPC
===============

Scenarios
---------

You can modify the following information about a VPC:

-  :ref:`Modifying the Name and Description of a VPC <en-us_topic_0030969462__section495418425354>`
-  :ref:`Modifying the CIDR Block of a VPC <en-us_topic_0030969462__section696206193617>`

.. _en-us_topic_0030969462__section495418425354:

Modifying the Name and Description of a VPC
-------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. Modify the name and description of a VPC using either of the following methods:

   -  Method 1:

      a. In the VPC list, click |image3| on the right of the VPC name.
      b. Enter the VPC name and click **OK**.

   -  Method 2:

      a. In the VPC list, click the VPC name with a hyperlink.

         The **Summary** page is displayed.

      b. Click |image4| on the right of the VPC name or description, enter the information, and click |image5|.

.. _en-us_topic_0030969462__section696206193617:

Modifying the CIDR Block of a VPC
---------------------------------

#. Log in to the management console.

#. Click |image6| in the upper left corner and select the desired region and project.

#. Click |image7| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the VPC list, locate the row that contains the VPC and click **Edit CIDR Block** in the **Operation** column.

   The **Edit CIDR Block** dialog box is displayed.

5. Modify the VPC CIDR block as prompted.

   .. important::

      A VPC CIDR block must be from 10.0.0.0/8-24, 172.16.0.0/12-24, or 192.168.0.0/16-24.

   -  If a VPC has no subnets, you can change both its network address and subnet mask.


      .. figure:: /_static/images/en-us_image_0000001627653972.png
         :alt: **Figure 1** Modifying network address and subnet mask

         **Figure 1** Modifying network address and subnet mask

   -  If a VPC has subnets, you only can change its subnet mask.


      .. figure:: /_static/images/en-us_image_0000001627493158.png
         :alt: **Figure 2** Modifying subnet mask

         **Figure 2** Modifying subnet mask

6. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001676063997.png
.. |image3| image:: /_static/images/en-us_image_0000001627174280.png
.. |image4| image:: /_static/images/en-us_image_0000001675813933.png
.. |image5| image:: /_static/images/en-us_image_0000001627334080.png
.. |image6| image:: /_static/images/en-us_image_0141273034.png
.. |image7| image:: /_static/images/en-us_image_0000001627744152.png
