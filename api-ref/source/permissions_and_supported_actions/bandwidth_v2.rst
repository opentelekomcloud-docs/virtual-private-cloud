:original_name: vpc_permission_0018.html

.. _vpc_permission_0018:

Bandwidth (V2)
==============

+-----------------------------------------+----------------------------------------------------------+-----------------------+
| Permission                              | API                                                      | Action                |
+=========================================+==========================================================+=======================+
| Assigning a shared bandwidth            | POST /v2.0/{project_id}/bandwidths                       | vpc:bandwidths:create |
+-----------------------------------------+----------------------------------------------------------+-----------------------+
| Deleting a shared bandwidth             | DELETE /v2.0/{project_id}/bandwidths/{bandwidth_id}      | vpc:bandwidths:delete |
+-----------------------------------------+----------------------------------------------------------+-----------------------+
| Adding an EIP to a shared bandwidth     | POST /v2.0/{project_id}/bandwidths/{bandwidth_id}/insert | vpc:publicIps:insert  |
+-----------------------------------------+----------------------------------------------------------+-----------------------+
| Removing an EIP from a shared bandwidth | POST /v2.0/{project_id}/bandwidths/{bandwidth_id}/remove | vpc:publicIps:remove  |
+-----------------------------------------+----------------------------------------------------------+-----------------------+
