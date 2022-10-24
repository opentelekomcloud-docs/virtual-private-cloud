:original_name: vpc_FlowLog02_0001.html

.. _vpc_FlowLog02_0001:

VPC Flow Log Overview
=====================

A VPC flow log records information about the traffic going to and from a VPC. VPC flow logs help you monitor network traffic, analyze network attacks, and determine whether security group and firewall rules require modification.

VPC flow logs must be used together with the Log Tank Service (LTS). Before you create a VPC flow log, you need to create a log group and a log topic in LTS. :ref:`Figure 1 <vpc_flowlog02_0001__en-us_topic_0151014680_fig1535115691415>` shows the process for configuring the VPC flow log function.

.. _vpc_flowlog02_0001__en-us_topic_0151014680_fig1535115691415:

.. figure:: /_static/images/en-us_image_0162336264.png
   :alt: **Figure 1** Configuring the VPC flow log function

   **Figure 1** Configuring the VPC flow log function

Notes and Constraints
---------------------

-  Currently, only C3, M3, and S2 ECSs support VPC flow logs.
-  By default, you can create a maximum of 10 VPC flow logs.
-  By default, a maximum of 400,000 flow log records are supported.
