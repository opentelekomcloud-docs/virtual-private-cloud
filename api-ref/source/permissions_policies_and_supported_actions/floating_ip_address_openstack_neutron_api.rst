:original_name: vpc_permission_0014.html

.. _vpc_permission_0014:

Floating IP Address (OpenStack Neutron API)
===========================================

+--------------------------------+------------------------------------------+------------------------+
| Permission                     | API                                      | Action                 |
+================================+==========================================+========================+
| Queries floating IP addresses. | GET /v2.0/floatingips                    | vpc:floatingIps:get    |
+--------------------------------+------------------------------------------+------------------------+
| Queries a floating IP address. | GET /v2.0/floatingips/{floatingip_id}    | vpc:floatingIps:get    |
+--------------------------------+------------------------------------------+------------------------+
| Creates a floating IP address. | POST /v2.0/floatingips                   | vpc:floatingIps:create |
+--------------------------------+------------------------------------------+------------------------+
| Updates a floating IP address. | PUT /v2.0/floatingips/{floatingip_id}    | vpc:floatingIps:update |
+--------------------------------+------------------------------------------+------------------------+
| Deletes a floating IP address. | DELETE /v2.0/floatingips/{floatingip_id} | vpc:floatingIps:delete |
+--------------------------------+------------------------------------------+------------------------+
