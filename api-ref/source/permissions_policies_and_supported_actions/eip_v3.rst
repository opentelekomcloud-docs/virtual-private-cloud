:original_name: vpc_permission_0031.html

.. _vpc_permission_0031:

EIP V3
======

+---------------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Permission                            | API                                                                     | Action                             |
+=======================================+=========================================================================+====================================+
| Querying all EIPs                     | GET /v3/{project_id}/eip/publicips                                      | eip:publicIps:list                 |
+---------------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Querying the details of an EIP        | GET /v3/{project_id}/eip/publicips/{publicip_id}                        | eip:publicIps:get                  |
+---------------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Updating an EIP                       | PUT /v3/{project_id}/eip/publicips/{publicip_id}                        | eip:publicIps:update               |
+---------------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Binding an EIP to an instance         | POST /v3/{project_id}/eip/publicips/{publicip_id}/associate-instance    | eip:publicIps:associateInstance    |
+---------------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Unbinding an EIP from an instance     | POST /v3/{project_id}/eip/publicips/{publicip_id}/disassociate-instance | eip:publicIps:disassociateInstance |
+---------------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Adding EIPs to a shared bandwidth     | POST /v3/{project_id}/eip/publicips/attach-share-bandwidth              | eip:publicIps:attachBandwidth      |
+---------------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Querying the number of available EIPs | POST /v3/{project_id}/eip/resources/available                           | eip:publicIps:count                |
+---------------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Querying common pools                 | GET /v3/{project_id}/eip/publicip-pools/common-pools                    | eip:publicipPools:list             |
+---------------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Querying EIP pools                    | GET /v3/{project_id}/eip/publicip-pools                                 | eip:publicipPools:list             |
+---------------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Querying the details of an EIP pool   | GET /v3/{project_id}/eip/publicip-pools/{publicip_pool_id}              | eip:publicipPools:get              |
+---------------------------------------+-------------------------------------------------------------------------+------------------------------------+
