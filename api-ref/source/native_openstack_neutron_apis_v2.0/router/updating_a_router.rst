:original_name: vpc_router_0004.html

.. _vpc_router_0004:

Updating a Router
=================

Function
--------

This API is used to update a router.

URI
---

PUT /v2.0/routers/{router_id}

Request Parameters
------------------

.. table:: **Table 1** Request parameter

   +-----------------+-----------------+--------------------------------------------------------------+------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                         | Description                                                                                    |
   +=================+=================+==============================================================+================================================================================================+
   | router          | Yes             | :ref:`router <vpc_router_0004__table128801154104715>` object | Specifies the router. For details, see :ref:`Table 2 <vpc_router_0004__table128801154104715>`. |
   |                 |                 |                                                              |                                                                                                |
   |                 |                 |                                                              | You must specify at least one attribute when updating a router.                                |
   +-----------------+-----------------+--------------------------------------------------------------+------------------------------------------------------------------------------------------------+

.. _vpc_router_0004__table128801154104715:

.. table:: **Table 2** **router** objects

   +-----------------------+-----------------+--------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Attribute             | Mandatory       | Type                                                                     | Description                                                                                                                   |
   +=======================+=================+==========================================================================+===============================================================================================================================+
   | name                  | No              | String                                                                   | Specifies the router name.                                                                                                    |
   |                       |                 |                                                                          |                                                                                                                               |
   |                       |                 |                                                                          | Instructions:                                                                                                                 |
   |                       |                 |                                                                          |                                                                                                                               |
   |                       |                 |                                                                          | The name can contain only letters, digits, underscores (_), hyphens (-), and periods (.).                                     |
   +-----------------------+-----------------+--------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up        | No              | Boolean                                                                  | Specifies the administrative status.                                                                                          |
   |                       |                 |                                                                          |                                                                                                                               |
   |                       |                 |                                                                          | The value can only be **true**.                                                                                               |
   +-----------------------+-----------------+--------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | external_gateway_info | No              | :ref:`external_gateway_info <vpc_router_0004__table189345484710>` object | Specifies the external gateway. This is an extended attribute. For details, see the **external_gateway_info** objects.        |
   +-----------------------+-----------------+--------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | routes                | No              | Array of :ref:`route <vpc_router_0004__table5893155464718>` objects      | Specifies a route list. This is an extended attribute. For details, see :ref:`Table 4 <vpc_router_0004__table5893155464718>`. |
   +-----------------------+-----------------+--------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_router_0004__table189345484710:

.. table:: **Table 3** **external_gateway_info** objects

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Attribute       | Mandatory       | Type            | Description                                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================================+
   | network_id      | No              | String          | Specifies the UUID of the external network.                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                         |
   |                 |                 |                 | You can use **GET /v2.0/networks?router:external=True** or run the **neutron net-external-list** command to query information about the external network.               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enable_snat     | No              | Boolean         | Specifies whether the SNAT function is enabled.                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                         |
   |                 |                 |                 | The default value is **false**.                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                         |
   |                 |                 |                 | Before setting **enable_snat** to **true**, ensure that an interface is added to the router. For details, see :ref:`Adding an Interface to a Router <vpc_router_0006>`. |
   |                 |                 |                 |                                                                                                                                                                         |
   |                 |                 |                 | Once **enable_snat** is set to **true**, a micro NAT gateway will be created.                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_router_0004__table5893155464718:

.. table:: **Table 4** **route** objects

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------+
   | Attribute       | Mandatory       | Type            | Description                                                                                                 |
   +=================+=================+=================+=============================================================================================================+
   | destination     | No              | String          | Specifies the IP address range.                                                                             |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | Instructions:                                                                                               |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | The prefix cannot be the same as that of a direct route.                                                    |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------+
   | nexthop         | No              | String          | Specifies the next hop IP address. The IP address can only be one in the subnet associated with the router. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Change the name of the router whose ID is f5dbdfe0-86f9-4b0a-9a32-6be143f0a076 to **router-220**.

.. code-block:: text

   PUT https://{Endpoint}/v2.0/routers/f5dbdfe0-86f9-4b0a-9a32-6be143f0a076

   {
       "router": {
              "name": "router-220"
       }
   }

Response Parameters
-------------------

.. table:: **Table 5** Response parameter

   +-----------+-------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Parameter | Type                                                        | Description                                                                                   |
   +===========+=============================================================+===============================================================================================+
   | router    | :ref:`router <vpc_router_0004__table24153696181443>` object | Specifies the router. For details, see :ref:`Table 6 <vpc_router_0004__table24153696181443>`. |
   +-----------+-------------------------------------------------------------+-----------------------------------------------------------------------------------------------+

.. _vpc_router_0004__table24153696181443:

.. table:: **Table 6** **router** objects

   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Attribute             | Type                                                                       | Description                                                                                                                    |
   +=======================+============================================================================+================================================================================================================================+
   | id                    | String                                                                     | Specifies the router ID.                                                                                                       |
   |                       |                                                                            |                                                                                                                                |
   |                       |                                                                            | This parameter is not mandatory when you query routers.                                                                        |
   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                     | Specifies the router name.                                                                                                     |
   |                       |                                                                            |                                                                                                                                |
   |                       |                                                                            | The name can contain only letters, digits, underscores (_), hyphens (-), and periods (.).                                      |
   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up        | Boolean                                                                    | Specifies the administrative status.                                                                                           |
   |                       |                                                                            |                                                                                                                                |
   |                       |                                                                            | The value can only be **true**.                                                                                                |
   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                                     | Specifies the router status. The value can be **ACTIVE**, **DOWN**, or **ERROR**.                                              |
   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                                                                     | Specifies the project ID.                                                                                                      |
   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | external_gateway_info | :ref:`external_gateway_info <vpc_router_0004__table11448068181443>` object | Specifies the external gateway. This is an extended attribute. For details, see the **external_gateway_info** objects.         |
   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | routes                | Array of :ref:`route <vpc_router_0004__table18829650181443>` objects       | Specifies a route list. This is an extended attribute. For details, see :ref:`Table 8 <vpc_router_0004__table18829650181443>`. |
   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                                     | Specifies the project ID.                                                                                                      |
   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                     | Specifies the time (UTC) when the router is created.                                                                           |
   |                       |                                                                            |                                                                                                                                |
   |                       |                                                                            | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                  |
   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                     | Specifies the time (UTC) when the router is updated.                                                                           |
   |                       |                                                                            |                                                                                                                                |
   |                       |                                                                            | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                  |
   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_router_0004__table11448068181443:

.. table:: **Table 7** **external_gateway_info** objects

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Attribute             | Type                  | Description                                                                                                                                               |
   +=======================+=======================+===========================================================================================================================================================+
   | network_id            | String                | Specifies the UUID of the external network.                                                                                                               |
   |                       |                       |                                                                                                                                                           |
   |                       |                       | You can use **GET /v2.0/networks?router:external=True** or run the **neutron net-external-list** command to query information about the external network. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enable_snat           | Boolean               | Specifies whether the SNAT function is enabled.                                                                                                           |
   |                       |                       |                                                                                                                                                           |
   |                       |                       | The default value is **false**.                                                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_router_0004__table18829650181443:

.. table:: **Table 8** **route** objects

   +-------------+--------+-------------------------------------------------------------------------------------------------------------+
   | Attribute   | Type   | Description                                                                                                 |
   +=============+========+=============================================================================================================+
   | destination | String | Specifies the IP address range.                                                                             |
   +-------------+--------+-------------------------------------------------------------------------------------------------------------+
   | nexthop     | String | Specifies the next hop IP address. The IP address can only be one in the subnet associated with the router. |
   +-------------+--------+-------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "router": {
           "id": "f5dbdfe0-86f9-4b0a-9a32-6be143f0a076",
           "name": "router-220",
           "status": "ACTIVE",
           "tenant_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
           "project_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
           "admin_state_up": true,
           "external_gateway_info": {
               "network_id": "0a2228f2-7f8a-45f1-8e09-9039e1d09975",
               "enable_snat": false
           },
           "routes": [],
           "created_at": "2018-09-20T02:06:07",
           "updated_at": "2018-09-20T02:06:09"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
