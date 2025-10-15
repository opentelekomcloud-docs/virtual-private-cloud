:original_name: vpc_permission_0016.html

.. _vpc_permission_0016:

Security Group (OpenStack Neutron API)
======================================

+-----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Permission                                    | API                                                          | Action                        |
+===============================================+==============================================================+===============================+
| Querying a security group                     | GET /v2.0/security-groups                                    | vpc:securityGroups:get        |
+-----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Querying the details of a security group      | GET /v2.0/security-groups/{security_group_id}                | vpc:securityGroups:get        |
+-----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Creating a security group                     | POST /v2.0/security-groups                                   | vpc:securityGroups:create     |
+-----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Updating a security group                     | PUT /v2.0/security-groups/{security_group_id}                | vpc:securityGroups:update     |
+-----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Deleting a security group                     | DELETE /v2.0/security-groups/{security_group_id}             | vpc:securityGroups:delete     |
+-----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Querying a security group rule                | GET /v2.0/security-group-rules                               | vpc:securityGroupRules:get    |
+-----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Querying the details of a security group rule | GET /v2.0/security-group-rules/{rules_security_groups_id}    | vpc:securityGroupRules:get    |
+-----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Adding a security group rule                  | POST /v2.0/security-group-rules                              | vpc:securityGroupRules:create |
+-----------------------------------------------+--------------------------------------------------------------+-------------------------------+
| Deleting a security group rule                | DELETE /v2.0/security-group-rules/{rules_security_groups_id} | vpc:securityGroupRules:delete |
+-----------------------------------------------+--------------------------------------------------------------+-------------------------------+
