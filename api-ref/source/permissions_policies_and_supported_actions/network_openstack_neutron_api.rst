:original_name: vpc_permission_0011.html

.. _vpc_permission_0011:

Network (OpenStack Neutron API)
===============================

+--------------------+------------------------------------+---------------------+
| Permission         | API                                | Action              |
+====================+====================================+=====================+
| Queries networks.  | GET /v2.0/networks                 | vpc:networks:get    |
+--------------------+------------------------------------+---------------------+
| Queries a network. | GET /v2.0/networks/{network_id}    | vpc:networks:get    |
+--------------------+------------------------------------+---------------------+
| Creates a network. | POST /v2.0/networks                | vpc:networks:create |
+--------------------+------------------------------------+---------------------+
| Updates a network. | PUT /v2.0/networks/{network_id}    | vpc:networks:update |
+--------------------+------------------------------------+---------------------+
| Deletes a network. | DELETE /v2.0/networks/{network_id} | vpc:networks:delete |
+--------------------+------------------------------------+---------------------+
