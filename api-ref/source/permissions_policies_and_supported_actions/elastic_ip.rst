:original_name: vpc_permission_0002.html

.. _vpc_permission_0002:

Elastic IP
==========

+-----------------+-------------------------------------------------+----------------------+
| Permission      | API                                             | Action               |
+=================+=================================================+======================+
| Assigns an EIP. | POST /v1/{project_id}/publicips                 | vpc:publicIps:create |
+-----------------+-------------------------------------------------+----------------------+
| Queries an EIP. | GET /v1/{project_id}/publicips/{publicip_id}    | vpc:publicIps:get    |
+-----------------+-------------------------------------------------+----------------------+
| Queries EIPs.   | GET /v1/{project_id}/publicips                  | vpc:publicIps:list   |
+-----------------+-------------------------------------------------+----------------------+
| Updates an EIP. | PUT /v1/{project_id}/publicips/{publicip_id}    | vpc:publicIps:update |
+-----------------+-------------------------------------------------+----------------------+
| Release an EIP. | DELETE /v1/{project_id}/publicips/{publicip_id} | vpc:publicIps:delete |
+-----------------+-------------------------------------------------+----------------------+
