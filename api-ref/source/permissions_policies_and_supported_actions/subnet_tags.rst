:original_name: vpc_permission_0019.html

.. _vpc_permission_0019:

Subnet Tags
===========

+---------------------------------------------+-----------------------------------------------------------+-----------------------+
| Permission                                  | API                                                       | Action                |
+=============================================+===========================================================+=======================+
| Creating a Tag for a Subnet                 | POST /v2.0/{project_id}/subnets/{subnet_id}/tags          | vpc:subnetTags:create |
+---------------------------------------------+-----------------------------------------------------------+-----------------------+
| Querying Subnet Tags                        | GET /v2.0/{project_id}/subnets/{subnet_id}/tags           | vpc:subnetTags:get    |
+---------------------------------------------+-----------------------------------------------------------+-----------------------+
| Deleting a Subnet Tag                       | DELETE /v2.0/{project_id}/subnets/{subnet_id}/tags/{key}  | vpc:subnetTags:delete |
+---------------------------------------------+-----------------------------------------------------------+-----------------------+
| Batch Creating or Deleting Subnet Tags      | POST /v2.0/{project_id}/subnets/{subnet_id}/tags/action   | vpc:subnetTags:create |
|                                             |                                                           |                       |
|                                             |                                                           | vpc:subnetTags:delete |
+---------------------------------------------+-----------------------------------------------------------+-----------------------+
| Querying Subnets by Tag                     | POST /v2.0/{project_id}/subnets/resource_instances/action | vpc:subnetTags:get    |
+---------------------------------------------+-----------------------------------------------------------+-----------------------+
| Querying Subnet Tags in a Specified Project | GET /v2.0/{project_id}/subnets/tags                       | vpc:subnetTags:get    |
+---------------------------------------------+-----------------------------------------------------------+-----------------------+
