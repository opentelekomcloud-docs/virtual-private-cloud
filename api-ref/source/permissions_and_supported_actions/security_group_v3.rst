:original_name: vpc_permission_0044.html

.. _vpc_permission_0044:

Security Group (V3)
===================

+---------------------------+-----------------------------------------------------------------+---------------------------+
| Permission                | API                                                             | Action                    |
+===========================+=================================================================+===========================+
| Creating a security group | POST /v3/{project_id}/vpc/security-groups                       | vpc:securityGroups:create |
+---------------------------+-----------------------------------------------------------------+---------------------------+
| Querying a security group | GET /v3/{project_id}/vpc/security-groups/{security_group_id}    | vpc:securityGroups:get    |
+---------------------------+-----------------------------------------------------------------+---------------------------+
| Querying security groups  | GET /v3/{project_id}/vpc/security-groups                        | vpc:securityGroups:get    |
+---------------------------+-----------------------------------------------------------------+---------------------------+
| Updating a security group | PUT /v3/{project_id}/vpc/security-groups/{security_group_id}    | vpc:securityGroups:update |
+---------------------------+-----------------------------------------------------------------+---------------------------+
| Deleting a security group | DELETE /v3/{project_id}/vpc/security-groups/{security_group_id} | vpc:securityGroups:delete |
+---------------------------+-----------------------------------------------------------------+---------------------------+
