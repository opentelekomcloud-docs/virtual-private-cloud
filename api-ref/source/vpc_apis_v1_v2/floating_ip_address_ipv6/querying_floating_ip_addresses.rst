:original_name: vpc_ipv6_0001.html

.. _vpc_ipv6_0001:

Querying Floating IP Addresses
==============================

Function
--------

This API is used to query all floating IP addresses accessible to the tenant submitting the request.

URI
---

GET /v2.0/eip/floatingips_v6

Example:

.. code-block:: text

   GET https://{Endpoint}/v2.0/eip/floatingips_v6?id={id}&router_id={router_id}&floating_network_id={floating_network_id}&floating_ip_address={floating_ip_address}&port_id={port_id }&fixed_ip_address={fixed_ip_address}&tenant_id={tenant_id}

:ref:`Table 1 <vpc_ipv6_0001__table668331194113>` describes the parameters.

.. _vpc_ipv6_0001__table668331194113:

.. table:: **Table 1** Parameter description

   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                                                                                       |
   +=====================+=================+=================+===================================================================================================================================================+
   | id                  | Yes             | String          | Specifies the floating IP address ID.                                                                                                             |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | floating_ip_address | No              | String          | Specifies the floating IPv6 address.                                                                                                              |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | floating_network_id | No              | String          | Specifies the external network ID.                                                                                                                |
   |                     |                 |                 |                                                                                                                                                   |
   |                     |                 |                 | You can only use fixed external network.                                                                                                          |
   |                     |                 |                 |                                                                                                                                                   |
   |                     |                 |                 | You can use **GET /v2.0/networks?router:external=True** or                                                                                        |
   |                     |                 |                 |                                                                                                                                                   |
   |                     |                 |                 | **GET /v2.0/networks?name={floating_network}** or run the **neutron net-external-list** command to obtain information about the external network. |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | router_id           | No              | String          | Specifies the ID of the belonged router.                                                                                                          |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_id             | No              | String          | Specifies the port ID.                                                                                                                            |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | fixed_ip_address    | No              | String          | Specifies the private IP address of the associated port.                                                                                          |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id           | No              | String          | Specifies the project ID.                                                                                                                         |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id          | No              | String          | Specifies the project ID.                                                                                                                         |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

-  Request parameter

   None

-  Example request

   None

Response Message
----------------

-  Response parameter

.. table:: **Table 2** Response parameter

   +-------------+--------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type                                                                     | Description                                                                                                    |
   +=============+==========================================================================+================================================================================================================+
   | floatingips | Array of :ref:`floatingip <vpc_ipv6_0001__table129961748135412>` objects | Specifies the floating IP address list. For details, see :ref:`Table 3 <vpc_ipv6_0001__table129961748135412>`. |
   +-------------+--------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

.. _vpc_ipv6_0001__table129961748135412:

.. table:: **Table 3** **floatingip** objects

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                    |
   +=======================+=======================+================================================================================================+
   | status                | String                | Specifies the floating IP address status. The value can be **ACTIVE**, **DOWN**, or **ERROR**. |
   |                       |                       |                                                                                                |
   |                       |                       | -  **ACTIVE** indicates that the floating IP address has been bound.                           |
   |                       |                       | -  **ERROR** indicates that the floating IP address is abnormal.                               |
   |                       |                       | -  **DOWN** indicates that the floating IP address has not been bound.                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | id                    | String                | Specifies the floating IP address ID.                                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | floating_ip_address   | String                | Specifies the floating IPv6 address.                                                           |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | floating_network_id   | String                | Specifies the external network ID.                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | router_id             | String                | Specifies the ID of the belonged router.                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | port_id               | String                | Specifies the port ID.                                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | fixed_ip_address      | String                | Specifies the private IP address of the associated port.                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | tenant_id             | String                | Specifies the project ID.                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | project_id            | String                | Specifies the project ID.                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | created_at            | String                | Specifies the time when the resource was created.                                              |
   |                       |                       |                                                                                                |
   |                       |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | updated_at            | String                | Specifies the time when the resource was updated.                                              |
   |                       |                       |                                                                                                |
   |                       |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | floatingips_links     | Array of strings      | Specifies the request URL.                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "floatingips": [
          {
            "id": "861a4c5b-b17b-4a1d-b653-f3e95dcb3345",
            "status": "DOWN",
            "router_id": null,
            "tenant_id": "26ae5181a416420998eb2093aaed84d9",
            "floating_network_id": "0a2228f2-7f8a-45f1-8e09-9039e1d09975",
            "fixed_ip_address": null,
            "floating_ip_address": "cdcd:910a:2222:5498:8475:1111:c613:16e3",
            "port_id": null,
            "project_id": "26ae5181a416420998eb2093aaed84d9",
            "created_at": "2024-05-23T09:20:59",
            "updated_at": "2024-05-28T15:02:53"
          }
        ],
        "floatingips_links": [
          {
            "href": "https://vpc.region.otctest.t-systems.com/v2.0/floatingips_v6?marker=861a4c5b-b17b-4a1d-b653-f3e95dcb3345&page_reverse=true&page_reverse=True",
            "rel": "previous"
          }
        ]
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
