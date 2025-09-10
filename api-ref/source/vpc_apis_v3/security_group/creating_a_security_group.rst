:original_name: vpc_apiv3_0010.html

.. _vpc_apiv3_0010:

Creating a Security Group
=========================

Function
--------

A security group is a collection of access control rules for cloud instances, such as cloud servers, containers, and databases, that have the same security requirements and that are mutually trusted within a VPC. You can define different access control rules for a security group, and these rules are then applied to all the instances added to this security group.

Constraints
-----------

By default, a security group only allows instances in it to communicate with each other.

URI
---

POST /v3/{project_id}/vpc/security-groups

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                        |
   +=================+=================+=================+====================================================================+
   | project_id      | Yes             | String          | -  Definition: ID of the project that a security group belongs to. |
   |                 |                 |                 |                                                                    |
   |                 |                 |                 | -  Range: None                                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+---------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                        | Description                                                                                                                                                                                                                                                              |
   +=================+=================+=============================================================================================+==========================================================================================================================================================================================================================================================================+
   | dry_run         | No              | Boolean                                                                                     | -  Definition: Whether to only send the check request.                                                                                                                                                                                                                   |
   |                 |                 |                                                                                             |                                                                                                                                                                                                                                                                          |
   |                 |                 |                                                                                             | -  Constraints: None                                                                                                                                                                                                                                                     |
   |                 |                 |                                                                                             |                                                                                                                                                                                                                                                                          |
   |                 |                 |                                                                                             | -  Range:                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                                             |                                                                                                                                                                                                                                                                          |
   |                 |                 |                                                                                             |    -  **true**: A check request will be sent and no security group will be created. Check items include mandatory parameters, request format, and constraints. If the check fails, an error will be returned. If the check succeeds, response code 202 will be returned. |
   |                 |                 |                                                                                             |                                                                                                                                                                                                                                                                          |
   |                 |                 |                                                                                             |    -  **false**: A request will be sent and a security group will be created.                                                                                                                                                                                            |
   |                 |                 |                                                                                             |                                                                                                                                                                                                                                                                          |
   |                 |                 |                                                                                             | -  Default Value: **false**                                                                                                                                                                                                                                              |
   +-----------------+-----------------+---------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group  | Yes             | :ref:`CreateSecurityGroupOption <vpc_apiv3_0010__request_createsecuritygroupoption>` object | -  Definition: Request body for creating a security group.                                                                                                                                                                                                               |
   |                 |                 |                                                                                             |                                                                                                                                                                                                                                                                          |
   |                 |                 |                                                                                             | -  Constraints: None                                                                                                                                                                                                                                                     |
   |                 |                 |                                                                                             |                                                                                                                                                                                                                                                                          |
   |                 |                 |                                                                                             | -  Range: None                                                                                                                                                                                                                                                           |
   |                 |                 |                                                                                             |                                                                                                                                                                                                                                                                          |
   |                 |                 |                                                                                             | -  Default Value: None                                                                                                                                                                                                                                                   |
   +-----------------+-----------------+---------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0010__request_createsecuritygroupoption:

.. table:: **Table 3** CreateSecurityGroupOption

   +-----------------------+-----------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type                                                                    | Description                                                                                                                                                         |
   +=======================+=================+=========================================================================+=====================================================================================================================================================================+
   | name                  | Yes             | String                                                                  | -  Definition: Name of a security group.                                                                                                                            |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         | -  Constraints: The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                 |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         | -  Range: None                                                                                                                                                      |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         | -  Default Value: None                                                                                                                                              |
   +-----------------------+-----------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | No              | String                                                                  | -  Definition: Description of a security group.                                                                                                                     |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         | -  Constraints: The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                                       |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         | -  Range: None                                                                                                                                                      |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         | -  Default Value: None                                                                                                                                              |
   +-----------------------+-----------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | String                                                                  | -  Definition: ID of the enterprise project that a security group belongs to.                                                                                       |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         | -  Constraints:                                                                                                                                                     |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         |    -  The value can contain a maximum of 36 bytes.                                                                                                                  |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         |    -  The value is **0** or a string in UUID format with hyphens (-).                                                                                               |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         | -  Range: None                                                                                                                                                      |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         | -  Default Value: **0** (default enterprise project)                                                                                                                |
   +-----------------------+-----------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | No              | Array of :ref:`RequestTag <vpc_apiv3_0010__request_requesttag>` objects | -  Definition: Tags of a security group, including tag keys and tag values, which can be used to classify and identify resources. For details, see the tag objects. |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         | -  Constraints: A maximum of 20 tag key-value pairs are supported.                                                                                                  |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         | -  Range: None                                                                                                                                                      |
   |                       |                 |                                                                         |                                                                                                                                                                     |
   |                       |                 |                                                                         | -  Default Value: None                                                                                                                                              |
   +-----------------------+-----------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0010__request_requesttag:

.. table:: **Table 4** RequestTag

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                      |
   +=================+=================+=================+==================================================================================+
   | key             | Yes             | String          | -  Definition: Tag key.                                                          |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 | -  Constraints: None                                                             |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 | -  Range:                                                                        |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 |    -  Each key can contain up to 36 Unicode characters and cannot be left blank. |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 |    -  Each key value of a resource must be unique.                               |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 |    -  The value can contain:                                                     |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 |       -  Letters                                                                 |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 |       -  Digits                                                                  |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 |       -  Special characters: underscores (_) ,at signs (@), and hyphens (-)      |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 | -  Default Value: None                                                           |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------+
   | value           | Yes             | String          | -  Definition: Tag value.                                                        |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 | -  Constraints: None                                                             |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 | -  Range:                                                                        |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 |    -  Each value can contain up to 43 Unicode characters and can be left blank.  |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 |    -  The value can contain:                                                     |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 |       -  Letters                                                                 |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 |       -  Digits                                                                  |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 |       -  Special characters: underscore (_), at signs (@), and hyphen (-)        |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 | -  Default Value: None                                                           |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 5** Response body parameters

   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Parameter             | Type                                                                         | Description                                                 |
   +=======================+==============================================================================+=============================================================+
   | request_id            | String                                                                       | -  Definition: Request ID.                                  |
   |                       |                                                                              |                                                             |
   |                       |                                                                              | -  Range: None                                              |
   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------+
   | security_group        | :ref:`SecurityGroupInfo <vpc_apiv3_0010__response_securitygroupinfo>` object | -  Definition: Response body for creating a security group. |
   |                       |                                                                              |                                                             |
   |                       |                                                                              | -  Range: None                                              |
   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------+

.. _vpc_apiv3_0010__response_securitygroupinfo:

.. table:: **Table 6** SecurityGroupInfo

   +-----------------------+----------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                   | Description                                                                                                                                                         |
   +=======================+========================================================================================+=====================================================================================================================================================================+
   | id                    | String                                                                                 | -  Definition: ID of a security group. After a security group is created, a security group ID is generated, which uniquely identifies the security group.           |
   |                       |                                                                                        |                                                                                                                                                                     |
   |                       |                                                                                        | -  Range: The value is in UUID format with hyphens (-).                                                                                                             |
   +-----------------------+----------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                                 | -  Definition: Name of a security group.                                                                                                                            |
   |                       |                                                                                        |                                                                                                                                                                     |
   |                       |                                                                                        | -  Range: The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                       |
   +-----------------------+----------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                                 | -  Definition: Description of a security group.                                                                                                                     |
   |                       |                                                                                        |                                                                                                                                                                     |
   |                       |                                                                                        | -  Range: The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                                             |
   +-----------------------+----------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                                                 | -  Definition: ID of the project that a security group belongs to.                                                                                                  |
   |                       |                                                                                        |                                                                                                                                                                     |
   |                       |                                                                                        | -  Range: None                                                                                                                                                      |
   +-----------------------+----------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                                 | -  Definition: Time when a security group was created.                                                                                                              |
   |                       |                                                                                        |                                                                                                                                                                     |
   |                       |                                                                                        | -  Range: UTC time in the format of yyyy-MM-ddTHH:mm:ssZ                                                                                                            |
   +-----------------------+----------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                                 | -  Definition: Time when a security group was updated.                                                                                                              |
   |                       |                                                                                        |                                                                                                                                                                     |
   |                       |                                                                                        | -  Range: UTC time in the format of yyyy-MM-ddTHH:mm:ssZ                                                                                                            |
   +-----------------------+----------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | String                                                                                 | -  Definition: ID of the enterprise project that a security group belongs to.                                                                                       |
   |                       |                                                                                        |                                                                                                                                                                     |
   |                       |                                                                                        | -  Range: The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). **0** indicates the default enterprise project.  |
   +-----------------------+----------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Array of :ref:`ResponseTag <vpc_apiv3_0010__response_responsetag>` objects             | -  Definition: Tags of a security group, including tag keys and tag values, which can be used to classify and identify resources. For details, see the tag objects. |
   |                       |                                                                                        |                                                                                                                                                                     |
   |                       |                                                                                        | -  Range: None                                                                                                                                                      |
   +-----------------------+----------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_rules  | Array of :ref:`SecurityGroupRule <vpc_apiv3_0010__response_securitygrouprule>` objects | -  Definition: Security group rule list.                                                                                                                            |
   |                       |                                                                                        |                                                                                                                                                                     |
   |                       |                                                                                        | -  Range: None                                                                                                                                                      |
   +-----------------------+----------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0010__response_responsetag:

.. table:: **Table 7** ResponseTag

   +-----------------------+-----------------------+----------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                      |
   +=======================+=======================+==================================================================================+
   | key                   | String                | -  Definition: Tag key.                                                          |
   |                       |                       |                                                                                  |
   |                       |                       | -  Range:                                                                        |
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
   | value                 | String                | -  Definition: Tag value.                                                        |
   |                       |                       |                                                                                  |
   |                       |                       | -  Range:                                                                        |
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

.. _vpc_apiv3_0010__response_securitygrouprule:

.. table:: **Table 8** SecurityGroupRule

   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Type                  | Description                                                                                                                                                                                                                                                          |
   +=========================+=======================+======================================================================================================================================================================================================================================================================+
   | id                      | String                | -  Definition: ID of a security group rule. After a security group rule is created, a security group rule ID is generated, which uniquely identifies the security group rule.                                                                                        |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range: The value is in UUID format with hyphens (-).                                                                                                                                                                                                              |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description             | String                | -  Definition: Description of a security group rule.                                                                                                                                                                                                                 |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range: The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                                                                                                                                              |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id       | String                | -  Definition: ID of the security group that a security group rule belongs to.                                                                                                                                                                                       |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range: None                                                                                                                                                                                                                                                       |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | direction               | String                | -  Definition: Inbound or outbound direction of a security group rule.                                                                                                                                                                                               |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range:                                                                                                                                                                                                                                                            |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       |    -  **ingress**: inbound direction                                                                                                                                                                                                                                 |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       |    -  **egress**: outbound direction                                                                                                                                                                                                                                 |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol                | String                | -  Definition: Communication protocol of a security group rule.                                                                                                                                                                                                      |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range:                                                                                                                                                                                                                                                            |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       |    -  **icmp**                                                                                                                                                                                                                                                       |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       |    -  **tcp**                                                                                                                                                                                                                                                        |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       |    -  **udp**                                                                                                                                                                                                                                                        |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       |    -  **icmpv6**                                                                                                                                                                                                                                                     |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       |    -  IP protocol number                                                                                                                                                                                                                                             |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ethertype               | String                | -  Definition: IP address version of a security group rule.                                                                                                                                                                                                          |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range:                                                                                                                                                                                                                                                            |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       |    -  IPv4                                                                                                                                                                                                                                                           |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       |    -  IPv6                                                                                                                                                                                                                                                           |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | multiport               | String                | -  Definition: Port range of a security group rule.                                                                                                                                                                                                                  |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range: The value can be a single port (80), a port range (1-30), or inconsecutive ports separated by commas (22,3389,80).                                                                                                                                         |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action                  | String                | -  Definition: Action of a security group rule.                                                                                                                                                                                                                      |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range:                                                                                                                                                                                                                                                            |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       |    -  **allow**                                                                                                                                                                                                                                                      |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       |    -  **deny**                                                                                                                                                                                                                                                       |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | priority                | Integer               | -  Definition: Priority of a security group rule.                                                                                                                                                                                                                    |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range: The value is from 1 to 100. The value 1 indicates the highest priority.                                                                                                                                                                                    |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_group_id         | String                | -  Definition: ID of the remote security group of a security group rule. If the action of the rule is **allow**, the traffic from the remote security group is allowed. If the action of the rule is **deny**, the traffic from the remote security group is denied. |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range: ID of an existing security group.                                                                                                                                                                                                                          |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_ip_prefix        | String                | -  Definition: Remote IP address of a security group rule.                                                                                                                                                                                                           |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       |    -  If **direction** is set to **egress**, the IP address is the outbound destination and will be accessed by instances in the security group.                                                                                                                     |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       |    -  If **direction** is set to **ingress**, the IP address is the inbound source and will access the instances in the security group.                                                                                                                              |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range: CIDR notation format. If an IP address is transferred in the request, the IP address is automatically formatted with /32 as the subnet mask, for example, 192.168.21.45/32.                                                                                |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_address_group_id | String                | -  Definition: ID of the remote IP address group of a security group rule.                                                                                                                                                                                           |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range: ID of an existing IP address group.                                                                                                                                                                                                                        |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at              | String                | -  Definition: Time when a security group rule was created.                                                                                                                                                                                                          |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range: UTC time in the format of yyyy-MM-ddTHH:mm:ssZ                                                                                                                                                                                                             |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at              | String                | -  Definition: Time when a security group rule was updated.                                                                                                                                                                                                          |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range: UTC time in the format of yyyy-MM-ddTHH:mm:ssZ                                                                                                                                                                                                             |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id              | String                | -  Definition: ID of the project that a security group rule belongs to.                                                                                                                                                                                              |
   |                         |                       |                                                                                                                                                                                                                                                                      |
   |                         |                       | -  Range: None                                                                                                                                                                                                                                                       |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 202**

.. table:: **Table 9** Response body parameters

   +-----------------------+-----------------------+-------------------------------+
   | Parameter             | Type                  | Description                   |
   +=======================+=======================+===============================+
   | request_id            | String                | -  Definition: Request ID.    |
   |                       |                       |                               |
   |                       |                       | -  Range: None                |
   +-----------------------+-----------------------+-------------------------------+
   | error_msg             | String                | -  Definition: Error message. |
   |                       |                       |                               |
   |                       |                       | -  Range: None                |
   +-----------------------+-----------------------+-------------------------------+
   | error_code            | String                | -  Definition: Error code.    |
   |                       |                       |                               |
   |                       |                       | -  Range: None                |
   +-----------------------+-----------------------+-------------------------------+

Example Requests
----------------

-  Create a security group, set its name to **security_group_1** and description to **security group description**, and specify the request as a prefight request.

   .. code-block:: text

      POST https://{Endpoint}/v3/{project_id}/vpc/security-groups

      {
        "security_group" : {
          "name" : "security_group_1",
          "description" : "security group description"
        },
        "dry_run" : true
      }

-  Create a security group and set its name to *security_group_1*\ \* and description to **security group description**.

   .. code-block:: text

      POST https://{Endpoint}/v3/{project_id}/vpc/security-groups

      {
        "security_group" : {
          "name" : "security_group_1",
          "description" : "security group description"
        }
      }

Example Responses
-----------------

**Status code: 201**

Normal response to the POST operation. For more status codes, see :ref:`Status Code <vpc_api_0002>`.

.. code-block::

   {
     "security_group" : {
       "id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
       "name" : "security_group_1",
       "project_id" : "060576782980d5762f9ec014dd2f1148",
       "description" : "security group description",
       "enterprise_project_id" : "0",
       "tags" : [ ],
       "security_group_rules" : [ {
         "id" : "f11a3824-ac19-4fad-b4f1-c5f4a6dd0a80",
         "project_id" : "060576782980d5762f9ec014dd2f1148",
         "security_group_id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
         "remote_group_id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
         "direction" : "ingress",
         "protocol" : null,
         "description" : "",
         "created_at" : "2020-07-09T05:56:27Z",
         "updated_at" : "2020-07-09T05:56:27Z",
         "ethertype" : "IPv6",
         "remote_ip_prefix" : null,
         "multiport" : null,
         "remote_address_group_id" : null,
         "action" : "allow",
         "priority" : 100
       }, {
         "id" : "3d6480e8-9ea4-46dc-bb1b-8db190cd5677",
         "project_id" : "060576782980d5762f9ec014dd2f1148",
         "security_group_id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
         "remote_group_id" : null,
         "direction" : "egress",
         "protocol" : null,
         "description" : "",
         "created_at" : "2020-07-09T05:56:27Z",
         "updated_at" : "2020-07-09T05:56:27Z",
         "ethertype" : "IPv6",
         "remote_ip_prefix" : null,
         "multiport" : null,
         "remote_address_group_id" : null,
         "action" : "allow",
         "priority" : 100
       }, {
         "id" : "9581f18c-1fdd-43da-ace9-7758a56ef28a",
         "project_id" : "060576782980d5762f9ec014dd2f1148",
         "security_group_id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
         "remote_group_id" : null,
         "direction" : "egress",
         "protocol" : null,
         "description" : "",
         "created_at" : "2020-07-09T05:56:27Z",
         "updated_at" : "2020-07-09T05:56:27Z",
         "ethertype" : "IPv4",
         "remote_ip_prefix" : null,
         "multiport" : null,
         "remote_address_group_id" : null,
         "action" : "allow",
         "priority" : 100
       }, {
         "id" : "a3ba270e-e58b-432d-a912-aeb7eace9fb8",
         "project_id" : "060576782980d5762f9ec014dd2f1148",
         "security_group_id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
         "remote_group_id" : "69c999ad-d9ef-4d79-94fd-35e6ceb75325",
         "direction" : "ingress",
         "protocol" : null,
         "description" : "",
         "created_at" : "2020-07-09T05:56:27Z",
         "updated_at" : "2020-07-09T05:56:27Z",
         "ethertype" : "IPv4",
         "remote_ip_prefix" : null,
         "multiport" : null,
         "remote_address_group_id" : null,
         "action" : "allow",
         "priority" : 100
       } ],
       "created_at" : "2020-07-09T05:56:27Z",
       "updated_at" : "2020-07-09T05:56:27Z"
     },
     "request_id" : "a8cf4f79ca3c22ca685e7e8872e8c20b"
   }

**Status code: 202**

Normal response for the specified pre-check request of API V3. For more status codes, see :ref:`Status Code <vpc_api_0002>`.

.. code-block::

   {
     "error_msg" : "Request validation has been passed with dry run...",
     "error_code" : "SYS.0202",
     "request_id" : "cfd81aea3f59eac7128dba4b36d516c8"
   }

Status Codes
------------

+-------------+------------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                  |
+=============+==============================================================================================================================+
| 201         | Normal response to the POST operation. For more status codes, see :ref:`Status Code <vpc_api_0002>`.                         |
+-------------+------------------------------------------------------------------------------------------------------------------------------+
| 202         | Normal response for the specified pre-check request of API V3. For more status codes, see :ref:`Status Code <vpc_api_0002>`. |
+-------------+------------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
