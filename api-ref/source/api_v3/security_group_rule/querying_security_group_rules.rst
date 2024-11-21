:original_name: vpc_apiv3_0017.html

.. _vpc_apiv3_0017:

Querying Security Group Rules
=============================

Function
--------

This API is used to query security group rules.

URI
---

GET /v3/{project_id}/vpc/security-group-rules

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Mandatory       | Type              | Description                                                                                                                                                              |
   +=========================+=================+===================+==========================================================================================================================================================================+
   | limit                   | No              | Integer           | -  Specifies the number of records returned on each page.                                                                                                                |
   |                         |                 |                   |                                                                                                                                                                          |
   |                         |                 |                   | -  Value range: 0 to 2000.                                                                                                                                               |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker                  | No              | String            | Start resource ID of pagination query. If the parameter is left blank, only resources on the first page are queried.                                                     |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                      | No              | Array of strings  | -  ID of the security group rule. Multiple IDs can be specified for filtering.                                                                                           |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id       | No              | Array of strings  | -  ID of the security group to which the security group rule belongs. Multiple IDs can be specified for filtering.                                                       |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol                | No              | Array of strings  | -  Protocol specified in the security group rule. Multiple protocols can be specified for filtering.                                                                     |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description             | No              | Array of strings  | -  Supplementary information about the security group. This field can be used to precisely filter security groups. Multiple descriptions can be specified for filtering. |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_group_id         | No              | Array of strings  | -  ID of the remote security group. Multiple IDs can be specified for filtering.                                                                                         |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | direction               | No              | String            | -  Access control direction specified in the security group rule.                                                                                                        |
   |                         |                 |                   |                                                                                                                                                                          |
   |                         |                 |                   | -  The value can be **ingress** (inbound direction) or **egress** (outbound direction).                                                                                  |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action                  | No              | String            | -  Action of the security group rule.                                                                                                                                    |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_ip_prefix        | No              | String            | -  Remote IP address.                                                                                                                                                    |
   |                         |                 |                   |                                                                                                                                                                          |
   |                         |                 |                   | -  The value must be in CIDR format.                                                                                                                                     |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | priority                | No              | Array of integers | Security group rule priority. Multiple priorities can be specified for filtering.                                                                                        |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ethertype               | No              | Array of strings  | Type of the security group rule. Value range: **IPv4**, **ipv4**, **IPv6**, or **ipv6**.                                                                                 |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id              | No              | Array of strings  | Project ID.                                                                                                                                                              |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_address_group_id | No              | Array of strings  | ID of the remote IP address group. Multiple IDs can be specified for filtering.                                                                                          |
   +-------------------------+-----------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +----------------------+----------------------------------------------------------------------------------------+----------------------------------------+
   | Parameter            | Type                                                                                   | Description                            |
   +======================+========================================================================================+========================================+
   | request_id           | String                                                                                 | Request ID.                            |
   +----------------------+----------------------------------------------------------------------------------------+----------------------------------------+
   | security_group_rules | Array of :ref:`SecurityGroupRule <vpc_apiv3_0017__response_securitygrouprule>` objects | Response body of security group rules. |
   +----------------------+----------------------------------------------------------------------------------------+----------------------------------------+
   | page_info            | :ref:`PageInfo <vpc_apiv3_0017__response_pageinfo>` object                             | Pagination information.                |
   +----------------------+----------------------------------------------------------------------------------------+----------------------------------------+

.. _vpc_apiv3_0017__response_securitygrouprule:

.. table:: **Table 4** SecurityGroupRule

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

.. _vpc_apiv3_0017__response_pageinfo:

.. table:: **Table 5** PageInfo

   +-----------------+---------+---------------------------------------------------------------------------------------------+
   | Parameter       | Type    | Description                                                                                 |
   +=================+=========+=============================================================================================+
   | previous_marker | String  | First record on the current page.                                                           |
   +-----------------+---------+---------------------------------------------------------------------------------------------+
   | current_count   | Integer | Total number of records on the current page.                                                |
   +-----------------+---------+---------------------------------------------------------------------------------------------+
   | next_marker     | String  | Last record on the current page. This parameter does not exist if the page is the last one. |
   +-----------------+---------+---------------------------------------------------------------------------------------------+

Example Requests
----------------

Query security group rules.

.. code-block:: text

   GET https://{Endpoint}/v3/{project_id}/vpc/security-group-rules

Example Responses
-----------------

**Status code: 200**

Normal response to the GET operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

-  .. code-block::

      {
        "request_id" : "80747d36e3376c0894ba8f9a9156355d",
        "security_group_rules" : [ {
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
          "multiport" : 333,
          "action" : "allow",
          "priority" : 1,
          "remote_group_id" : null,
          "remote_address_group_id" : null
        } ]
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
