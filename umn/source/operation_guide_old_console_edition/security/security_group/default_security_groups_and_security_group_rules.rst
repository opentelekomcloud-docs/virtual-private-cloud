:original_name: vpc_SecurityGroup02_0002.html

.. _vpc_SecurityGroup02_0002:

Default Security Groups and Security Group Rules
================================================

Your account automatically comes with a default security group. The default security group allows all outbound traffic, denies all inbound traffic, and allows all traffic between cloud resources in the group. Your cloud resources in this security group can communicate with each other already without adding additional rules.

:ref:`Figure 1 <vpc_securitygroup02_0002__en-us_topic_0118534003_fig997718156161>` shows the default security group rules. The following uses access between ECSs as an example.

.. _vpc_securitygroup02_0002__en-us_topic_0118534003_fig997718156161:

.. figure:: /_static/images/en-us_image_0000001230120807.png
   :alt: **Figure 1** Default security group


   **Figure 1** Default security group

:ref:`Table 1 <vpc_securitygroup02_0002__en-us_topic_0118534003_table493045171919>` describes the default rules for the default security group.

.. _vpc_securitygroup02_0002__en-us_topic_0118534003_table493045171919:

.. table:: **Table 1** Default security group rules

   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Direction | Protocol | Port/Range | Source/Destination                                           | Description                                                                                                        |
   +===========+==========+============+==============================================================+====================================================================================================================+
   | Outbound  | All      | All        | Destination: 0.0.0.0/0                                       | Allows all outbound traffic.                                                                                       |
   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Inbound   | All      | All        | Source: the current security group (for example, sg-*xxxxx*) | Allows communications among ECSs within the security group and denies all inbound traffic (incoming data packets). |
   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
