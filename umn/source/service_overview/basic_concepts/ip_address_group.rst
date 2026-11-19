:original_name: vpc_Concepts_0017.html

.. _vpc_Concepts_0017:

IP Address Group
================

An IP address group is a collection of IP addresses. It can be associated with security groups and firewalls to simplify IP address configuration and management.

You can add IP address ranges and IP addresses that need to be managed in a unified manner to an IP address group. An IP address group can work together with different cloud resources. :ref:`Table 1 <vpc_concepts_0017__en-us_topic_0146580403_table106971359413>` lists the resources that can be associated with an IP address group.

.. _vpc_concepts_0017__en-us_topic_0146580403_table106971359413:

.. table:: **Table 1** Resources that can be associated with an IP address group

   +---------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Associated Resource | Description                                                                                    | Example                                                                                                                                                                                   |
   +=====================+================================================================================================+===========================================================================================================================================================================================+
   | Security group      | The **Source** or **Destination** of a security group rule can be set to **IP address group**. | As shown in :ref:`Figure 1 <vpc_concepts_0017__en-us_topic_0146580403_fig12881184316212>`, the inbound rule of security group **sg-A** uses IP address group **ipGroup-A** as the source. |
   +---------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Firewall            | The **Source** or **Destination** of a firewall is set to **IP address group**.                | As shown in :ref:`Figure 1 <vpc_concepts_0017__en-us_topic_0146580403_fig12881184316212>`, the inbound rule of firewall **fw-A** uses IP address group **ipGroup-A** as the source.       |
   +---------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_concepts_0017__en-us_topic_0146580403_fig12881184316212:

.. figure:: /_static/images/en-us_image_0000001499056198.png
   :alt: **Figure 1** Using an IP address group

   **Figure 1** Using an IP address group
