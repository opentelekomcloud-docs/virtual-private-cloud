:original_name: vpc010006.html

.. _vpc010006:

Adding EIPs to a Shared Bandwidth
=================================

Scenarios
---------

Add EIPs to a shared bandwidth and the EIPs can then share that bandwidth. You can add multiple EIPs to a shared bandwidth at the same time.

Notes and Constraints
---------------------

-  The type of EIPs must be the same as that of the shared bandwidth the EIPs to be added to.
-  Do not add EIPs of the dedicated load balancer type (**5_gray**) and other types to the same shared bandwidth. Otherwise, the bandwidth limit policy will not take effect.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Elastic IP**.

4. In the navigation pane on the left, choose **Elastic IP and Bandwidth** > **Shared Bandwidths**.

5. In the shared bandwidth list, locate the row that contains the shared bandwidth that you want to add EIPs to. In the **Operation** column, choose **Add EIP**, and select the EIPs to be added.

   .. note::

      -  After an EIP is added to a shared bandwidth, the dedicated bandwidth used by the EIP will become invalid and the EIP will start to use the shared bandwidth. The EIP's dedicated bandwidth will be deleted and will no longer be billed.


   .. figure:: /_static/images/en-us_image_0000001211006359.png
      :alt: **Figure 1** Add EIP

      **Figure 1** Add EIP

6. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0000001454059512.png
