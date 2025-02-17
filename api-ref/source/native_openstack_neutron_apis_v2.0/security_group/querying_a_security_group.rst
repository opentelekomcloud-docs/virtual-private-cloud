:original_name: vpc_sg02_0002.html

.. _vpc_sg02_0002:

Querying a Security Group
=========================

Function
--------

This API is used to query details about a specific security group.

URI
---

GET /v2.0/security-groups/{security_group_id}

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v2.0/security-groups/0431c9c5-1660-42e0-8a00-134bec7f03e2

Response Parameters
-------------------

.. table:: **Table 1** Response parameter

   +----------------+-----------------------------------------------------------------+---------------------------------------------------------------------------------------------------+
   | Parameter      | Type                                                            | Description                                                                                       |
   +================+=================================================================+===================================================================================================+
   | security_group | :ref:`security_group <vpc_sg02_0002__table513726041607>` object | Specifies the security group. For details, see :ref:`Table 2 <vpc_sg02_0002__table513726041607>`. |
   +----------------+-----------------------------------------------------------------+---------------------------------------------------------------------------------------------------+

.. _vpc_sg02_0002__table513726041607:

.. table:: **Table 2** **Security Group** objects

   +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | Attribute             | Type                                                                           | Description                                                                                                 |
   +=======================+================================================================================+=============================================================================================================+
   | id                    | String                                                                         | Specifies the security group ID.                                                                            |
   |                       |                                                                                |                                                                                                             |
   |                       |                                                                                | This parameter is not mandatory when you query security groups.                                             |
   +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                                                                         | Specifies the project ID.                                                                                   |
   +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                         | Specifies the security group name.                                                                          |
   +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                         | Provides supplementary information about the security group.                                                |
   +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | security_group_rules  | Array of :ref:`Security Group Rule <vpc_sg02_0002__table655457801607>` objects | Specifies the security group rule list. For details, see :ref:`Table 3 <vpc_sg02_0002__table655457801607>`. |
   +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                                         | Specifies the project ID.                                                                                   |
   +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                         | Specifies the time (UTC) when the security group is created.                                                |
   |                       |                                                                                |                                                                                                             |
   |                       |                                                                                | Format: *yyyy-MM-ddTHH:mm:ss*                                                                               |
   +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                         | Specifies the time (UTC) when the security group is updated.                                                |
   |                       |                                                                                |                                                                                                             |
   |                       |                                                                                | Format: *yyyy-MM-ddTHH:mm:ss*                                                                               |
   +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+

.. _vpc_sg02_0002__table655457801607:

.. table:: **Table 3** **Security Group Rule** objects

   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Attribute               | Type                  | Description                                                                                                                                                                                 |
   +=========================+=======================+=============================================================================================================================================================================================+
   | id                      | String                | Specifies the security group rule ID.                                                                                                                                                       |
   |                         |                       |                                                                                                                                                                                             |
   |                         |                       | This parameter is not mandatory when you query security group rules.                                                                                                                        |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description             | String                | Provides supplementary information about the security group rule.                                                                                                                           |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id       | String                | Specifies the ID of the belonged security group.                                                                                                                                            |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_group_id         | String                | Specifies the peer ID of the belonged security group.                                                                                                                                       |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | direction               | String                | Specifies the direction of the traffic for which the security group rule takes effect.                                                                                                      |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_ip_prefix        | String                | Specifies the peer IP address segment.                                                                                                                                                      |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol                | String                | Specifies the protocol type or the IP protocol number.                                                                                                                                      |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_max          | Integer               | Specifies the maximum port number. When ICMP is used, the value is the ICMP code.                                                                                                           |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_min          | Integer               | Specifies the minimum port number. If the ICMP protocol is used, this parameter indicates the ICMP type.                                                                                    |
   |                         |                       |                                                                                                                                                                                             |
   |                         |                       | When the TCP or UDP protocol is used, both **port_range_max** and **port_range_min** must be specified, and the **port_range_max** value must be greater than the **port_range_min** value. |
   |                         |                       |                                                                                                                                                                                             |
   |                         |                       | When the ICMP protocol is used, if you specify the ICMP code (**port_range_max**), you must also specify the ICMP type (**port_range_min**).                                                |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ethertype               | String                | Specifies the network type.                                                                                                                                                                 |
   |                         |                       |                                                                                                                                                                                             |
   |                         |                       | IPv4 and IPv6 are supported.                                                                                                                                                                |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id               | String                | Specifies the project ID.                                                                                                                                                                   |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_address_group_id | String                | -  Specifies the remote IP address group ID.                                                                                                                                                |
   |                         |                       | -  The parameter value is mutually exclusive with parameters **remote_ip_prefix** and **remote_group_id**.                                                                                  |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id              | String                | Specifies the project ID.                                                                                                                                                                   |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at              | String                | Specifies the time (UTC) when the security group rule is created.                                                                                                                           |
   |                         |                       |                                                                                                                                                                                             |
   |                         |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                               |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at              | String                | Specifies the time (UTC) when the security group rule is updated.                                                                                                                           |
   |                         |                       |                                                                                                                                                                                             |
   |                         |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                               |
   +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "security_group": {
           "id": "0431c9c5-1660-42e0-8a00-134bec7f03e2",
           "name": "sg-ad3f",
           "description": "",
           "tenant_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
           "project_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
           "security_group_rules": [
               {
                   "id": "d90e55ba-23bd-4d97-b722-8cb6fb485d69",
                   "direction": "ingress",
                   "protocol": null,
                   "ethertype": "IPv4",
                   "description": null,
                   "remote_group_id": "0431c9c5-1660-42e0-8a00-134bec7f03e2",
                   "remote_ip_prefix": null,
                   "tenant_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
                   "port_range_max": null,
                   "port_range_min": null,
                   "security_group_id": "0431c9c5-1660-42e0-8a00-134bec7f03e2",
                   "remote_address_group_id": "0150a3a7-82ca-4569-865c-04e46e5e9249"
               },
               {
                   "id": "aecff4d4-9ce9-489c-86a3-803aedec65f7",
                   "direction": "egress",
                   "protocol": null,
                   "ethertype": "IPv4",
                   "description": null,
                   "remote_group_id": null,
                   "remote_ip_prefix": null,
                   "tenant_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
                   "port_range_max": null,
                   "port_range_min": null,
                   "security_group_id": "0431c9c5-1660-42e0-8a00-134bec7f03e2",
                   "remote_address_group_id": null
               }
           ],
           "created_at": "2018-09-12T08:24:14",
           "updated_at": "2018-09-12T08:24:14"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
