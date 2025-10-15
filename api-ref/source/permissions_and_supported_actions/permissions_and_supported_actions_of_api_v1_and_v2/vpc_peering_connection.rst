:original_name: vpc_permission_0005.html

.. _vpc_permission_0005:

VPC Peering Connection
======================

+------------------------------------+--------------------------------------------+---------------------+
| Permission                         | API                                        | Action              |
+====================================+============================================+=====================+
| Querying VPC peering connections   | GET /v2.0/vpc/peerings                     | vpc:peerings:get    |
+------------------------------------+--------------------------------------------+---------------------+
| Querying a VPC peering connection  | GET /v2.0/vpc/peerings/{peering_id}        | vpc:peerings:get    |
+------------------------------------+--------------------------------------------+---------------------+
| Creating a VPC peering connection  | POST /v2.0/vpc/peerings                    | vpc:peerings:create |
+------------------------------------+--------------------------------------------+---------------------+
| Accepting a VPC peering connection | PUT /v2.0/vpc/peerings/{peering_id}/accept | vpc:peerings:accept |
+------------------------------------+--------------------------------------------+---------------------+
| Refusing a VPC peering connection  | PUT /v2.0/vpc/peerings/{peering_id}/reject | vpc:peerings:reject |
+------------------------------------+--------------------------------------------+---------------------+
| Updating a VPC peering connection  | PUT /v2.0/vpc/peerings/{peering_id}        | vpc:peerings:update |
+------------------------------------+--------------------------------------------+---------------------+
| Deleting a VPC peering connection  | DELETE /v2.0/vpc/peerings/{peering_id}     | vpc:peerings:delete |
+------------------------------------+--------------------------------------------+---------------------+
