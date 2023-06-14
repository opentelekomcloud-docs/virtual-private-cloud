:original_name: FlowLog_0002.html

.. _FlowLog_0002:

VPC Flow Log Overview
=====================

A VPC flow log records information about the traffic going to and from a VPC. VPC flow logs help you monitor network traffic, analyze network attacks, and determine whether security group and firewall rules require modification.

VPC flow logs must be used together with the Log Tank Service (LTS). Before you create a VPC flow log, you need to create a log group and a log topic in LTS. :ref:`Figure 1 <flowlog_0002__fig1535115691415>` shows the process for configuring VPC flow logs.

.. _flowlog_0002__fig1535115691415:

.. figure:: /_static/images/en-us_image_0162336264.png
   :alt: **Figure 1** Configuring VPC flow logs

   **Figure 1** Configuring VPC flow logs

Notes and Constraints
---------------------

-  Currently, only C3, M3, and S2 ECSs support VPC flow logs.
-  By default, you can create a maximum of 10 VPC flow logs.
-  By default, a maximum of 400,000 flow log records are supported.
