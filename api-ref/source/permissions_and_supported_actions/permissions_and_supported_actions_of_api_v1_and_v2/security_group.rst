:original_name: vpc_permission_0008.html

.. _vpc_permission_0008:

Security Group
==============

+---------------------------+-------------------------------------------------------------+---------------------------+
| Permission                | API                                                         | Action                    |
+===========================+=============================================================+===========================+
| Creating a security group | POST /v1/{project_id}/security-groups                       | vpc:securityGroups:create |
+---------------------------+-------------------------------------------------------------+---------------------------+
| Querying a security group | GET /v1/{project_id}/security-groups/{security_group_id}    | vpc:securityGroups:get    |
+---------------------------+-------------------------------------------------------------+---------------------------+
| Querying security groups  | GET /v1/{project_id}/security-groups                        | vpc:securityGroups:get    |
+---------------------------+-------------------------------------------------------------+---------------------------+
| Deleting a security group | DELETE /v1/{project_id}/security-groups/{security_group_id} | vpc:securityGroups:delete |
+---------------------------+-------------------------------------------------------------+---------------------------+
