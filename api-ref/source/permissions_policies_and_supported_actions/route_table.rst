:original_name: en-us_topic_0000001234585289.html

.. _en-us_topic_0000001234585289:

Route Table
===========

+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Permission                                | API                                                      | Action                    |
+===========================================+==========================================================+===========================+
| Querying Route Tables                     | GET /v1/{project_id}/routetables                         | vpc:routeTables:list      |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Querying a Route Table                    | GET /v1/{project_id}/routetables/{routetable_id}         | vpc:routeTables:get       |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Creating a Route Table                    | POST /v1/{project_id}/routetables                        | vpc:routeTables:create    |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Updating a Route Table                    | UPDATE /v1/{project_id}/routetables/{routetable_id}      | vpc:routeTables:update    |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Associating Subnets with a Route Table    | POST /v1/{project_id}/routetables/{routetable_id}/action | vpc:routeTables:associate |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Disassociating Subnets from a Route Table | POST /v1/{project_id}/routetables/{routetable_id}/action | vpc:routeTables:associate |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
| Deleting a Route Table                    | DELETE /v1/{project_id}/routetables/{routetable_id}      | vpc:routeTables:delete    |
+-------------------------------------------+----------------------------------------------------------+---------------------------+
