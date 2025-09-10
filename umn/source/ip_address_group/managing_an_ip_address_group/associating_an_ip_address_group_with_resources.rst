:original_name: vpc_IPAddressGroup_0004.html

.. _vpc_IPAddressGroup_0004:

Associating an IP Address Group with Resources
==============================================

Scenarios
---------

This section describes how to associate an IP address group with a resource.

An IP address group can be associated with security groups.

Prerequisites
-------------

-  You have created an IP address group has been created. For details, see :ref:`Creating an IP Address Group <vpc_ipaddressgroup_0003>`.
-  There are IP address entries in the IP address group. For details, see :ref:`Adding IP Address Entries to an IP Address Group <vpc_ipaddressgroup_0007>`.

Procedure
---------

You need to associate an IP address group with resources. For details, see :ref:`Table 1 <vpc_ipaddressgroup_0004__table106971359413>`.

.. _vpc_ipaddressgroup_0004__table106971359413:

.. table:: **Table 1** Associating an IP address group with resources

   +-----------------------+------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | Resource              | Description                                                                                    | Reference                                                     |
   +=======================+================================================================================================+===============================================================+
   | Security group        | The **Source** or **Destination** of a security group rule can be set to **IP address group**. | :ref:`Adding a Security Group Rule <en-us_topic_0030969470>`  |
   |                       |                                                                                                |                                                               |
   |                       |                                                                                                | -  Inbound rule: Set **Source** to an IP address group.       |
   |                       |                                                                                                | -  Outbound rule: Set **Destination** to an IP address group. |
   +-----------------------+------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
