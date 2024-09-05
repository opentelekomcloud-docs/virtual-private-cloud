:original_name: vpc_eip_0004.html

.. _vpc_eip_0004:

Updating an EIP
===============

Function
--------

This API is used to bind an EIP to a NIC, or unbind an EIP from a NIC.

.. note::

   Note the following when you use EIPs of the Dedicated Load Balancer (**5_gray**) type:

   -  In **eu-de**, no more new EIPs of this type can be assigned. You can assign EIPs of the BGP (**5_bgp**) type.
   -  Existing EIPs of the Dedicated Load Balancer (**5_gray**) type can be bound to dedicated or shared load balancers.

      -  The EIP console cannot be used to bind EIPs to or unbind them from dedicated load balancers.
      -  You can use APIs to bind EIPs to or unbind them from dedicated load balancers. For details, see `Binding an EIP <https://docs.otc.t-systems.com/elastic-ip/api-ref/api_v3/eips/binding_an_eip.html>`__ and `Unbinding an EIP <https://docs.otc.t-systems.com/elastic-ip/api-ref/api_v3/eips/unbinding_an_eip.html>`__.
      -  EIPs of this type can be bound to or unbound from shared load balancers using the EIP console or APIs.
      -  You are advised to bind or unbind BGP EIPs to or from dedicated load balancers.

   -  **5_gray** EIPs cannot be added to the same shared bandwidth as EIPs of other types. If they are in the same shared bandwidth, the bandwidth limit settings will not take effect.

URI
---

PUT /v1/{project_id}/publicips/{publicip_id}

:ref:`Table 1 <vpc_eip_0004__table25231885>` describes the parameters.

.. _vpc_eip_0004__table25231885:

.. table:: **Table 1** Parameter description

   =========== ========= ==========================================
   Parameter   Mandatory Description
   =========== ========= ==========================================
   project_id  Yes       Specifies the project ID.
   publicip_id Yes       Specifies the unique identifier of an EIP.
   =========== ========= ==========================================

Request Message
---------------

-  Request parameter

   .. table:: **Table 2** Request parameter

      +-----------+-----------+------------------------------------------------------+------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type                                                 | Description                                                                              |
      +===========+===========+======================================================+==========================================================================================+
      | publicip  | Yes       | :ref:`publicip <vpc_eip_0004__table23403840>` object | Specifies the EIP object. For details, see :ref:`Table 3 <vpc_eip_0004__table23403840>`. |
      +-----------+-----------+------------------------------------------------------+------------------------------------------------------------------------------------------+

   .. _vpc_eip_0004__table23403840:

   .. table:: **Table 3** Description of the **publicip** field

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                              |
      +=================+=================+=================+==========================================================================================================================================================================================================================================================+
      | port_id         | No              | String          | -  Specifies the port ID.                                                                                                                                                                                                                                |
      |                 |                 |                 |                                                                                                                                                                                                                                                          |
      |                 |                 |                 | -  The value must be an existing port ID. If this parameter is not included or the parameter value is left blank, the EIP is unbound. If the specified port ID does not exist or has already been bound with an EIP, an error message will be displayed. |
      |                 |                 |                 |                                                                                                                                                                                                                                                          |
      |                 |                 |                 |    Leaving this parameter blank does not unbind the EIP from the dedicated load balancer.                                                                                                                                                                |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | alias           | No              | String          | -  Specifies the EIP name.                                                                                                                                                                                                                               |
      |                 |                 |                 | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                                                                   |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request 1 (Binding an EIP to a NIC)

   .. code-block:: text

      PUT https://{Endpoint}/v1/{project_id}/publicips/{publicip_id}

      {
          "publicip": {
              "port_id": "f588ccfa-8750-4d7c-bf5d-2ede24414706"
          }
      }

Response Message
----------------

-  Response parameter

   .. table:: **Table 4** Response parameter

      +-----------+---------------------------------------------------------+---------------------------------------------------------------------------------------------+
      | Parameter | Type                                                    | Description                                                                                 |
      +===========+=========================================================+=============================================================================================+
      | publicip  | :ref:`publicip <vpc_eip_0004__table83964341880>` object | Specifies the EIP object. For details, see :ref:`Table 5 <vpc_eip_0004__table83964341880>`. |
      +-----------+---------------------------------------------------------+---------------------------------------------------------------------------------------------+

   .. _vpc_eip_0004__table83964341880:

   .. table:: **Table 5** Description of the **publicips** field

      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                                                      | Description                                                                                                                                      |
      +=======================+===========================================================+==================================================================================================================================================+
      | id                    | String                                                    | Specifies the unique identifier of an EIP.                                                                                                       |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                                                    | -  Specifies the EIP status.                                                                                                                     |
      |                       |                                                           | -  Possible values are as follows:                                                                                                               |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           |    -  **FREEZED** (Frozen)                                                                                                                       |
      |                       |                                                           |    -  **BIND_ERROR** (Binding failed)                                                                                                            |
      |                       |                                                           |    -  **BINDING** (Binding)                                                                                                                      |
      |                       |                                                           |    -  **PENDING_DELETE** (Releasing)                                                                                                             |
      |                       |                                                           |    -  **PENDING_CREATE** (Assigning)                                                                                                             |
      |                       |                                                           |    -  **PENDING_UPDATE** (Updating)                                                                                                              |
      |                       |                                                           |    -  **NOTIFYING** (Assigning)                                                                                                                  |
      |                       |                                                           |    -  **NOTIFY_DELETE** (Releasing)                                                                                                              |
      |                       |                                                           |    -  **DOWN** (Unbound)                                                                                                                         |
      |                       |                                                           |    -  **ACTIVE** (Bound)                                                                                                                         |
      |                       |                                                           |    -  **ELB** (Bound to a load balancer)                                                                                                         |
      |                       |                                                           |    -  **VPN** (Bound to a VPN)                                                                                                                   |
      |                       |                                                           |    -  **ERROR** (Exceptions)                                                                                                                     |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | profile               | :ref:`profile <vpc_eip_0004__table66651219193417>` object | Specifies the additional parameters, including the order ID and product ID. For details, see :ref:`Table 6 <vpc_eip_0004__table66651219193417>`. |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           | This parameter is not supported currently.                                                                                                       |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                                                    | -  Specifies the EIP type.                                                                                                                       |
      |                       |                                                           | -  The value can be **5_bgp** (Dynamic BGP), **5_mailbgp** (Mail BGP), **5_gray** (Dedicated Load Balancer), or **5_dualStack**.                 |
      |                       |                                                           | -  Constraints:                                                                                                                                  |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           |    -  The configured value must be supported by the system.                                                                                      |
      |                       |                                                           |    -  **publicip_id** is an IPv4 port. If **publicip_type** is not specified, the default value is **5_bgp**.                                    |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | public_ip_address     | String                                                    | Specifies the obtained EIP if only IPv4 EIPs are available. (IPv6 is not supported currently.)                                                   |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | ip_version            | Integer                                                   | Specifies the IP address version. The value can be **4** or **6**.                                                                               |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           | -  **4**: IPv4                                                                                                                                   |
      |                       |                                                           | -  **6**: IPv6 (IPv6 is not supported currently.)                                                                                                |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | private_ip_address    | String                                                    | -  Specifies the private IP address bound to the EIP.                                                                                            |
      |                       |                                                           | -  This parameter is returned only when a port is associated with the EIP.                                                                       |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           | .. note::                                                                                                                                        |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           |    This parameter is not displayed if the EIP is bound to a dedicated load balancer. This parameter is displayed if the EIP is bound to an ECS.  |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | port_id               | String                                                    | -  Specifies the port ID.                                                                                                                        |
      |                       |                                                           | -  This parameter is returned only when a port is associated with the EIP.                                                                       |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           | .. note::                                                                                                                                        |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           |    This parameter is not displayed if the EIP is bound to a dedicated load balancer. This parameter is displayed if the EIP is bound to an ECS.  |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | tenant_id             | String                                                    | Specifies the project ID.                                                                                                                        |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | create_time           | String                                                    | Specifies the time (UTC) when the EIP is assigned.                                                                                               |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           | Format: *yyyy-MM-dd HH:mm:ss*                                                                                                                    |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | bandwidth_id          | String                                                    | Specifies the ID of the EIP bandwidth.                                                                                                           |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | bandwidth_size        | Integer                                                   | Specifies the bandwidth (Mbit/s).                                                                                                                |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | bandwidth_share_type  | String                                                    | -  Specifies the EIP bandwidth type.                                                                                                             |
      |                       |                                                           | -  The value can be **PER** or **WHOLE**.                                                                                                        |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           |    -  **PER**: Dedicated bandwidth                                                                                                               |
      |                       |                                                           |    -  **WHOLE**: Shared bandwidth                                                                                                                |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | alias                 | String                                                    | Specifies the EIP name.                                                                                                                          |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | enterprise_project_id | String                                                    | -  Specifies the enterprise project ID. The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). |
      |                       |                                                           | -  When you assign an EIP, associate an enterprise project ID with the EIP.                                                                      |
      |                       |                                                           | -  If this parameter is not specified, the default value is **0**, which indicates that the default enterprise project is used.                  |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           | .. note::                                                                                                                                        |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           |    This parameter is unsupported. Do not use it.                                                                                                 |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | public_border_group   | String                                                    | Specifies whether it is in a central site or an edge site.                                                                                       |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           | The value can be:                                                                                                                                |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           | -  center                                                                                                                                        |
      |                       |                                                           | -  *Edge site name*                                                                                                                              |
      |                       |                                                           |                                                                                                                                                  |
      |                       |                                                           | An EIP can only be bound to a resource of the same region.                                                                                       |
      +-----------------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _vpc_eip_0004__table66651219193417:

   .. table:: **Table 6** Description of the **profile** field

      ========== ====== =========================
      Parameter  Type   Description
      ========== ====== =========================
      order_id   String Specifies the order ID.
      product_id String Specifies the product ID.
      region_id  String Specifies the region ID.
      user_id    String Specifies the user ID.
      ========== ====== =========================

-  Example response (Binding an EIP to a NIC)

   .. code-block::

      {
        "publicip": {
          "id": "f6318bef-6508-4ea5-a48f-6152b6b1a8fb",
          "status": "ACTIVE",
          "alias": "tom",
          "profile": {},
          "type": "5_bgp",
          "port_id": "a135e9b8-1630-40d2-a6c5-eb534a61efbe",
          "public_ip_address": "10.xx.xx.162",
          "private_ip_address": "192.168.1.131",
          "tenant_id": "26ae5181a416420998eb2093aaed84d9",
          "create_time": "2019-03-27 01:33:18",
          "bandwidth_size": 7,
          "ip_version": 4,
          "bandwidth_name": "bandwidth-2aef",
          "enterprise_project_id": "0",
          "bandwidth_share_type": "PER",
          "bandwidth_id": "7a258fff-10d8-44b8-8124-c59079eb8f4c"
        }
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
