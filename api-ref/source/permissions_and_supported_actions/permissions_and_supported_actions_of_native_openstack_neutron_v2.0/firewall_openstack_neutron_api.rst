:original_name: vpc_permission_0015.html

.. _vpc_permission_0015:

Firewall (OpenStack Neutron API)
================================

+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Permission                     | API                                                                | Action                             |
+================================+====================================================================+====================================+
| Querying all firewall rules    | GET /v2.0/fwaas/firewall_rules                                     | vpc:firewallRules:get              |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Querying a firewall rule       | GET /v2.0/fwaas/firewall_rules/{firewall_rule_id}                  | vpc:firewallRules:get              |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Creating a firewall rule       | POST /v2.0/fwaas/firewall_rules                                    | vpc:firewallRules:create           |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Updating a firewall rule       | PUT /v2.0/fwaas/firewall_rules/{firewall_rule_id}                  | vpc:firewallRules:update           |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Deleting a firewall rule       | DELETE /v2.0/fwaas/firewall_rules/{firewall_rule_id}               | vpc:firewallRules:delete           |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Querying all firewall policies | GET /v2.0/fwaas/firewall_policies                                  | vpc:firewallPolicies:get           |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Querying a firewall policy     | GET /v2.0/fwaas/firewall_policies/{firewall_policy_id}             | vpc:firewallPolicies:get           |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Creating a firewall policy     | POST /v2.0/fwaas/firewall_policies                                 | vpc:firewallPolicies:create        |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Updating a firewall policy     | PUT /v2.0/fwaas/firewall_policies/{firewall_policy_id}             | vpc:firewallPolicies:update        |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Deleting a firewall policy     | DELETE /v2.0/fwaas/firewall_policies/{firewall_policy_id}          | vpc:firewallPolicies:delete        |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Inserting a firewall rule      | PUT /v2.0/fwaas/firewall_policies/{firewall_policy_id}/insert_rule | -  vpc:firewallPolicies:addRule    |
|                                |                                                                    | -  vpc:firewallPolicies:get        |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Removing a firewall rule       | PUT /v2.0/fwaas/firewall_policies/{firewall_policy_id}/remove_rule | -  vpc:firewallPolicies:removeRule |
|                                |                                                                    | -  vpc:firewallPolicies:get        |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Querying all firewall groups   | GET /v2.0/fwaas/firewall_groups                                    | vpc:firewallGroups:get             |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Querying a firewall group      | GET /v2.0/fwaas/firewall_groups/{firewall_group_id}                | vpc:firewallGroups:get             |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Creating a firewall group      | POST /v2.0/fwaas/firewall_groups                                   | vpc:firewallGroups:create          |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Updating a firewall group      | PUT /v2.0/fwaas/firewall_groups/{firewall_group_id}                | vpc:firewallGroups:update          |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Deleting a firewall group      | DELETE /v2.0/fwaas/firewall_groups/{firewall_group_id}             | vpc:firewallGroups:delete          |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
