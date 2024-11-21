:original_name: vpc_permission_0012.html

.. _vpc_permission_0012:

Subnet (OpenStack Neutron API)
==============================

================= ================================ ==================
Permission        API                              Action
================= ================================ ==================
Querying subnets  GET /v2.0/subnets                vpc:subnets:get
Querying a subnet GET /v2.0/subnets/{subnet_id}    vpc:subnets:get
Creating a subnet POST /v2.0/subnets               vpc:subnets:create
Updating a subnet PUT /v2.0/subnets/{subnet_id}    vpc:subnets:update
Deleting a subnet DELETE /v2.0/subnets/{subnet_id} vpc:subnets:delete
================= ================================ ==================
