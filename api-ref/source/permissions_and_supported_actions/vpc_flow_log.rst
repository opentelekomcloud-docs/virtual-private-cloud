:original_name: vpc_permission_0025.html

.. _vpc_permission_0025:

VPC Flow Log
============

+---------------------+---------------------------------------------------+---------------------+
| Permission          | API                                               | Action              |
+=====================+===================================================+=====================+
| Creating a flow log | POST /v1/{project_id}/fl/flow_logs                | vpc:flowLogs:create |
+---------------------+---------------------------------------------------+---------------------+
| Querying flow logs  | GET /v1/{project_id}/fl/flow_logs                 | vpc:flowLogs:get    |
+---------------------+---------------------------------------------------+---------------------+
| Querying a flow log | GET /v1/{project_id}/fl/flow_logs/{flowlog_id}    | vpc:flowLogs:get    |
+---------------------+---------------------------------------------------+---------------------+
| Updating a flow log | PUT /v1/{project_id}/fl/flow_logs/{flowlog_id}    | vpc:flowLogs:update |
+---------------------+---------------------------------------------------+---------------------+
| Deleting a flow log | DELETE /v1/{project_id}/fl/flow_logs/{flowlog_id} | vpc:flowLogs:delete |
+---------------------+---------------------------------------------------+---------------------+
