:original_name: vpc_firewall_0016.html

.. _vpc_firewall_0016:

Updating a Firewall Group
=========================

Function
--------

This API is used to update a firewall group.

URI
---

PUT /v2.0/fwaas/firewall_groups/{firewall_group_id}

Request Parameters
------------------

.. table:: **Table 1** Request parameter

   +----------------+----------------------------------------------------------------------+-----------+--------------------------------------------------------------------------------------------------------+
   | Parameter      | Type                                                                 | Mandatory | Description                                                                                            |
   +================+======================================================================+===========+========================================================================================================+
   | firewall_group | :ref:`firewall_group <vpc_firewall_0016__table1368812022812>` object | Yes       | Specifies the firewall group. For details, see :ref:`Table 2 <vpc_firewall_0016__table1368812022812>`. |
   +----------------+----------------------------------------------------------------------+-----------+--------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0016__table1368812022812:

.. table:: **Table 2** **Firewall Group** objects

   +----------------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Mandatory       | Type             | Description                                                                                                                                                                                                     |
   +============================+=================+==================+=================================================================================================================================================================================================================+
   | name                       | No              | String           | Specifies the name of the firewall group.                                                                                                                                                                       |
   |                            |                 |                  |                                                                                                                                                                                                                 |
   |                            |                 |                  | The value can contain a maximum of 255 characters.                                                                                                                                                              |
   +----------------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                | No              | String           | Provides supplementary information about the firewall group.                                                                                                                                                    |
   |                            |                 |                  |                                                                                                                                                                                                                 |
   |                            |                 |                  | The value can contain a maximum of 255 characters.                                                                                                                                                              |
   +----------------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ingress_firewall_policy_id | No              | String           | Specifies the firewall policy for inbound traffic.                                                                                                                                                              |
   +----------------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | egress_firewall_policy_id  | No              | String           | Specifies the firewall policy for outbound traffic.                                                                                                                                                             |
   +----------------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ports                      | No              | Array of strings | Specifies the list of ports bound with the firewall group.                                                                                                                                                      |
   |                            |                 |                  |                                                                                                                                                                                                                 |
   |                            |                 |                  | The value must be the port ID.                                                                                                                                                                                  |
   |                            |                 |                  |                                                                                                                                                                                                                 |
   |                            |                 |                  | .. note::                                                                                                                                                                                                       |
   |                            |                 |                  |                                                                                                                                                                                                                 |
   |                            |                 |                  |    The port is the one whose **device_owner** is **network:router_interface_distributed**.                                                                                                                      |
   |                            |                 |                  |                                                                                                                                                                                                                 |
   |                            |                 |                  |    -  Call the VPC API for querying the port ID. The filtering criteria are the specified **network_id** and **device_owner**. The **network_id** is the network ID of the subnet associated with the firewall. |
   |                            |                 |                  |                                                                                                                                                                                                                 |
   |                            |                 |                  |       Example:                                                                                                                                                                                                  |
   |                            |                 |                  |                                                                                                                                                                                                                 |
   |                            |                 |                  |       .. code:: text                                                                                                                                                                                            |
   |                            |                 |                  |                                                                                                                                                                                                                 |
   |                            |                 |                  |          GET https://{Endpoint}/v1/{project_id}/ports?network_id={network_id}&device_owner=network%3Arouter_interface_distributed                                                                               |
   +----------------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up             | No              | Boolean          | Specifies the administrative status of the firewall.                                                                                                                                                            |
   |                            |                 |                  |                                                                                                                                                                                                                 |
   |                            |                 |                  | The value can be **true** or **false**.                                                                                                                                                                         |
   +----------------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Associate the ACL group whose ID is 2fb0e81f-9f63-44b2-9894-c13a3284594a with the outbound ACL policy 53f36c32-db25-4856-a0ba-e605fd88c5e9.

.. code-block:: text

   PUT https://{Endpoint}/v2.0/fwaas/firewall_groups/2fb0e81f-9f63-44b2-9894-c13a3284594a

   {
       "firewall_group": {
           "egress_firewall_policy_id": "53f36c32-db25-4856-a0ba-e605fd88c5e9"
       }
   }

Response Parameters
-------------------

.. table:: **Table 3** Response parameter

   +----------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Parameter      | Type                                                                  | Description                                                                                             |
   +================+=======================================================================+=========================================================================================================+
   | firewall_group | :ref:`firewall_group <vpc_firewall_0016__table31629250121127>` object | Specifies the firewall group. For details, see :ref:`Table 4 <vpc_firewall_0016__table31629250121127>`. |
   +----------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0016__table31629250121127:

.. table:: **Table 4** **Firewall Group** objects

   +----------------------------+-----------------------+--------------------------------------------------------------------------+
   | Parameter                  | Type                  | Description                                                              |
   +============================+=======================+==========================================================================+
   | id                         | String                | Specifies the UUID of the firewall group.                                |
   +----------------------------+-----------------------+--------------------------------------------------------------------------+
   | name                       | String                | Specifies the name of the firewall group.                                |
   +----------------------------+-----------------------+--------------------------------------------------------------------------+
   | description                | String                | Provides supplementary information about the firewall group.             |
   +----------------------------+-----------------------+--------------------------------------------------------------------------+
   | tenant_id                  | String                | Specifies the project ID.                                                |
   +----------------------------+-----------------------+--------------------------------------------------------------------------+
   | ingress_firewall_policy_id | String                | Specifies the firewall policy for inbound traffic.                       |
   +----------------------------+-----------------------+--------------------------------------------------------------------------+
   | egress_firewall_policy_id  | String                | Specifies the firewall policy for outbound traffic.                      |
   +----------------------------+-----------------------+--------------------------------------------------------------------------+
   | ports                      | Array of strings      | Specifies the list of ports bound with the firewall group.               |
   +----------------------------+-----------------------+--------------------------------------------------------------------------+
   | public                     | Boolean               | Specifies whether the firewall group can be shared by different tenants. |
   +----------------------------+-----------------------+--------------------------------------------------------------------------+
   | status                     | String                | Specifies the status of the firewall policy.                             |
   |                            |                       |                                                                          |
   |                            |                       | The value can be:                                                        |
   |                            |                       |                                                                          |
   |                            |                       | -  **ACTIVE** (Normal)                                                   |
   |                            |                       | -  **INACTIVE** (Inactive)                                               |
   |                            |                       | -  **ERROR** (Error occurred)                                            |
   |                            |                       | -  **PENDING_CREATE** (Creating)                                         |
   |                            |                       | -  **PENDING_UPDATE** (Updating)                                         |
   |                            |                       | -  **PENDING_DELETE** (Deleting)                                         |
   +----------------------------+-----------------------+--------------------------------------------------------------------------+
   | admin_state_up             | Boolean               | Specifies the administrative status of the firewall.                     |
   +----------------------------+-----------------------+--------------------------------------------------------------------------+
   | project_id                 | String                | Specifies the project ID.                                                |
   +----------------------------+-----------------------+--------------------------------------------------------------------------+
   | created_at                 | String                | Specifies the time (UTC) when the resource is created.                   |
   |                            |                       |                                                                          |
   |                            |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                            |
   +----------------------------+-----------------------+--------------------------------------------------------------------------+
   | updated_at                 | String                | Specifies the time (UTC) when the resource is updated.                   |
   |                            |                       |                                                                          |
   |                            |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                            |
   +----------------------------+-----------------------+--------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "firewall_group": {
           "status": "PENDING_UPDATE",
           "public": false,
           "egress_firewall_policy_id": "53f36c32-db25-4856-a0ba-e605fd88c5e9",
           "name": "",
           "admin_state_up": true,
           "ports": [
               "c133f2bf-6937-4416-bb17-012e1be5cd2d"
           ],
           "tenant_id": "23c8a121505047b6869edf39f3062712",
           "id": "0415f554-26ed-44e7-a881-bdf4e6216e38",
           "ingress_firewall_policy_id": "afc52ce9-5305-4ec9-9feb-44feb8330341",
           "description": "",
           "project_id": "23c8a121505047b6869edf39f3062712",
           "created_at": "2018-09-12T08:24:14",
           "updated_at": "2018-09-12T08:24:14"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
