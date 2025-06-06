:original_name: vpc_sg01_0002.html

.. _vpc_sg01_0002:

Querying Security Group Details
===============================

Function
--------

This API is used to query details about a security group.

URI
---

GET /v1/{project_id}/security-groups/{security_group_id}

:ref:`Table 1 <vpc_sg01_0002__table211310359520>` describes the parameters.

.. _vpc_sg01_0002__table211310359520:

.. table:: **Table 1** Parameter description

   +-------------------+-----------+--------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Description                                                                    |
   +===================+===========+================================================================================+
   | project_id        | Yes       | Specifies the project ID.                                                      |
   +-------------------+-----------+--------------------------------------------------------------------------------+
   | security_group_id | Yes       | Specifies the security group ID, which uniquely identifies the security group. |
   +-------------------+-----------+--------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/security-groups/16b6e77a-08fa-42c7-aa8b-106c048884e6

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +----------------+-----------------------------------------------------------------+--------------------------------------+
   | Parameter      | Type                                                            | Description                          |
   +================+=================================================================+======================================+
   | security_group | :ref:`security_group <vpc_sg01_0002__table333218689520>` object | Specifies the security group object. |
   +----------------+-----------------------------------------------------------------+--------------------------------------+

.. _vpc_sg01_0002__table333218689520:

.. table:: **Table 3** Description of **security_group** fields

   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                           | Description                                                                                                                                                        |
   +=======================+================================================================================+====================================================================================================================================================================+
   | name                  | String                                                                         | Specifies the security group name.                                                                                                                                 |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                         | Provides supplementary information about the security group.                                                                                                       |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                                                                         | Specifies the security group ID, which uniquely identifies the security group.                                                                                     |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id                | String                                                                         | Specifies the resource ID of the VPC to which the security group belongs.                                                                                          |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | .. note::                                                                                                                                                          |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    Currently, this parameter is not recommended because it is only used as a prompt and does not restrict that the security group must be associated with the VPC. |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_rules  | Array of :ref:`security_group_rule <vpc_sg01_0002__table488727239520>` objects | Specifies the default security group rules, which ensure that resources in the security group can communicate with one another.                                    |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | String                                                                         | -  Specifies the enterprise project ID. When creating a security group, associate the enterprise project ID with the security group.                               |
   |                       |                                                                                | -  The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). Value **0** indicates the default enterprise project.  |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                | .. note::                                                                                                                                                          |
   |                       |                                                                                |                                                                                                                                                                    |
   |                       |                                                                                |    This parameter is unsupported. Do not use it.                                                                                                                   |
   +-----------------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_sg01_0002__table488727239520:

.. table:: **Table 4** **security_group_rule** objects

   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Type                  | Description                                                                                                                                                                                                                                               |
   +=========================+=======================+===========================================================================================================================================================================================================================================================+
   | id                      | String                | Specifies the security group rule ID, which uniquely identifies the security group rule.                                                                                                                                                                  |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description             | String                | -  Provides supplementary information about the security group rule.                                                                                                                                                                                      |
   |                         |                       | -  The value can contain no more than 255 characters, including letters and digits.                                                                                                                                                                       |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id       | String                | Specifies the security group rule ID, which uniquely identifies the security group rule.                                                                                                                                                                  |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | direction               | String                | -  Specifies the direction of access control.                                                                                                                                                                                                             |
   |                         |                       | -  Possible values are as follows:                                                                                                                                                                                                                        |
   |                         |                       |                                                                                                                                                                                                                                                           |
   |                         |                       |    -  **egress**                                                                                                                                                                                                                                          |
   |                         |                       |    -  **ingress**                                                                                                                                                                                                                                         |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ethertype               | String                | -  Specifies the IP protocol version.                                                                                                                                                                                                                     |
   |                         |                       | -  The value can be **IPv4** or **IPv6**.                                                                                                                                                                                                                 |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol                | String                | -  Specifies the protocol type.                                                                                                                                                                                                                           |
   |                         |                       | -  The value can be **icmp**, **tcp**, **udp**, or an IP protocol number (0 to 255, for example, 47 for GRE)                                                                                                                                              |
   |                         |                       | -  If the parameter is left blank, all protocols are supported.                                                                                                                                                                                           |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_min          | Integer               | -  Specifies the start port number.                                                                                                                                                                                                                       |
   |                         |                       | -  The value ranges from 1 to 65535.                                                                                                                                                                                                                      |
   |                         |                       | -  The value cannot be greater than the **port_range_max** value. An empty value indicates all ports. If the protocol is **icmp**, the value range is shown in :ref:`ICMP-Port Range Relationship Table <vpc_api_0009>`.                                  |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_max          | Integer               | -  Specifies the end port number.                                                                                                                                                                                                                         |
   |                         |                       | -  The value ranges from 1 to 65535.                                                                                                                                                                                                                      |
   |                         |                       | -  If the protocol is not **icmp**, the value cannot be smaller than the **port_range_min** value. An empty value indicates all ports. If the protocol is **icmp**, the value range is shown in :ref:`ICMP-Port Range Relationship Table <vpc_api_0009>`. |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_ip_prefix        | String                | -  Specifies the remote IP address. If the access control direction is set to **egress**, the parameter specifies the source IP address. If the access control direction is set to **ingress**, the parameter specifies the destination IP address.       |
   |                         |                       | -  The value can be in the CIDR format or IP addresses.                                                                                                                                                                                                   |
   |                         |                       | -  The parameter value is mutually exclusive with parameters **remote_group_id** and **remote_address_group_id**.                                                                                                                                         |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_group_id         | String                | -  Specifies the ID of the peer security group.                                                                                                                                                                                                           |
   |                         |                       | -  The parameter value is mutually exclusive with parameters **remote_ip_prefix** and **remote_address_group_id**.                                                                                                                                        |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_address_group_id | String                | -  Specifies the remote IP address group ID.                                                                                                                                                                                                              |
   |                         |                       | -  The parameter value is mutually exclusive with parameters **remote_ip_prefix** and **remote_group_id**.                                                                                                                                                |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id               | String                | -  Specifies the ID of the project to which the security group rule belongs.                                                                                                                                                                              |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "security_group": {
           "id": "16b6e77a-08fa-42c7-aa8b-106c048884e6",
           "name": "qq",
           "description": "qq",
           "vpc_id": "3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85",
           "enterprise_project_id": "0aad99bc-f5f6-4f78-8404-c598d76b0ed2",
           "security_group_rules": [
              {
                   "id": "f11a3824-ac19-4fad-b4f1-c5f4a6dd0a80",
                   "tenant_id": "060576782980d5762f9ec014dd2f1148",
                   "security_group_id": "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
                   "remote_group_id": "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
                   "direction": "ingress",
                   "protocol": null,
                   "description": "",
                   "ethertype": "IPv6",
                   "remote_ip_prefix": null,
                   "remote_address_group_id": null,
                   "port_range_max": null,
                   "port_range_min": null
               },
               {
                   "id": "3d6480e8-9ea4-46dc-bb1b-8db190cd5677",
                   "tenant_id": "060576782980d5762f9ec014dd2f1148",
                   "security_group_id": "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
                   "remote_group_id": null,
                   "direction": "egress",
                   "protocol": null,
                   "description": "",
                   "ethertype": "IPv6",
                   "remote_ip_prefix": null,
                   "remote_address_group_id": null,
                   "port_range_max": null,
                   "port_range_min": null
               },
               {
                   "id": "9581f18c-1fdd-43da-ace9-7758a56ef28a",
                   "tenant_id": "060576782980d5762f9ec014dd2f1148",
                   "security_group_id": "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
                   "remote_group_id": null,
                   "direction": "egress",
                   "protocol": null,
                   "description": "",
                   "ethertype": "IPv4",
                   "remote_ip_prefix": null,
                   "remote_address_group_id": null,
                   "port_range_max": null,
                   "port_range_min": null
               },
               {
                   "id": "a3ba270e-e58b-432d-a912-aeb7eace9fb8",
                   "tenant_id": "060576782980d5762f9ec014dd2f1148",
                   "security_group_id": "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
                   "remote_group_id": "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
                   "direction": "ingress",
                   "protocol": null,
                   "description": "",
                   "ethertype": "IPv4",
                   "remote_ip_prefix": null,
                   "remote_address_group_id": null,
                   "port_range_max": null,
                   "port_range_min": null
               }
           ]
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
