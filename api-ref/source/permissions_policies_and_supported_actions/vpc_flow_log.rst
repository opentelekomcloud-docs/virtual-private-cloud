:original_name: vpc_permission_0025.html

.. _vpc_permission_0025:

VPC Flow Log
============

+-------------------------+---------------------------------------------------+---------------------+
| Permission              | API                                               | Action              |
+=========================+===================================================+=====================+
| Creating a VPC Flow Log | POST /v1/{project_id}/fl/flow_logs                | vpc:flowLogs:create |
+-------------------------+---------------------------------------------------+---------------------+
| Querying VPC Flow Logs  | GET /v1/{project_id}/fl/flow_logs                 | vpc:flowLogs:get    |
+-------------------------+---------------------------------------------------+---------------------+
| Querying a VPC Flow Log | GET /v1/{project_id}/fl/flow_logs/{flowlog_id}    | vpc:flowLogs:get    |
+-------------------------+---------------------------------------------------+---------------------+
| Updating a VPC Flow Log | PUT /v1/{project_id}/fl/flow_logs/{flowlog_id}    | vpc:flowLogs:update |
+-------------------------+---------------------------------------------------+---------------------+
| Deleting a Flow Log     | DELETE /v1/{project_id}/fl/flow_logs/{flowlog_id} | vpc:flowLogs:delete |
+-------------------------+---------------------------------------------------+---------------------+
