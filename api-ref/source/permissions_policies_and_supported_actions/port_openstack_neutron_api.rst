:original_name: vpc_permission_0010.html

.. _vpc_permission_0010:

Port (OpenStack Neutron API)
============================

=============== ============================ ================
Permission      API                          Action
=============== ============================ ================
Queries ports.  GET /v2.0/ports              vpc:ports:get
Queries a port. GET /v2.0/ports/{port_id}    vpc:ports:get
Creates a port. POST /v2.0/ports             vpc:ports:create
Updates a port. PUT /v2.0/ports/{port_id}    vpc:ports:update
Deletes a port. DELETE /v2.0/ports/{port_id} vpc:ports:delete
=============== ============================ ================
