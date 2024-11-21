:original_name: vpc_permission_0032.html

.. _vpc_permission_0032:

Security Group Rule (V3)
========================

+--------------------------------+-----------------------------------------------------------------------------+-------------------------------+
| Permission                     | API                                                                         | Action                        |
+================================+=============================================================================+===============================+
| Adding a security group rule   | POST /v3/{project_id}/vpc/security-group-rules                              | vpc:securityGroupRules:create |
+--------------------------------+-----------------------------------------------------------------------------+-------------------------------+
| Querying a security group rule | GET /v3/{project_id}/vpc/security-group-rules/{rules_security_groups_id}    | vpc:securityGroupRules:get    |
+--------------------------------+-----------------------------------------------------------------------------+-------------------------------+
| Querying security group rules  | GET /v3/{project_id}/vpc/security-group-rules                               | vpc:securityGroupRules:get    |
+--------------------------------+-----------------------------------------------------------------------------+-------------------------------+
| Deleting a security group rule | DELETE /v3/{project_id}/vpc/security-group-rules/{rules_security_groups_id} | vpc:securityGroupRules:delete |
+--------------------------------+-----------------------------------------------------------------------------+-------------------------------+
| Updating a security group rule | ``-``                                                                       | vpc:securityGroupRules:update |
+--------------------------------+-----------------------------------------------------------------------------+-------------------------------+
