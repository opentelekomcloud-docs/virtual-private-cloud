:original_name: vpc_firewall_0002.html

.. _vpc_firewall_0002:

Querying a Firewall Rule
========================

Function
--------

This API is used to query details about a specific firewall rule.

URI
---

GET /v2.0/fwaas/firewall_rules/{firewall_rule_id}

:ref:`Table 1 <vpc_firewall_0002__table18880184689>` describes the parameters.

.. _vpc_firewall_0002__table18880184689:

.. table:: **Table 1** Parameter description

   +------------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | Name             | Mandatory | Type   | Description                                                                                                                        |
   +==================+===========+========+====================================================================================================================================+
   | firewall_rule_id | Yes       | String | Specifies the firewall rule ID, which uniquely identifies the firewall rule. The **firewall_rule_id** value is used as the filter. |
   +------------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

None

Response Message
----------------

.. table:: **Table 2** Response parameter

   +---------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type                                                                 | Description                                                                                                    |
   +===============+======================================================================+================================================================================================================+
   | firewall_rule | :ref:`firewall_rule <vpc_firewall_0002__table38646929121127>` object | Specifies the firewall rule objects. For details, see :ref:`Table 3 <vpc_firewall_0002__table38646929121127>`. |
   +---------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0002__table38646929121127:

.. table:: **Table 3** **Firewall Rule** objects

   +------------------------+---------+-------------------------------------------------------------------------+
   | Attribute              | Type    | Description                                                             |
   +========================+=========+=========================================================================+
   | id                     | String  | Specifies the UUID of the firewall rule.                                |
   +------------------------+---------+-------------------------------------------------------------------------+
   | name                   | String  | Specifies the firewall rule name.                                       |
   +------------------------+---------+-------------------------------------------------------------------------+
   | description            | String  | Provides supplementary information about the firewall rule.             |
   +------------------------+---------+-------------------------------------------------------------------------+
   | tenant_id              | String  | Specifies the project ID.                                               |
   +------------------------+---------+-------------------------------------------------------------------------+
   | public                 | Boolean | Specifies whether the firewall rule can be shared by different tenants. |
   +------------------------+---------+-------------------------------------------------------------------------+
   | protocol               | String  | Specifies the IP protocol.                                              |
   +------------------------+---------+-------------------------------------------------------------------------+
   | source_port            | String  | Specifies the source port number or port number range.                  |
   +------------------------+---------+-------------------------------------------------------------------------+
   | destination_port       | String  | Specifies the destination port number or port number range.             |
   +------------------------+---------+-------------------------------------------------------------------------+
   | ip_version             | Integer | Specifies the IP protocol version.                                      |
   +------------------------+---------+-------------------------------------------------------------------------+
   | source_ip_address      | String  | Specifies the source IP address or CIDR block.                          |
   +------------------------+---------+-------------------------------------------------------------------------+
   | destination_ip_address | String  | Specifies the destination IP address or CIDR block.                     |
   +------------------------+---------+-------------------------------------------------------------------------+
   | action                 | String  | Specifies action performed on traffic passing through the firewall.     |
   +------------------------+---------+-------------------------------------------------------------------------+
   | enabled                | Boolean | Specifies whether the firewall rule is enabled.                         |
   +------------------------+---------+-------------------------------------------------------------------------+
   | project_id             | String  | Specifies the project ID.                                               |
   +------------------------+---------+-------------------------------------------------------------------------+

Example:
--------

Example request

.. code-block:: text

   GET https://{Endpoint}/v2.0/fwaas/firewall_rules/514e6776-162a-4b5d-ab8b-aa36b86655ef

Example response

.. code-block::

   {
       "firewall_rule": {
           "protocol": "tcp",
           "name": "bobby_rule",
           "mode": "normal",
           "tenant_id": "4490a89232ce46d4ae4bfb227ef1a40a",
           "rule_profile": "",
           "enabled": true,
           "source_port": null,
           "source_ip_address": null,
           "destination_ip_address": null,
           "firewall_policy_id": null,
           "action": "allow",
           "position": null,
           "ip_version": 4,
           "shared": false,
           "destination_port": null,
           "id": "514e6776-162a-4b5d-ab8b-aa36b86655ef",
           "description": "",
           "project_id": "4490a89232ce46d4ae4bfb227ef1a40a"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
