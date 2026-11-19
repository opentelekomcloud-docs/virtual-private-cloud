:original_name: FlowLog_0004.html

.. _FlowLog_0004:

Viewing a VPC Flow Log
======================

Scenarios
---------

View information about your flow log record.

The capture window is approximately 10 minutes, which indicates that a flow log record will be generated every 10 minutes. After creating a VPC flow log, you need to wait about 10 minutes before you can view the flow log record.

.. note::

   If an ECS is in the stopped state, its flow log records will not be displayed.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

4. In the navigation pane on the left, choose **VPC Flow Logs**.

5. Locate the row that contains the target VPC flow log and click **View Log Record** in the **Operation** column.

   The **Log Management** page is displayed.


   .. figure:: /_static/images/en-us_image_0000002524909582.png
      :alt: **Figure 1** Log management

      **Figure 1** Log management

6. In the log group list, locate the target log group and click the name of the target log stream.

   The log stream details page is displayed.

7. Enter key information in the search box to quickly find the flow log to be viewed.

   The flow log record is in the following format:

   .. code-block::

      <version> <project-id> <interface-id> <srcaddr> <dstaddr> <srcport> <dstport> <protocol> <packets> <bytes> <start> <end> <action> <log-status>

   For details about the fields supported by the current VPC flow log version, see :ref:`VPC Flow Log Data <flowlog_0002__section2039010441903>`.

:ref:`Table 1 <flowlog_0004__table1083924581412>` provides you with flow log examples.

.. _flowlog_0004__table1083924581412:

.. table:: **Table 1** Flow log examples

   +---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scenario                                                                  | Example Value                                                                                                                                                                                                                                                                                                                                                                                                           |
   +===========================================================================+=========================================================================================================================================================================================================================================================================================================================================================================================================================+
   | A flow log record in which data was recorded during the capture window    | Value **1** indicates the VPC flow log version. Traffic with a size of 96 bytes to the network interface (**1d515d18-1b36-47dc-a983-bd6512aed4bd**) during the past 10 minutes (from 16:55:36 to 17:05:36 on January 29, 2019) was allowed. A data packet was transmitted over the UDP protocol from source IP address **192.168.0.154** and port **38929** to destination IP address **192.168.3.25** and port **53**. |
   |                                                                           |                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |                                                                           | .. code-block::                                                                                                                                                                                                                                                                                                                                                                                                         |
   |                                                                           |                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |                                                                           |    1 5f67944957444bd6bb4fe3b367de8f3d 1d515d18-1b36-47dc-a983-bd6512aed4bd 192.168.0.154 192.168.3.25 38929 53 17 1 96 1548752136 1548752736 ACCEPT OK                                                                                                                                                                                                                                                                  |
   +---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | A flow log record in which no data was recorded during the capture window | .. code-block::                                                                                                                                                                                                                                                                                                                                                                                                         |
   |                                                                           |                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |                                                                           |    1 5f67944957444bd6bb4fe3b367de8f3d 1d515d18-1b36-47dc-a983-bd6512aed4bd - - - - - - - 1431280876 1431280934 - NODATA                                                                                                                                                                                                                                                                                                 |
   +---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | A flow log record in which data was skipped during the capture window     | .. code-block::                                                                                                                                                                                                                                                                                                                                                                                                         |
   |                                                                           |                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |                                                                           |    1 5f67944957444bd6bb4fe3b367de8f3d 1d515d18-1b36-47dc-a983-bd6512aed4bd - - - - - - - 1431280876 1431280934 - SKIPDATA                                                                                                                                                                                                                                                                                               |
   +---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

You can enter a keyword on the log stream details page on the LTS console to search for flow log records.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865582981.png
