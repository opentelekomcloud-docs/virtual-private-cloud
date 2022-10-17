:original_name: vpc_permission_0018.html

.. _vpc_permission_0018:

Bandwidth (V2.0)
================

+-----------------------------------------+----------------------------------------------------------+-----------------------+
| Permission                              | API                                                      | Action                |
+=========================================+==========================================================+=======================+
| Allocates a shared bandwidth.           | POST /v2.0/{project_id}/bandwidths                       | vpc:bandwidths:create |
+-----------------------------------------+----------------------------------------------------------+-----------------------+
| Deletes a shared bandwidth.             | DELETE /v2.0/{project_id}/bandwidths/{bandwidth_id}      | vpc:bandwidths:delete |
+-----------------------------------------+----------------------------------------------------------+-----------------------+
| Adds an EIP to a shared bandwidth.      | POST /v2.0/{project_id}/bandwidths/{bandwidth_id}/insert | vpc:publicIps:insert  |
+-----------------------------------------+----------------------------------------------------------+-----------------------+
| Removes an EIP from a shared bandwidth. | POST /v2.0/{project_id}/bandwidths/{bandwidth_id}/remove | vpc:publicIps:remove  |
+-----------------------------------------+----------------------------------------------------------+-----------------------+
