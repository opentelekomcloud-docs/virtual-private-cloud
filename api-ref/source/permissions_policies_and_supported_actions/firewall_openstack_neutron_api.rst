:original_name: vpc_permission_0015.html

.. _vpc_permission_0015:

Firewall (OpenStack Neutron API)
================================

+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Permission                     | API                                                                | Action                             |
+================================+====================================================================+====================================+
| Queries all firewall rules.    | GET /v2.0/fwaas/firewall_rules                                     | vpc:firewallRules:get              |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Queries a firewall rule.       | GET /v2.0/fwaas/firewall_rules/{firewall_rule_id}                  | vpc:firewallRules:get              |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Creates a firewall rule.       | POST /v2.0/fwaas/firewall_rules                                    | vpc:firewallRules:create           |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Updates a firewall rule.       | PUT /v2.0/fwaas/firewall_rules/{firewall_rule_id}                  | vpc:firewallRules:update           |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Deletes a firewall rule.       | DELETE /v2.0/fwaas/firewall_rules/{firewall_rule_id}               | vpc:firewallRules:delete           |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Queries all firewall policies. | GET /v2.0/fwaas/firewall_policies                                  | vpc:firewallPolicies:get           |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Queries a firewall policy.     | GET /v2.0/fwaas/firewall_policies/{firewall_policy_id}             | vpc:firewallPolicies:get           |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Creates a firewall policy.     | POST /v2.0/fwaas/firewall_policies                                 | vpc:firewallPolicies:create        |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Updates a firewall policy.     | PUT /v2.0/fwaas/firewall_policies/{firewall_policy_id}             | vpc:firewallPolicies:update        |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Deletes a firewall policy.     | DELETE /v2.0/fwaas/firewall_policies/{firewall_policy_id}          | vpc:firewallPolicies:delete        |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Inserts a firewall rule.       | PUT /v2.0/fwaas/firewall_policies/{firewall_policy_id}/insert_rule | -  vpc:firewallPolicies:addRule    |
|                                |                                                                    | -  vpc:firewallPolicies:get        |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Removes a firewall rule.       | PUT /v2.0/fwaas/firewall_policies/{firewall_policy_id}/remove_rule | -  vpc:firewallPolicies:removeRule |
|                                |                                                                    | -  vpc:firewallPolicies:get        |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Queries all firewall groups.   | GET /v2.0/fwaas/firewall_groups                                    | vpc:firewallGroups:get             |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Queries a firewall group.      | GET /v2.0/fwaas/firewall_groups/{firewall_group_id}                | vpc:firewallGroups:get             |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Creates a firewall group.      | POST /v2.0/fwaas/firewall_groups                                   | vpc:firewallGroups:create          |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Updates a firewall group.      | PUT /v2.0/fwaas/firewall_groups/{firewall_group_id}                | vpc:firewallGroups:update          |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
| Deletes a firewall group       | DELETE /v2.0/fwaas/firewall_groups/{firewall_group_id}             | vpc:firewallGroups:delete          |
+--------------------------------+--------------------------------------------------------------------+------------------------------------+
