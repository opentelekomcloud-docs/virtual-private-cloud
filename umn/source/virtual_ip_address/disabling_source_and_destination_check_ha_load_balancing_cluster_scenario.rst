:original_name: vpc_vip_0008.html

.. _vpc_vip_0008:

Disabling Source and Destination Check (HA Load Balancing Cluster Scenario)
===========================================================================

Scenarios
---------

If a virtual IP address is used in an HA load balancing cluster, you need to disable source/destination check for ECS NICs.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. In the upper left corner of the page, click |image2|. In the service list, choose **Computing** > **Elastic Cloud Server**.
#. In the ECS list, click the ECS name.
#. On the displayed ECS details page, click the **NICs** tab.
#. Click the IP address to view the NIC details.
#. Check that **Source/Destination Check** is disabled.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001681512581.png
