:original_name: vpc_permission_0029.html

.. _vpc_permission_0029:

Route Table
===========

+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Permission                                | API                                                      | Action                    |
+===========================================+==========================================================+===========================+
| Querying route tables                     | GET /v1/{project_id}/routetables                         | vpc:routeTables:list      |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Querying a route table                    | GET /v1/{project_id}/routetables/{routetable_id}         | vpc:routeTables:get       |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Creating a route table                    | POST /v1/{project_id}/routetables                        | vpc:routeTables:create    |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Updating a route table                    | PUT /v1/{project_id}/routetables/{routetable_id}         | vpc:routeTables:update    |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Associating subnets with a route table    | POST /v1/{project_id}/routetables/{routetable_id}/action | vpc:routeTables:associate |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Disassociating subnets from a route table | POST /v1/{project_id}/routetables/{routetable_id}/action | vpc:routeTables:associate |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Deleting a route table                    | DELETE /v1/{project_id}/routetables/{routetable_id}      | vpc:routeTables:delete    |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
