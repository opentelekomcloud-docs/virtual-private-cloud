:original_name: vpc_sg02_0004.html

.. _vpc_sg02_0004:

Updating a Security Group
=========================

Function
--------

This API is used to update a security group.

URI
---

PUT /v2.0/security-groups/{security_group_id}

Request Parameters
------------------

.. table:: **Table 1** Request parameter

   +-----------------+-----------------------------------------------------------------+-----------------+---------------------------------------------------------------------------------------------------+
   | Parameter       | Type                                                            | Mandatory       | Description                                                                                       |
   +=================+=================================================================+=================+===================================================================================================+
   | security_group  | :ref:`security_group <vpc_sg02_0004__table513726041607>` object | Yes             | Specifies the security group. For details, see :ref:`Table 2 <vpc_sg02_0004__table513726041607>`. |
   |                 |                                                                 |                 |                                                                                                   |
   |                 |                                                                 |                 | You must specify at least one attribute when updating a security group.                           |
   +-----------------+-----------------------------------------------------------------+-----------------+---------------------------------------------------------------------------------------------------+

.. _vpc_sg02_0004__table513726041607:

.. table:: **Table 2** **Security Group** objects

   +-------------+-----------+--------+--------------------------------------------------------------+
   | Attribute   | Mandatory | Type   | Description                                                  |
   +=============+===========+========+==============================================================+
   | name        | No        | String | Specifies the security group name.                           |
   +-------------+-----------+--------+--------------------------------------------------------------+
   | description | No        | String | Provides supplementary information about the security group. |
   +-------------+-----------+--------+--------------------------------------------------------------+

Example Request
---------------

Change the name of the security group whose ID is d29ae17d-f355-4992-8747-1fb66cc9afd2 to **sg-test02**.

.. code-block:: text

   PUT https://{Endpoint}/v2.0/security-groups/d29ae17d-f355-4992-8747-1fb66cc9afd2

   {
       "security_group": {
              "name": "sg-test02"
       }
   }

Response Parameters
-------------------

.. table:: **Table 3** Response parameter

   +----------------+--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type                                                               | Description                                                                                                  |
   +================+====================================================================+==============================================================================================================+
   | security_group | :ref:`security_group <vpc_sg02_0004__table166682044134519>` object | Specifies the security group objects. For details, see :ref:`Table 4 <vpc_sg02_0004__table166682044134519>`. |
   +----------------+--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+

.. _vpc_sg02_0004__table166682044134519:

.. table:: **Table 4** **Security Group** objects

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
   | security_group_rules  | Array of :ref:`Security Group Rule <vpc_sg02_0004__table655457801607>` objects | Specifies the security group rule list. For details, see :ref:`Table 5 <vpc_sg02_0004__table655457801607>`. |
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

.. _vpc_sg02_0004__table655457801607:

.. table:: **Table 5** **Security Group Rule** objects

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
           "id": "d29ae17d-f355-4992-8747-1fb66cc9afd2",
           "name": "sg-test02",
           "description": "",
           "tenant_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
           "project_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
           "security_group_rules": [
               {
                   "id": "6332de3e-98fb-4f8c-b44a-fcb8ff09881e",
                   "direction": "egress",
                   "protocol": null,
                   "ethertype": "IPv6",
                   "description": null,
                   "remote_group_id": null,
                   "remote_ip_prefix": null,
                   "tenant_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
                   "port_range_max": null,
                   "port_range_min": null,
                   "security_group_id": "d29ae17d-f355-4992-8747-1fb66cc9afd2",
                   "remote_address_group_id": "0150a3a7-82ca-4569-865c-04e46e5e9249"
               },
               {
                   "id": "3f51e52c-0e85-40f7-a137-85927392e436",
                   "direction": "egress",
                   "protocol": null,
                   "ethertype": "IPv4",
                   "description": null,
                   "remote_group_id": null,
                   "remote_ip_prefix": null,
                   "tenant_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
                   "port_range_max": null,
                   "port_range_min": null,
                   "security_group_id": "d29ae17d-f355-4992-8747-1fb66cc9afd2",
                   "remote_address_group_id": null
               }
           ],
           "created_at": "2018-09-20T02:15:34",
           "updated_at": "2018-09-20T02:16:31"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
