:original_name: vpc_permission_0022.html

.. _vpc_permission_0022:

VPC
===

============== ===================================== ===============
Permission     API                                   Action
============== ===================================== ===============
Creates a VPC. POST /v1/{project_id}/vpcs            vpc:vpcs:create
Queries a VPC. GET /v1/{project_id}/vpcs/{vpc_id}    vpc:vpcs:get
Queries VPCs.  GET /v1/{project_id}/vpcs             vpc:vpcs:list
Updates a VPC. PUT /v1/{project_id}/vpcs/{vpc_id}    vpc:vpcs:update
Deletes a VPC. DELETE /v1/{project_id}/vpcs/{vpc_id} vpc:vpcs:delete
============== ===================================== ===============
