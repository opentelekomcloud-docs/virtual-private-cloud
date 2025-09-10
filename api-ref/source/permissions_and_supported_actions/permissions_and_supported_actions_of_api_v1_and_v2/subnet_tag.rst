:original_name: vpc_permission_0019.html

.. _vpc_permission_0019:

Subnet Tag
==========

+---------------------------------------------+-----------------------------------------------------------+-----------------------+
| Permission                                  | API                                                       | Action                |
+=============================================+===========================================================+=======================+
| Adding a tag to a subnet                    | POST /v2.0/{project_id}/subnets/{subnet_id}/tags          | vpc:subnetTags:create |
+---------------------------------------------+-----------------------------------------------------------+-----------------------+
| Querying tags of a subnet                   | GET /v2.0/{project_id}/subnets/{subnet_id}/tags           | vpc:subnetTags:get    |
+---------------------------------------------+-----------------------------------------------------------+-----------------------+
| Deleting a tag from a subnet                | DELETE /v2.0/{project_id}/subnets/{subnet_id}/tags/{key}  | vpc:subnetTags:delete |
+---------------------------------------------+-----------------------------------------------------------+-----------------------+
| Batch adding or deleting subnet tags        | POST /v2.0/{project_id}/subnets/{subnet_id}/tags/action   | vpc:subnetTags:create |
|                                             |                                                           |                       |
|                                             |                                                           | vpc:subnetTags:delete |
+---------------------------------------------+-----------------------------------------------------------+-----------------------+
| Querying subnets by tag                     | POST /v2.0/{project_id}/subnets/resource_instances/action | vpc:subnetTags:get    |
+---------------------------------------------+-----------------------------------------------------------+-----------------------+
| Querying subnet tags in a specified project | GET /v2.0/{project_id}/subnets/tags                       | vpc:subnetTags:get    |
+---------------------------------------------+-----------------------------------------------------------+-----------------------+
