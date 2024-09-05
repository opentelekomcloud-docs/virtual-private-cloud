:original_name: vpc_permission_0031.html

.. _vpc_permission_0031:

EIP V3
======

+-----------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Permission                        | API                                                                     | Action                             |
+===================================+=========================================================================+====================================+
| Querying all EIPs                 | GET /v3/{project_id}/eip/publicips                                      | eip:publicIps:list                 |
+-----------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Querying the details of an EIP    | GET /v3/{project_id}/eip/publicips/{publicip_id}                        | eip:publicIps:get                  |
+-----------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Binding an EIP to an instance     | POST /v3/{project_id}/eip/publicips/{publicip_id}/associate-instance    | eip:publicIps:associateInstance    |
+-----------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Unbinding an EIP from an instance | POST /v3/{project_id}/eip/publicips/{publicip_id}/disassociate-instance | eip:publicIps:disassociateInstance |
+-----------------------------------+-------------------------------------------------------------------------+------------------------------------+
| Querying common pools             | GET /v3/{project_id}/eip/publicip-pools/common-pools                    | eip:publicipPools:list             |
+-----------------------------------+-------------------------------------------------------------------------+------------------------------------+
