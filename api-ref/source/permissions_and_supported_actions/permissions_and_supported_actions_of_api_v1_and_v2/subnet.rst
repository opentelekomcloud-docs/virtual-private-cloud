:original_name: vpc_permission_0001.html

.. _vpc_permission_0001:

Subnet
======

+-------------------+-----------------------------------------------------------+--------------------+
| Permission        | API                                                       | Action             |
+===================+===========================================================+====================+
| Creating a subnet | POST /v1/{project_id}/subnets                             | vpc:subnets:create |
+-------------------+-----------------------------------------------------------+--------------------+
| Querying a subnet | GET /v1/{project_id}/subnets/{subnet_id}                  | vpc:subnets:get    |
+-------------------+-----------------------------------------------------------+--------------------+
| Querying subnets  | GET /v1/{project_id}/subnets                              | vpc:subnets:get    |
+-------------------+-----------------------------------------------------------+--------------------+
| Updating a subnet | PUT /v1/{project_id}/vpcs/{vpc_id}/subnets/{subnet_id}    | vpc:subnets:update |
+-------------------+-----------------------------------------------------------+--------------------+
| Deleting a subnet | DELETE /v1/{project_id}/vpcs/{vpc_id}/subnets/{subnet_id} | vpc:subnets:delete |
+-------------------+-----------------------------------------------------------+--------------------+
