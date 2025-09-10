:original_name: vpc_permission_0007.html

.. _vpc_permission_0007:

Private IP Address
==================

+--------------------------------+-----------------------------------------------------+-----------------------+
| Permission                     | API                                                 | Action                |
+================================+=====================================================+=======================+
| Assigning a private IP address | POST /v1/{project_id}/privateips                    | vpc:privateIps:create |
+--------------------------------+-----------------------------------------------------+-----------------------+
| Querying a private IP address  | GET /v1/{project_id}/privateips/{privateip_id}      | vpc:privateIps:get    |
+--------------------------------+-----------------------------------------------------+-----------------------+
| Querying private IP addresses  | GET /v1/{project_id}/subnets/{subnet_id}/privateips | vpc:privateIps:list   |
+--------------------------------+-----------------------------------------------------+-----------------------+
| Releasing a private IP address | DELETE /v1/{project_id}/privateips/{privateip_id}   | vpc:privateIps:delete |
+--------------------------------+-----------------------------------------------------+-----------------------+
