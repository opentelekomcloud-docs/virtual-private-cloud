:original_name: vpc_IPAddressGroup_0002.html

.. _vpc_IPAddressGroup_0002:

IP Address Group Overview
=========================


IP Address Group Overview
-------------------------

An IP address group is a collection of IP addresses. It can be associated with security groups to simplify IP address configuration and management.

You can add IP address ranges and IP addresses that need to be managed in a unified manner to an IP address group. An IP address group can work together with different cloud resources. :ref:`Table 1 <vpc_ipaddressgroup_0002__table106971359413>` lists the resources that can be associated with an IP address group.

.. _vpc_ipaddressgroup_0002__table106971359413:

.. table:: **Table 1** Resources that can be associated with an IP address group

   +----------------+------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Resource       | Description                                                                                    | Example                                                                                                                                                        |
   +================+================================================================================================+================================================================================================================================================================+
   | Security group | The **Source** or **Destination** of a security group rule can be set to **IP address group**. | As shown in :ref:`Figure 1 <vpc_ipaddressgroup_0002__fig208404173279>`, the inbound rule of security group sg-A uses IP address group ipGroup-A as the source. |
   +----------------+------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_ipaddressgroup_0002__fig208404173279:

.. figure:: /_static/images/en-us_image_0000002373307737.png
   :alt: **Figure 1** Using an IP address group

   **Figure 1** Using an IP address group
