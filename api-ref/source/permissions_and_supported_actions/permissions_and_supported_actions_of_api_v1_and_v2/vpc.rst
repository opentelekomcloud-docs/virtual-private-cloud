:original_name: vpc_permission_0022.html

.. _vpc_permission_0022:

VPC
===

============== ===================================== ===============
Permission     API                                   Action
============== ===================================== ===============
Creating a VPC POST /v1/{project_id}/vpcs            vpc:vpcs:create
Querying a VPC GET /v1/{project_id}/vpcs/{vpc_id}    vpc:vpcs:get
Querying VPCs  GET /v1/{project_id}/vpcs             vpc:vpcs:list
Updating a VPC PUT /v1/{project_id}/vpcs/{vpc_id}    vpc:vpcs:update
Deleting a VPC DELETE /v1/{project_id}/vpcs/{vpc_id} vpc:vpcs:delete
============== ===================================== ===============
