:original_name: vpc_apiv3_0012.html

.. _vpc_apiv3_0012:

Querying the Details of a Security Group
========================================

Function
--------

This API is used to query the details of a security group.

URI
---

GET /v3/{project_id}/vpc/security-groups/{security_group_id}

.. table:: **Table 1** Path Parameters

   ================= ========= ====== ==================
   Parameter         Mandatory Type   Description
   ================= ========= ====== ==================
   project_id        Yes       String Project ID.
   security_group_id Yes       String Security group ID.
   ================= ========= ====== ==================

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +----------------+------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter      | Type                                                                         | Description                                   |
   +================+==============================================================================+===============================================+
   | request_id     | String                                                                       | Request ID.                                   |
   +----------------+------------------------------------------------------------------------------+-----------------------------------------------+
   | security_group | :ref:`SecurityGroupInfo <vpc_apiv3_0012__response_securitygroupinfo>` object | Response for querying security group details. |
   +----------------+------------------------------------------------------------------------------+-----------------------------------------------+

.. _vpc_apiv3_0012__response_securitygroupinfo:

.. table:: **Table 3** SecurityGroupInfo

   +-----------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                   | Description                                                                                                                                                          |
   +=======================+========================================================================================+======================================================================================================================================================================+
   | id                    | String                                                                                 | -  Security group ID, which uniquely identifies the security group.                                                                                                  |
   |                       |                                                                                        |                                                                                                                                                                      |
   |                       |                                                                                        | -  The value is in UUID format with hyphens (-).                                                                                                                     |
   +-----------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                                 | -  Security group name.                                                                                                                                              |
   |                       |                                                                                        |                                                                                                                                                                      |
   |                       |                                                                                        | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                               |
   +-----------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                                 | -  Description about the security group.                                                                                                                             |
   |                       |                                                                                        |                                                                                                                                                                      |
   |                       |                                                                                        | -  The value can contain up to 255 characters and cannot contain angle brackets (< or >).                                                                            |
   +-----------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                                                 | -  ID of the project to which the security group belongs.                                                                                                            |
   +-----------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                                 | -  Time when the security group was created.                                                                                                                         |
   |                       |                                                                                        |                                                                                                                                                                      |
   |                       |                                                                                        | -  The value is a UTC time in the format of *yyyy-MM-ddTHH:mm:ssZ*.                                                                                                  |
   +-----------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                                 | -  Time when the security group was updated.                                                                                                                         |
   |                       |                                                                                        |                                                                                                                                                                      |
   |                       |                                                                                        | -  The value is a UTC time in the format of *yyyy-MM-ddTHH:mm:ssZ*.                                                                                                  |
   +-----------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | String                                                                                 | -  ID of the enterprise project to which the security group belongs.                                                                                                 |
   |                       |                                                                                        |                                                                                                                                                                      |
   |                       |                                                                                        | -  The project ID can be **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). **0** indicates the default enterprise project. |
   +-----------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Array of :ref:`Tag <vpc_apiv3_0012__response_tag>` objects                             | -  Security group tags. For details, see the tag objects.                                                                                                            |
   |                       |                                                                                        |                                                                                                                                                                      |
   |                       |                                                                                        | -  Value range: 0 to 20 key-value pairs.                                                                                                                             |
   +-----------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_rules  | Array of :ref:`SecurityGroupRule <vpc_apiv3_0012__response_securitygrouprule>` objects | Security group rules.                                                                                                                                                |
   +-----------------------+----------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0012__response_tag:

.. table:: **Table 4** Tag

   +-----------------------+-----------------------+----------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                      |
   +=======================+=======================+==================================================================================+
   | key                   | String                | -  Tag key.                                                                      |
   |                       |                       |                                                                                  |
   |                       |                       | -  Value ranges:                                                                 |
   |                       |                       |                                                                                  |
   |                       |                       |    -  Each key can contain up to 36 Unicode characters and cannot be left blank. |
   |                       |                       |                                                                                  |
   |                       |                       |    -  Each key value of a resource must be unique.                               |
   |                       |                       |                                                                                  |
   |                       |                       |    -  The value can contain:                                                     |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Letters                                                                 |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Digits                                                                  |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Special characters: underscores (_) ,at signs (@), and hyphens (-)      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------+
   | value                 | String                | -  Tag value.                                                                    |
   |                       |                       |                                                                                  |
   |                       |                       | -  Value range:                                                                  |
   |                       |                       |                                                                                  |
   |                       |                       |    -  Each value can contain up to 43 Unicode characters and can be left blank.  |
   |                       |                       |                                                                                  |
   |                       |                       |    -  The value can contain:                                                     |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Letters                                                                 |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Digits                                                                  |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Special characters: underscore (_), at signs (@), and hyphen (-)        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------+

.. _vpc_apiv3_0012__response_securitygrouprule:

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

Querying the details of a security group.

.. code-block:: text

   GET https://{Endpoint}/v3/{project_id}/vpc/security-groups/1d8b19c7-7c56-48f7-a99b-4b40eb390967

Example Responses
-----------------

**Status code: 200**

Normal response to the GET operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

-  .. code-block::

      {
        "security_group" : {
          "id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
          "name" : "security_group_1",
          "project_id" : "060576782980d5762f9ec014dd2f1148",
          "description" : "security group description",
          "enterprise_project_id" : 0,
          "tags" : [ {
            "key" : "a",
            "value" : "b"
          } ],
          "security_group_rules" : [ {
            "id" : "f11a3824-ac19-4fad-b4f1-c5f4a6dd0a80",
            "project_id" : "060576782980d5762f9ec014dd2f1148",
            "security_group_id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
            "remote_group_id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
            "direction" : "ingress",
            "description" : "",
            "created_at" : "2020-07-09T05:56:27.000+00:00",
            "updated_at" : "2020-07-09T05:56:27.000+00:00",
            "ethertype" : "IPv6",
            "action" : "allow",
            "priority" : 100,
            "protocol" : null,
            "multiport" : null,
            "remote_ip_prefix" : null,
            "remote_address_group_id" : null
          }, {
            "id" : "3d6480e8-9ea4-46dc-bb1b-8db190cd5677",
            "project_id" : "060576782980d5762f9ec014dd2f1148",
            "security_group_id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
            "direction" : "egress",
            "description" : "",
            "created_at" : "2020-07-09T05:56:27.000+00:00",
            "updated_at" : "2020-07-09T05:56:27.000+00:00",
            "ethertype" : "IPv6",
            "action" : "allow",
            "priority" : 100,
            "protocol" : null,
            "multiport" : null,
            "remote_ip_prefix" : null,
            "remote_group_id" : null,
            "remote_address_group_id" : null
          }, {
            "id" : "9581f18c-1fdd-43da-ace9-7758a56ef28a",
            "project_id" : "060576782980d5762f9ec014dd2f1148",
            "security_group_id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
            "direction" : "egress",
            "description" : "",
            "created_at" : "2020-07-09T05:56:27.000+00:00",
            "updated_at" : "2020-07-09T05:56:27.000+00:00",
            "ethertype" : "IPv4",
            "action" : "allow",
            "priority" : 100,
            "protocol" : null,
            "multiport" : null,
            "remote_ip_prefix" : null,
            "remote_group_id" : null,
            "remote_address_group_id" : null
          }, {
            "id" : "a3ba270e-e58b-432d-a912-aeb7eace9fb8",
            "project_id" : "060576782980d5762f9ec014dd2f1148",
            "security_group_id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
            "remote_group_id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
            "direction" : "ingress",
            "description" : "",
            "created_at" : "2020-07-09T05:56:27.000+00:00",
            "updated_at" : "2020-07-09T05:56:27.000+00:00",
            "ethertype" : "IPv4",
            "action" : "allow",
            "priority" : 100,
            "protocol" : null,
            "multiport" : null,
            "remote_ip_prefix" : null,
            "remote_address_group_id" : null
          } ],
          "created_at" : "2020-07-09T05:56:27.000+00:00",
          "updated_at" : "2020-07-09T05:56:27.000+00:00"
        },
        "request_id" : "a8cf4f79ca3c22ca685e7e8872e8c20b"
      }

Status Codes
------------

+-------------+------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                          |
+=============+======================================================================================================+
| 200         | Normal response to the GET operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`. |
+-------------+------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
