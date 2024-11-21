:original_name: vpc_permission_0010.html

.. _vpc_permission_0010:

Port (OpenStack Neutron API)
============================

=============== ============================ ================
Permission      API                          Action
=============== ============================ ================
Querying ports  GET /v2.0/ports              vpc:ports:get
Querying a port GET /v2.0/ports/{port_id}    vpc:ports:get
Creating a port POST /v2.0/ports             vpc:ports:create
Updating a port PUT /v2.0/ports/{port_id}    vpc:ports:update
Deleting a port DELETE /v2.0/ports/{port_id} vpc:ports:delete
=============== ============================ ================
