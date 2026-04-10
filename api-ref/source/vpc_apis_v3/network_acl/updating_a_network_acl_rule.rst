:original_name: UpdateFirewallRules.html

.. _UpdateFirewallRules:

Updating a Network ACL Rule
===========================

Function
--------

This API is used to update the basic information about a network ACL rule, such as the source address, destination address, source port, and destination port.

URI
---

PUT /v3/{project_id}/vpc/firewalls/{firewall_id}/update-rules

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                     |
   +=================+=================+=================+=================================================================================================================================================================================+
   | firewall_id     | Yes             | String          | **Definition**:                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                 |
   |                 |                 |                 | Network ACL ID. You can call the API :ref:`Querying Network ACLs <listfirewall>` to obtain the ID of the target network ACL, and then use this API to update network ACL rules. |
   |                 |                 |                 |                                                                                                                                                                                 |
   |                 |                 |                 | **Range**:                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                 |
   |                 |                 |                 | N/A                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id      | Yes             | String          | **Definition**:                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                 |
   |                 |                 |                 | ID of the project that the network ACL belongs to.                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                 |
   |                 |                 |                 | **Range**:                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                 |
   |                 |                 |                 | N/A                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                           | Description                                                                                                                                                                                                                                                                 |
   +=================+=================+================================================================================================+=============================================================================================================================================================================================================================================================================+
   | firewall        | Yes             | :ref:`FirewallUpdateRuleOption <updatefirewallrules__request_firewallupdateruleoption>` object | **Definition**:                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | Request body for updating a network ACL rule                                                                                                                                                                                                                                |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | **Constraints**:                                                                                                                                                                                                                                                            |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | N/A                                                                                                                                                                                                                                                                         |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | **Range**:                                                                                                                                                                                                                                                                  |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | N/A                                                                                                                                                                                                                                                                         |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | **Default Value**:                                                                                                                                                                                                                                                          |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | N/A                                                                                                                                                                                                                                                                         |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dry_run         | No              | Boolean                                                                                        | **Definition**:                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | Whether to only check the request.                                                                                                                                                                                                                                          |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | **Constraints**:                                                                                                                                                                                                                                                            |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | N/A                                                                                                                                                                                                                                                                         |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | **Range**:                                                                                                                                                                                                                                                                  |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | -  **true**: A check request will be sent and no network ACL rule will not be updated. Check items include mandatory parameters, request format, and constraints. If the check fails, an error will be returned. If the check succeeds, response code 202 will be returned. |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | -  false: A request will be sent and a network ACL rule will be updated.                                                                                                                                                                                                    |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | **Default Value**:                                                                                                                                                                                                                                                          |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                                                | false                                                                                                                                                                                                                                                                       |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _updatefirewallrules__request_firewallupdateruleoption:

.. table:: **Table 3** FirewallUpdateRuleOption

   +-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                                             | Description                                                                                                                                          |
   +=================+=================+==================================================================================================================+======================================================================================================================================================+
   | ingress_rules   | No              | Array of :ref:`FirewallUpdateRuleItemOption <updatefirewallrules__request_firewallupdateruleitemoption>` objects | **Definition**:                                                                                                                                      |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | Inbound network ACL rules to be updated.                                                                                                             |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | **Constraints**:                                                                                                                                     |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | -  Either **ingress_rules** or **egress_rules** can be specified. That is, either the inbound or outbound rules can be specified for updating rules. |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | -  Currently, only one network ACL rule can be updated at a time.                                                                                    |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | **Range**:                                                                                                                                           |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | N/A                                                                                                                                                  |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | **Default Value**:                                                                                                                                   |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | N/A                                                                                                                                                  |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | egress_rules    | No              | Array of :ref:`FirewallUpdateRuleItemOption <updatefirewallrules__request_firewallupdateruleitemoption>` objects | **Definition**:                                                                                                                                      |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | Outbound network ACL rules to be updated.                                                                                                            |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | **Constraints**:                                                                                                                                     |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | -  Either **ingress_rules** or **egress_rules** can be specified. That is, either the inbound or outbound rules can be specified for updating rules. |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | -  Currently, only one network ACL rule can be updated at a time.                                                                                    |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | **Range**:                                                                                                                                           |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | N/A                                                                                                                                                  |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | **Default Value**:                                                                                                                                   |
   |                 |                 |                                                                                                                  |                                                                                                                                                      |
   |                 |                 |                                                                                                                  | N/A                                                                                                                                                  |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _updatefirewallrules__request_firewallupdateruleitemoption:

.. table:: **Table 4** FirewallUpdateRuleItemOption

   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                    | Mandatory       | Type            | Description                                                                                                                              |
   +==============================+=================+=================+==========================================================================================================================================+
   | id                           | Yes             | String          | **Definition**:                                                                                                                          |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | Network ACL rule ID.                                                                                                                     |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Constraints**:                                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | The value is in UUID format with hyphens (-).                                                                                            |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Range**:                                                                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Default Value**:                                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | name                         | No              | String          | **Definition**:                                                                                                                          |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | Network ACL rule name.                                                                                                                   |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Constraints**:                                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | The value can contain 0 to 255 characters, including letters, digits, underscores (_), hyphens (-), and periods.                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Range**:                                                                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Default Value**:                                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | description                  | No              | String          | **Definition**:                                                                                                                          |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | Supplementary information about the network ACL rule.                                                                                    |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Constraints**:                                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | The value can contain 0 to 255 characters and cannot contain angle brackets (< or >).                                                    |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Range**:                                                                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Default Value**:                                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | action                       | No              | String          | **Definition**:                                                                                                                          |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | Whether a network ACL rule allows or denies traffic.                                                                                     |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Constraints**:                                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Range**:                                                                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  allow: A network ACL rule allows traffic.                                                                                             |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  deny: A network ACL rule denies traffic.                                                                                              |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Default Value**:                                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol                     | No              | String          | **Definition**:                                                                                                                          |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | Communication protocol of a network ACL rule.                                                                                            |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Constraints**:                                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  The protocol cannot be empty.                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  If the protocol is **icmpv6**, IP version should be IPv6.                                                                             |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  If the protocol is **icmp**, IP version should be IPv4.                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  tcp                                                                                                                                   |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  udp                                                                                                                                   |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  icmp                                                                                                                                  |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  icmpv6                                                                                                                                |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  IP protocol number (0-255)                                                                                                            |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  any: any protocol                                                                                                                     |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Range**:                                                                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Default Value**:                                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_version                   | No              | Integer         | **Definition**:                                                                                                                          |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | IP address version of a network ACL rule.                                                                                                |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Constraints**:                                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Range**:                                                                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  4: IPv4 network ACL rule.                                                                                                             |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  6: IPv6 network ACL rule.                                                                                                             |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Default Value**:                                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | source_ip_address            | No              | String          | **Definition**:                                                                                                                          |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | Source IP address or source IP address range of a network ACL rule.                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Constraints**:                                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **source_ip_address** and **source_address_group_id** cannot be specified at the same time.                                              |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Range**:                                                                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Default Value**:                                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | destination_ip_address       | No              | String          | **Definition**:                                                                                                                          |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | Destination IP address or destination IP address range of a network ACL rule.                                                            |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Constraints**:                                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **destination_ip_address** and **destination_address_group_id** cannot be specified at the same time.                                    |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Range**:                                                                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Default Value**:                                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | source_port                  | No              | String          | **Definition**:                                                                                                                          |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | Source port of a network ACL rule.                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Constraints**:                                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  Individual port: for example, 22                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  Consecutive ports: for example, 22-30                                                                                                 |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  Non-consecutive ports: ports and port ranges, such as **22,23-30**. You can specify up to 20 port ranges. Port ranges cannot overlap. |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  All ports: Leave it empty or enter 1-65535.                                                                                           |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Range**:                                                                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Default Value**:                                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | destination_port             | No              | String          | **Definition**:                                                                                                                          |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | Destination port of a network ACL rule.                                                                                                  |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Constraints**:                                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  Individual port: for example, 22                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  Consecutive ports: for example, 22-30                                                                                                 |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  Non-consecutive ports: ports and port ranges, such as **22,23-30**. You can specify up to 20 port ranges. Port ranges cannot overlap. |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  All ports: Leave it empty or enter 1-65535.                                                                                           |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Range**:                                                                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Default Value**:                                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | source_address_group_id      | No              | String          | **Definition**:                                                                                                                          |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | ID of the source IP address group of a network ACL rule.                                                                                 |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Constraints**:                                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  **source_ip_address** and **source_address_group_id** cannot be specified at the same time.                                           |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  **source_address_group_id** and **destination_address_group_id** cannot be specified at the same time.                                |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Range**:                                                                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Default Value**:                                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | destination_address_group_id | No              | String          | **Definition**:                                                                                                                          |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | ID of the destination IP address group of a network ACL rule.                                                                            |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Constraints**:                                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  **destination_ip_address** and **destination_address_group_id** cannot be specified at the same time.                                 |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  **destination_address_group_id** and **source_address_group_id** cannot be specified at the same time.                                |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Range**:                                                                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Default Value**:                                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | enabled                      | No              | Boolean         | **Definition**:                                                                                                                          |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | Whether a network ACL rule is enabled.                                                                                                   |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Constraints**:                                                                                                                         |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | N/A                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Range**:                                                                                                                               |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  true: A network ACL rule is enabled.                                                                                                  |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | -  false: A network ACL rule is disabled.                                                                                                |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | **Default Value**:                                                                                                                       |
   |                              |                 |                 |                                                                                                                                          |
   |                              |                 |                 | true                                                                                                                                     |
   +------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------------------+-----------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter             | Type                                                                        | Description                                   |
   +=======================+=============================================================================+===============================================+
   | firewall              | :ref:`FirewallDetail <updatefirewallrules__response_firewalldetail>` object | **Definition**:                               |
   |                       |                                                                             |                                               |
   |                       |                                                                             | Response body for updating a network ACL rule |
   |                       |                                                                             |                                               |
   |                       |                                                                             | **Range**:                                    |
   |                       |                                                                             |                                               |
   |                       |                                                                             | N/A                                           |
   +-----------------------+-----------------------------------------------------------------------------+-----------------------------------------------+
   | request_id            | String                                                                      | **Definition**:                               |
   |                       |                                                                             |                                               |
   |                       |                                                                             | Request ID.                                   |
   |                       |                                                                             |                                               |
   |                       |                                                                             | **Range**:                                    |
   |                       |                                                                             |                                               |
   |                       |                                                                             | N/A                                           |
   +-----------------------+-----------------------------------------------------------------------------+-----------------------------------------------+

.. _updatefirewallrules__response_firewalldetail:

.. table:: **Table 6** FirewallDetail

   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                            | Description                                                                                                                                              |
   +=======================+=================================================================================================+==========================================================================================================================================================+
   | id                    | String                                                                                          | **Definition**:                                                                                                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | Network ACL ID. Each network ACL comes with an ID, which uniquely identifies the network ACL.                                                            |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | **Range**:                                                                                                                                               |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | The value is in UUID format with hyphens (-).                                                                                                            |
   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                                          | **Definition**:                                                                                                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | Name of the network ACL.                                                                                                                                 |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | **Range**:                                                                                                                                               |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods.                                          |
   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                                          | **Definition**:                                                                                                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | Supplementary information about the network ACL.                                                                                                         |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | **Range**:                                                                                                                                               |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | The value can contain 0 to 255 characters and cannot contain angle brackets (< or >).                                                                    |
   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                                                          | **Definition**:                                                                                                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | ID of the project that the network ACL belongs to.                                                                                                       |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | **Range**:                                                                                                                                               |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | N/A                                                                                                                                                      |
   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                                          | **Definition**:                                                                                                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | Time when the network ACL was created. The value is automatically generated by the system.                                                               |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | **Range**:                                                                                                                                               |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | The value is a UTC time in the format of *yyyy-MM-ddTHH:mm:ssZ*.                                                                                         |
   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                                          | **Definition**:                                                                                                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | Time when the network ACL was last updated. The value is automatically generated by the system.                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | **Range**:                                                                                                                                               |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | The value is a UTC time in the format of *yyyy-MM-ddTHH:mm:ssZ*.                                                                                         |
   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up        | Boolean                                                                                         | **Definition**:                                                                                                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | Network ACL administrative status.                                                                                                                       |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | **Range**                                                                                                                                                |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | -  true: The network ACL is enabled.                                                                                                                     |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | -  false: The network ACL is disabled.                                                                                                                   |
   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                                                          | **Definition**:                                                                                                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | Network ACL status.                                                                                                                                      |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | **Range**                                                                                                                                                |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | -  ACTIVE: The network ACL is associated with a subnet.                                                                                                  |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | -  INACTIVE: The network ACL is not associated with a subnet.                                                                                            |
   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | String                                                                                          | **Definition**:                                                                                                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | ID of the enterprise project that the network ACL belongs to.                                                                                            |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | **Range**:                                                                                                                                               |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). **0** indicates the default enterprise project. |
   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Array of :ref:`ResponseTag <updatefirewallrules__response_responsetag>` objects                 | **Definition**:                                                                                                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | Tags of a network ACL, including tag keys and tag values, which can be used to classify and identify resources. For details, see the tag objects.        |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | **Range**:                                                                                                                                               |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | N/A                                                                                                                                                      |
   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | associations          | Array of :ref:`FirewallAssociation <updatefirewallrules__response_firewallassociation>` objects | **Definition**:                                                                                                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | Subnets associated with the network ACL.                                                                                                                 |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | **Range**:                                                                                                                                               |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | N/A                                                                                                                                                      |
   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ingress_rules         | Array of :ref:`FirewallRuleDetail <updatefirewallrules__response_firewallruledetail>` objects   | **Definition**:                                                                                                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | Network ACL inbound rules.                                                                                                                               |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | **Range**:                                                                                                                                               |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | N/A                                                                                                                                                      |
   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | egress_rules          | Array of :ref:`FirewallRuleDetail <updatefirewallrules__response_firewallruledetail>` objects   | **Definition**:                                                                                                                                          |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | Network ACL outbound rules.                                                                                                                              |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | **Range**:                                                                                                                                               |
   |                       |                                                                                                 |                                                                                                                                                          |
   |                       |                                                                                                 | N/A                                                                                                                                                      |
   +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _updatefirewallrules__response_responsetag:

.. table:: **Table 7** ResponseTag

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                        |
   +=======================+=======================+====================================================================================================================================+
   | key                   | String                | **Definition**:                                                                                                                    |
   |                       |                       |                                                                                                                                    |
   |                       |                       | Tag key.                                                                                                                           |
   |                       |                       |                                                                                                                                    |
   |                       |                       | **Range**:                                                                                                                         |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  A tag key can contain a maximum of 128 Unicode characters and cannot be left blank.                                             |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  Each tag key of a resource must be unique.                                                                                      |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  The value can contain:                                                                                                          |
   |                       |                       |                                                                                                                                    |
   |                       |                       |    -  Letters                                                                                                                      |
   |                       |                       |                                                                                                                                    |
   |                       |                       |    -  Digits                                                                                                                       |
   |                       |                       |                                                                                                                                    |
   |                       |                       |    -  Special characters: underscores (_), periods (.), colons (:), plus signs (+), hyphens (-), at signs (@), and equal signs (=) |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | value                 | String                | **Definition**:                                                                                                                    |
   |                       |                       |                                                                                                                                    |
   |                       |                       | Tag value.                                                                                                                         |
   |                       |                       |                                                                                                                                    |
   |                       |                       | **Range**:                                                                                                                         |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  Each value can contain a maximum of 255 Unicode characters and can be left blank.                                               |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  The value can contain:                                                                                                          |
   |                       |                       |                                                                                                                                    |
   |                       |                       |    -  Letters                                                                                                                      |
   |                       |                       |                                                                                                                                    |
   |                       |                       |    -  Digits                                                                                                                       |
   |                       |                       |                                                                                                                                    |
   |                       |                       |    -  Special characters: underscores (_), colons (:), plus signs (+), hyphens (-), at signs (@), and equal signs (=)              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+

.. _updatefirewallrules__response_firewallassociation:

.. table:: **Table 8** FirewallAssociation

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                              |
   +=======================+=======================+==========================================================================================+
   | virsubnet_id          | String                | **Definition**:                                                                          |
   |                       |                       |                                                                                          |
   |                       |                       | ID of the subnet associated with the network ACL.                                        |
   |                       |                       |                                                                                          |
   |                       |                       | **Range**:                                                                               |
   |                       |                       |                                                                                          |
   |                       |                       | -  If the network ACL type is normal, it can only be associated with common subnets.     |
   |                       |                       |                                                                                          |
   |                       |                       | -  If the network ACL type is CloudDCN, it can only be associated with CloudDCN subnets. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+

.. _updatefirewallrules__response_firewallruledetail:

.. table:: **Table 9** FirewallRuleDetail

   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                    | Type                  | Description                                                                                                                              |
   +==============================+=======================+==========================================================================================================================================+
   | id                           | String                | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | Network ACL rule ID. Each network ACL rule comes with an ID, which uniquely identifies the network ACL rule.                             |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | The value is in UUID format with hyphens (-).                                                                                            |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | name                         | String                | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | Network ACL rule name.                                                                                                                   |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | The value can contain 0 to 255 characters, including letters, digits, underscores (_), hyphens (-), and periods.                         |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | description                  | String                | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | Supplementary information about the network ACL rule.                                                                                    |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | The value can contain 0 to 255 characters and cannot contain angle brackets (< or >).                                                    |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | action                       | String                | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | Whether a network ACL rule allows or denies traffic.                                                                                     |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  allow: A network ACL rule allows traffic.                                                                                             |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  deny: A network ACL rule denies traffic.                                                                                              |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id                   | String                | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | ID of the project that the network ACL rule belongs to.                                                                                  |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | N/A                                                                                                                                      |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol                     | String                | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | Communication protocol of a network ACL rule.                                                                                            |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  tcp                                                                                                                                   |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  udp                                                                                                                                   |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  icmp                                                                                                                                  |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  icmpv6                                                                                                                                |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  IP protocol number (0-255)                                                                                                            |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  any: any protocol                                                                                                                     |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_version                   | Integer               | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | IP address version of a network ACL rule.                                                                                                |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  4: IPv4 network ACL rule.                                                                                                             |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  6: IPv6 network ACL rule.                                                                                                             |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | source_ip_address            | String                | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | Source IP address or source IP address range of a network ACL rule.                                                                      |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **source_ip_address** and **source_address_group_id** cannot be specified at the same time.                                              |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | destination_ip_address       | String                | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | Destination IP address or destination IP address range of a network ACL rule.                                                            |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **destination_ip_address** and **destination_address_group_id** cannot be specified at the same time.                                    |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | source_port                  | String                | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | Source port of a network ACL rule.                                                                                                       |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  Individual port: for example, 22                                                                                                      |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  Consecutive ports: for example, 22-30                                                                                                 |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  Non-consecutive ports: ports and port ranges, such as **22,23-30**. You can specify up to 20 port ranges. Port ranges cannot overlap. |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  All ports: Leave it empty or enter 1-65535.                                                                                           |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | destination_port             | String                | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | Destination port of a network ACL rule.                                                                                                  |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  Individual port: for example, 22                                                                                                      |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  Consecutive ports: for example, 22-30                                                                                                 |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  Non-consecutive ports: ports and port ranges, such as **22,23-30**. You can specify up to 20 port ranges. Port ranges cannot overlap. |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  All ports: Leave it empty or enter 1-65535.                                                                                           |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | source_address_group_id      | String                | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | ID of the source IP address group of a network ACL rule.                                                                                 |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **source_ip_address** and **source_address_group_id** cannot be specified at the same time.                                              |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | destination_address_group_id | String                | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | ID of the destination IP address group of a network ACL rule.                                                                            |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **destination_ip_address** and **destination_address_group_id** cannot be specified at the same time.                                    |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | enabled                      | Boolean               | **Definition**:                                                                                                                          |
   |                              |                       |                                                                                                                                          |
   |                              |                       | Whether a network ACL rule is enabled.                                                                                                   |
   |                              |                       |                                                                                                                                          |
   |                              |                       | **Range**:                                                                                                                               |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  true: (default value) A network ACL rule is enabled.                                                                                  |
   |                              |                       |                                                                                                                                          |
   |                              |                       | -  false: A network ACL rule is disabled.                                                                                                |
   +------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Update the inbound rule whose ID is 774cf578-e70d-ec11-a40c-b864b1cf74ea in the network ACL whose ID is e9a7731d-5bd9-4250-a524-b9a076fd5629.

.. code-block:: text

   PUT https://{Endpoint}/v3/{project_id}/vpc/firewalls/e9a7731d-5bd9-4250-a524-b9a076fd5629/update-rules

   {
     "firewall" : {
       "ingress_rules" : [ {
         "id" : "774cf578-e70d-ec11-a40c-b864b1cf74ea",
         "name" : "network_acl_rule test2",
         "description" : "network_acl_rule test2",
         "action" : "allow",
         "protocol" : "tcp",
         "ip_version" : "4",
         "source_ip_address" : "192.168.3.0/24",
         "destination_ip_address" : "192.168.6.0/24",
         "source_port" : "30-40,60-90",
         "destination_port" : "40-60,70-90",
         "source_address_group_id" : null,
         "destination_address_group_id" : null
       } ]
     }
   }

Example Responses
-----------------

**Status code: 200**

Normal response to the PUT operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

.. code-block::

   {
     "firewall" : {
       "id" : "e9a7731d-5bd9-4250-a524-b9a076fd5629",
       "name" : "network_acl_test1",
       "description" : "network_acl_test1",
       "project_id" : "9476ea5a8a9849c38358e43c0c3a9e12",
       "created_at" : "2022-04-07T07:30:46.000+00:00",
       "updated_at" : "2022-04-07T07:30:46.000+00:00",
       "admin_state_up" : true,
       "enterprise_project_id" : "158ad39a-dab7-45a3-9b5a-2836b3cf93f9",
       "status" : "ACTIVE",
       "tags" : [ ],
       "ingress_rules" : [ {
         "id" : "774cf578-e70d-ec11-a40c-b864b1cf74ea",
         "name" : "network_acl_rule test2",
         "description" : "network_acl_rule test2",
         "action" : "allow",
         "project_id" : "9476ea5a8a9849c38358e43c0c3a9e12",
         "protocol" : "tcp",
         "ip_version" : 4,
         "source_ip_address" : "192.168.3.0/24",
         "destination_ip_address" : "192.168.6.0/24",
         "source_port" : "30-40,60-90",
         "destination_port" : "40-60,70-90"
       } ],
       "egress_rules" : [ {
         "id" : "f9a7731d-5bd9-4250-a524-b9a076fd5629",
         "name" : "network_acl_rule test",
         "description" : "network_acl_rule test",
         "action" : "allow",
         "project_id" : "9476ea5a8a9849c38358e43c0c3a9e12",
         "protocol" : "tcp",
         "ip_version" : 4,
         "source_ip_address" : "192.168.3.0/24",
         "destination_ip_address" : "192.168.6.0/24",
         "source_port" : "30-40,60-90",
         "destination_port" : "40-60,70-90"
       } ],
       "associations" : [ {
         "virsubnet_id" : "8359e5b0-353f-4ef3-a071-98e67a34a143"
       } ]
     }
   }

Status Codes
------------

+-------------+------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                          |
+=============+======================================================================================================+
| 200         | Normal response to the PUT operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`. |
+-------------+------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
