:original_name: vpc_permission_0011.html

.. _vpc_permission_0011:

Network (OpenStack Neutron API)
===============================

+--------------------+------------------------------------+---------------------+
| Permission         | API                                | Action              |
+====================+====================================+=====================+
| Querying networks  | GET /v2.0/networks                 | vpc:networks:get    |
+--------------------+------------------------------------+---------------------+
| Querying a network | GET /v2.0/networks/{network_id}    | vpc:networks:get    |
+--------------------+------------------------------------+---------------------+
| Creating a network | POST /v2.0/networks                | vpc:networks:create |
+--------------------+------------------------------------+---------------------+
| Updating a network | PUT /v2.0/networks/{network_id}    | vpc:networks:update |
+--------------------+------------------------------------+---------------------+
| Deleting a network | DELETE /v2.0/networks/{network_id} | vpc:networks:delete |
+--------------------+------------------------------------+---------------------+
