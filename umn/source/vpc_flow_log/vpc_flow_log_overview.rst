:original_name: FlowLog_0002.html

.. _FlowLog_0002:

VPC Flow Log Overview
=====================

What Is a VPC Flow Log?
-----------------------

A VPC flow log records information about the traffic going to and from a VPC. VPC flow logs help you monitor network traffic, analyze network attacks, and determine whether security group and firewall rules require modification.

VPC flow logs must be used together with the Log Tank Service (LTS). Before you create a VPC flow log, you need to create a log group and a log stream in LTS. :ref:`Figure 1 <flowlog_0002__fig20742104751616>` shows the process for configuring VPC flow logs.

.. _flowlog_0002__fig20742104751616:

.. figure:: /_static/images/en-us_image_0000001865583169.png
   :alt: **Figure 1** Configuring VPC flow logs

   **Figure 1** Configuring VPC flow logs

Notes and Constraints
---------------------

-  VPC flow logs ECS support for **EU-DE**: x2, x1, s7n, s3, s2, x2e, x1e, c9, c7t, 
   c7n, c4, c3, m9, m7n, m4, m3, e3, d2, pi2, p3, p2v, p2s, g7v, g7, g6 specifications.
-  VPC flow logs ECS support for **EU-NL**: x2, s7n, s3, x2e, c9, c7n, c4, m9, m7n, 
   m4, i3, pi2, p3, p2s, g7 specifications.
-  Each account can have up to 10 VPC flow logs in a region.
-  By default, a maximum of 400,000 flow log records are supported.
