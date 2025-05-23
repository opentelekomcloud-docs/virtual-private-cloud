:original_name: vpc_permission_0021.html

.. _vpc_permission_0021:

VPC Tag
=======

+-----------------------------------+--------------------------------------------------------+-----------------------+
| Permission                        | API                                                    | Action                |
+===================================+========================================================+=======================+
| Adding a tag to a VPC             | POST /v2.0/{project_id}/vpcs/{vpc_id}/tags             | vpc:vpcTags:create    |
+-----------------------------------+--------------------------------------------------------+-----------------------+
| Querying tags of a VPC            | GET /v2.0/{project_id}/vpcs/{vpc_id}/tags              | vpc:vpcTags:get       |
+-----------------------------------+--------------------------------------------------------+-----------------------+
| Deleting a VPC tag                | DELETE /v2.0/{project_id}/vpcs/{vpc_id}/tags/{key}     | vpc:vpcTags:delete    |
+-----------------------------------+--------------------------------------------------------+-----------------------+
| Batch adding or deleting VPC tags | POST /v2.0/{project_id}/vpcs/{vpc_id}/tags/action      | vpc:vpcTags:create    |
|                                   |                                                        |                       |
|                                   |                                                        | vpc:vpcTags:delete    |
+-----------------------------------+--------------------------------------------------------+-----------------------+
| Querying VPCs by tag              | POST /v2.0/{project_id}/vpcs/resource_instances/action | vpc:vpcTags:get       |
+-----------------------------------+--------------------------------------------------------+-----------------------+
| Querying VPC tags in a project    | GET /v2.0/{project_id}/vpcs/tags                       | vpc:vpcTags:get       |
+-----------------------------------+--------------------------------------------------------+-----------------------+
