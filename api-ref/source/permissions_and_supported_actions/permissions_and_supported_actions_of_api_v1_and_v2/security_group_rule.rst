:original_name: vpc_permission_0009.html

.. _vpc_permission_0009:

Security Group Rule
===================

+--------------------------------+-------------------------------------------------------------------------+-------------------------------+
| Permission                     | API                                                                     | Action                        |
+================================+=========================================================================+===============================+
| Adding a security group rule   | POST /v1/{project_id}/security-group-rules                              | vpc:securityGroupRules:create |
+--------------------------------+-------------------------------------------------------------------------+-------------------------------+
| Querying a security group rule | GET /v1/{project_id}/security-group-rules/{rules_security_groups_id}    | vpc:securityGroupRules:get    |
+--------------------------------+-------------------------------------------------------------------------+-------------------------------+
| Querying security group rules  | GET /v1/{project_id}/security-group-rules                               | vpc:securityGroupRules:get    |
+--------------------------------+-------------------------------------------------------------------------+-------------------------------+
| Deleting a security group rule | DELETE /v1/{project_id}/security-group-rules/{rules_security_groups_id} | vpc:securityGroupRules:delete |
+--------------------------------+-------------------------------------------------------------------------+-------------------------------+
| Updating a security group rule | ``-``                                                                   | vpc:securityGroupRules:update |
+--------------------------------+-------------------------------------------------------------------------+-------------------------------+
