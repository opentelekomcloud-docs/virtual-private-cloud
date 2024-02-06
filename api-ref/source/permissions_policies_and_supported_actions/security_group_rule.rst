:original_name: vpc_permission_0009.html

.. _vpc_permission_0009:

Security Group Rule
===================

+--------------------------------+-------------------------------------------------------------------------+-------------------------------+
| Permission                     | API                                                                     | Action                        |
+================================+=========================================================================+===============================+
| Creates a security group rule. | POST /v1/{project_id}/security-group-rules                              | vpc:securityGroupRules:create |
+--------------------------------+-------------------------------------------------------------------------+-------------------------------+
| Queries a security group rule. | GET /v1/{project_id}/security-group-rules/{rules_security_groups_id}    | vpc:securityGroupRules:get    |
+--------------------------------+-------------------------------------------------------------------------+-------------------------------+
| Queries security group rules.  | GET /v1/{project_id}/security-group-rules                               | vpc:securityGroupRules:get    |
+--------------------------------+-------------------------------------------------------------------------+-------------------------------+
| Deletes a security group rule. | DELETE /v1/{project_id}/security-group-rules/{rules_security_groups_id} | vpc:securityGroupRules:delete |
+--------------------------------+-------------------------------------------------------------------------+-------------------------------+
| Updates a security group rule. | ``-``                                                                   | vpc:securityGroupRules:update |
+--------------------------------+-------------------------------------------------------------------------+-------------------------------+
