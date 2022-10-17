:original_name: vpc_permission_0016.html

.. _vpc_permission_0016:

Security Group (OpenStack Neutron API)
======================================

+----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Permission                                   | API                                                          | Action                        |
+==============================================+==============================================================+===============================+
| Queries a security group.                    | GET /v2.0/security-groups                                    | vpc:securityGroups:get        |
+----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Queries details about a security group.      | GET /v2.0/security-groups/{security_group_id}                | vpc:securityGroups:get        |
+----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Creates a security group.                    | POST /v2.0/security-groups                                   | vpc:securityGroups:create     |
+----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Updates a security group.                    | PUT /v2.0/security-groups/{security_group_id}                | vpc:securityGroups:update     |
+----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Deletes a security group.                    | DELETE /v2.0/security-groups/{security_group_id}             | vpc:securityGroups:delete     |
+----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Queries a security group rule.               | GET /v2.0/security-group-rules                               | vpc:securityGroupRules:get    |
+----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Queries details about a security group rule. | GET /v2.0/security-group-rules/{rules_security_groups_id}    | vpc:securityGroupRules:get    |
+----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Creates a security group rule.               | POST /v2.0/security-group-rules                              | vpc:securityGroupRules:create |
+----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Deletes a security group rule.               | DELETE /v2.0/security-group-rules/{rules_security_groups_id} | vpc:securityGroupRules:delete |
+----------------------------------------------+--------------------------------------------------------------+-------------------------------+
