:original_name: vpc_apiv3_0016.html

.. _vpc_apiv3_0016:

Creating a Security Group Rule
==============================

Function
--------

This API is used to create a security group rule.

URI
---

POST /v3/{project_id}/vpc/security-group-rules

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +---------------------+-----------------+-----------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type                                                                                                | Description                                                                                                                                                                                                                                                                               |
   +=====================+=================+=====================================================================================================+===========================================================================================================================================================================================================================================================================================+
   | dry_run             | No              | Boolean                                                                                             | -  Whether to only send the check request.                                                                                                                                                                                                                                                |
   |                     |                 |                                                                                                     |                                                                                                                                                                                                                                                                                           |
   |                     |                 |                                                                                                     | -  The value can be:                                                                                                                                                                                                                                                                      |
   |                     |                 |                                                                                                     |                                                                                                                                                                                                                                                                                           |
   |                     |                 |                                                                                                     |    -  **true**: A check request will be sent and no security group rule will be created. Check items include mandatory parameters, request format, and permission verification. If the check fails, an error will be returned. If the check succeeds, response code 202 will be returned. |
   |                     |                 |                                                                                                     |                                                                                                                                                                                                                                                                                           |
   |                     |                 |                                                                                                     |    -  **false** (default value): A request will be sent and a security group rule will be created.                                                                                                                                                                                        |
   +---------------------+-----------------+-----------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_rule | Yes             | :ref:`CreateSecurityGroupRuleOption <vpc_apiv3_0016__request_createsecuritygroupruleoption>` object | Request body for creating a security group rule.                                                                                                                                                                                                                                          |
   +---------------------+-----------------+-----------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0016__request_createsecuritygroupruleoption:

.. table:: **Table 3** CreateSecurityGroupRuleOption

   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                                                                                             |
   +===================+=================+=================+=========================================================================================================================================================================================================+
   | security_group_id | Yes             | String          | -  ID of the security group to which the security group rule belongs.                                                                                                                                   |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description       | No              | String          | -  Provides supplementary information about the security group.                                                                                                                                         |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                                                                                        |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | direction         | Yes             | String          | -  Inbound or outbound direction of a security group rule.                                                                                                                                              |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  The value can be:                                                                                                                                                                                    |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 |    -  **ingress**: inbound direction.                                                                                                                                                                   |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 |    -  **egress**: outbound direction.                                                                                                                                                                   |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ethertype         | No              | String          | -  IP version.                                                                                                                                                                                          |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  The value can be **IPv4** or **IPv6**.                                                                                                                                                               |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  If you do not set this parameter, **IPv4** is used by default.                                                                                                                                       |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol          | No              | String          | -  Protocol type.                                                                                                                                                                                       |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  The value can be **icmp**, **tcp**, **udp**, **icmpv6** or an IP number (0 to 255).                                                                                                                  |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  Constraints:                                                                                                                                                                                         |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 |    -  If the parameter is left blank, all protocols are supported.                                                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 |    -  When the protocol is **icmpv6**, IP version should be **IPv6**.                                                                                                                                   |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 |    -  When the protocol is **icmp**, IP version should be **IPv4**.                                                                                                                                     |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | multiport         | No              | String          | -  Port or port range                                                                                                                                                                                   |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  The value can be a single port (80), a port range (1-30), or inconsecutive ports separated by commas (22,3389,80).                                                                                   |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  The port is from 1 to 65535.                                                                                                                                                                         |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_ip_prefix  | No              | String          | -  Remote IP address. If **direction** is set to **egress**, the parameter specifies the source IP address. If **direction** is set to **ingress**, the parameter specifies the destination IP address. |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  The value is an IP address or a CIDR block.                                                                                                                                                          |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  Constraints:                                                                                                                                                                                         |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 |    -  The parameter is mutually exclusive with parameter **remote_group_id**.                                                                                                                           |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 |    -  If this parameter is left blank, the remote IP address is not limited, and the traffic from all remote IP addresses is allowed or rejected.                                                       |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_group_id   | No              | String          | -  ID of the remote security group, which allows or denies traffic to and from the security group.                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  Value range: ID of an existing security group.                                                                                                                                                       |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  The parameter is mutually exclusive with parameter **remote_ip_prefix**.                                                                                                                             |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action            | No              | String          | -  Action of the security group rule.                                                                                                                                                                   |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  The value can be:                                                                                                                                                                                    |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 |    -  **allow**                                                                                                                                                                                         |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 |    -  **deny**                                                                                                                                                                                          |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  The default value is **allow**.                                                                                                                                                                      |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | priority          | No              | String          | -  Rule priority in a security group.                                                                                                                                                                   |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  The value is from **1** to **100**. The value **1** indicates the highest priority.                                                                                                                  |
   |                   |                 |                 |                                                                                                                                                                                                         |
   |                   |                 |                 | -  The default value is **1**.                                                                                                                                                                          |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   +---------------------+------------------------------------------------------------------------------+---------------------------------------------------+
   | Parameter           | Type                                                                         | Description                                       |
   +=====================+==============================================================================+===================================================+
   | request_id          | String                                                                       | Request ID.                                       |
   +---------------------+------------------------------------------------------------------------------+---------------------------------------------------+
   | security_group_rule | :ref:`SecurityGroupRule <vpc_apiv3_0016__response_securitygrouprule>` object | Response body for creating a security group rule. |
   +---------------------+------------------------------------------------------------------------------+---------------------------------------------------+

.. _vpc_apiv3_0016__response_securitygrouprule:

.. table:: **Table 5** SecurityGroupRule

   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Type                  | Description                                                                                                           |
   +=========================+=======================+=======================================================================================================================+
   | id                      | String                | -  Security group rule ID, which uniquely identifies the security group rule.                                         |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  The value is in UUID format with hyphens (-).                                                                      |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | description             | String                | -  Provides supplementary information about the security group rule.                                                  |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                      |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | security_group_id       | String                | -  ID of the security group to which the security group rule belongs.                                                 |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | direction               | String                | -  Inbound or outbound direction of a security group rule.                                                            |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  The value can be:                                                                                                  |
   |                         |                       |                                                                                                                       |
   |                         |                       |    -  ingress: inbound direction.                                                                                     |
   |                         |                       |                                                                                                                       |
   |                         |                       |    -  egress: outbound direction.                                                                                     |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | protocol                | String                | -  Protocol type                                                                                                      |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  The value can be **icmp**, **tcp**, **udp**, **icmpv6**, or an IP number.                                          |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  Constraints:                                                                                                       |
   |                         |                       |                                                                                                                       |
   |                         |                       |    -  If the parameter is left blank, all protocols are supported.                                                    |
   |                         |                       |                                                                                                                       |
   |                         |                       |    -  When the protocol is **icmpv6**, IP version should be **IPv6**.                                                 |
   |                         |                       |                                                                                                                       |
   |                         |                       |    -  When the protocol is **icmp**, IP version should be **IPv4**.                                                   |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | ethertype               | String                | -  IP version                                                                                                         |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  The value can be **IPv4** or **IPv6**.                                                                             |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  If you do not set this parameter, **IPv4** is used by default.                                                     |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | multiport               | String                | -  Port or port range                                                                                                 |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  The value can be a single port (80), a port range (1-30), or inconsecutive ports separated by commas (22,3389,80). |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | action                  | String                | -  Action of the security group rule.                                                                                 |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  The value can be: **allow**, **deny**.                                                                             |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  The default value is **deny**.                                                                                     |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | priority                | Integer               | -  Rule priority.                                                                                                     |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  The value is from **1** to **100**. The value **1** indicates the highest priority.                                |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | remote_group_id         | String                | -  ID of the remote security group, which allows or denies traffic to and from the security group.                    |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  Value range: ID of an existing security group.                                                                     |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  The parameter value is mutually exclusive with parameters **remote_ip_prefix** and **remote_address_group_id**.    |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | remote_ip_prefix        | String                | -  Remote IP address.                                                                                                 |
   |                         |                       |                                                                                                                       |
   |                         |                       |    -  If direction is set to **egress**, the parameter specifies the source IP address.                               |
   |                         |                       |                                                                                                                       |
   |                         |                       |    -  If direction is set to **ingress**, the parameter specifies the destination IP address.                         |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  The value is an IP address or a CIDR block.                                                                        |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  Constraints:                                                                                                       |
   |                         |                       |                                                                                                                       |
   |                         |                       |    -  The parameter value is mutually exclusive with parameters **remote_group_id** and **remote_address_group_id**.  |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | remote_address_group_id | String                | -  ID of the remote IP address group.                                                                                 |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  Value range: ID of an existing IP address group                                                                    |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  The parameter value is mutually exclusive with parameters **remote_ip_prefix** and **remote_group_id**.            |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | created_at              | String                | -  Time when the security group rule is created.                                                                      |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  UTC time in the format of *yyyy-MM-ddTHH:mm:ssZ*.                                                                  |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | updated_at              | String                | -  Time when the security group rule is updated.                                                                      |
   |                         |                       |                                                                                                                       |
   |                         |                       | -  UTC time in the format of *yyyy-MM-ddTHH:mm:ssZ*.                                                                  |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | project_id              | String                | -  ID of the project to which the security group rule belongs.                                                        |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Create an inbound rule in the security group whose ID is **1c8d9f94-6022-4518-bb98-e0145fcc7b33**.

.. code-block:: text

   POST https://{Endpoint}/v3/{project_id}/vpc/security-group-rules

   {
     "security_group_rule" : {
       "security_group_id" : "1c8d9f94-6022-4518-bb98-e0145fcc7b33",
       "direction" : "ingress",
       "protocol" : "tcp",
       "description" : "security group rule description",
       "action" : "allow",
       "priority" : 1,
       "multiport" : "33",
       "remote_ip_prefix" : "10.10.0.0/16"
     }
   }

Example Responses
-----------------

**Status code: 201**

Normal response to the POST operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

-  .. code-block::

      {
        "request_id" : "1666b2708aaf849337572d6846dce781",
        "security_group_rule" : {
          "id" : "f626eb24-d8bd-4d26-ae0b-c16bb65730cb",
          "project_id" : "060576782980d5762f9ec014dd2f1148",
          "security_group_id" : "0552091e-b83a-49dd-88a7-4a5c86fd9ec3",
          "direction" : "ingress",
          "protocol" : "tcp",
          "description" : "security group rule description",
          "created_at" : "2020-08-13T07:12:36.000+00:00",
          "updated_at" : "2020-08-13T07:12:36.000+00:00",
          "ethertype" : "IPv4",
          "remote_ip_prefix" : "10.10.0.0/16",
          "multiport" : 33,
          "action" : "allow",
          "priority" : 1,
          "remote_group_id" : null,
          "remote_address_group_id" : null
        }
      }

Status Codes
------------

+-------------+-------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                           |
+=============+=======================================================================================================+
| 201         | Normal response to the POST operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`. |
+-------------+-------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
