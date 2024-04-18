:original_name: en-us_topic_0030969462.html

.. _en-us_topic_0030969462:

Modifying a VPC
===============

Scenarios
---------

You can modify the following information about a VPC:

-  :ref:`Modifying the Name and Description of a VPC <en-us_topic_0030969462__section495418425354>`
-  :ref:`Modifying the CIDR Block of a VPC <en-us_topic_0030969462__section696206193617>`

   .. note::

      If the :ref:`secondary IPv4 CIDR block <vpc_vpc_0007>` function is available in a region, the CIDR block of a VPC in this region cannot be modified through the console. You can call an API to modify VPC CIDR block by referring to `Updating VPC Information <https://docs.otc.t-systems.com/virtual-private-cloud/api-ref/apis/virtual_private_cloud/updating_vpc_information.html#vpc-api01-0004>`__.

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

5. Click **Add Secondary IPv4 CIDR Block**.

6. Enter the secondary CIDR block and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823402.png
.. |image3| image:: /_static/images/en-us_image_0000001818823394.png
.. |image4| image:: /_static/images/en-us_image_0000001865663133.png
.. |image5| image:: /_static/images/en-us_image_0000001818983186.png
.. |image6| image:: /_static/images/en-us_image_0000001818982734.png
.. |image7| image:: /_static/images/en-us_image_0000001865663129.png
