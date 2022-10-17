:original_name: vpc_permission_0012.html

.. _vpc_permission_0012:

Subnet (OpenStack Neutron API)
==============================

================= ================================ ==================
Permission        API                              Action
================= ================================ ==================
Queries subnets.  GET /v2.0/subnets                vpc:subnets:get
Queries a subnet. GET /v2.0/subnets/{subnet_id}    vpc:subnets:get
Creates a subnet. POST /v2.0/subnets               vpc:subnets:create
Updates a subnet. PUT /v2.0/subnets/{subnet_id}    vpc:subnets:update
Deletes a subnet. DELETE /v2.0/subnets/{subnet_id} vpc:subnets:delete
================= ================================ ==================
