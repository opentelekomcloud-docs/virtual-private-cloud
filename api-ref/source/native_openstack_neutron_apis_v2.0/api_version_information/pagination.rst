:original_name: vpc_version_0003xx.html

.. _vpc_version_0003xx:

Pagination
==========

Function
--------

Neutron APIs v2.0 provides the pagination function. You can set parameters **limit** and **marker** in the URL of the list request to enable the desired number of items to be returned. All returned items are displayed in the ascending order of ID.

-  To access the next page of the request, perform the following configurations:

   -  Replace the value of **marker** in the original access request URL. Replace the value of **marker** to the value of **marker** in the value of **href** if the value of **rel** in the response is **next**.
   -  Set the value of **page_reverse** to **False**.

-  To access the previous page of the request, perform the following configurations:

   -  Replace the value of **marker** in the original access request URL. Replace the value of **marker** to the value of **marker** in the value of **href** if the value of **rel** in the response is **previous**.
   -  Set the value of **page_reverse** to **True**.

Request Parameters
------------------

.. table:: **Table 1** Request parameter

   +--------------+---------+-----------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Type    | Mandatory | Description                                                                                                              |
   +==============+=========+===========+==========================================================================================================================+
   | limit        | Integer | No        | Specifies the number of items displayed per page.                                                                        |
   +--------------+---------+-----------+--------------------------------------------------------------------------------------------------------------------------+
   | marker       | String  | No        | Specifies the ID of the last item in the previous list. If the marker value is invalid, error code 400 will be returned. |
   +--------------+---------+-----------+--------------------------------------------------------------------------------------------------------------------------+
   | page_reverse | Boolean | No        | Specifies the page direction. The value can be **True** or **False**.                                                    |
   +--------------+---------+-----------+--------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  When **page_reverse** is set to **False**:

.. code-block:: text

   GET https://{Endpoint}/v2.0/networks?limit=2&marker=3d42a0d4-a980-4613-ae76-a2cddecff054&page_reverse=False

-  When **page_reverse** is set to **True**:

.. code-block:: text

   GET https://{Endpoint}/v2.0/vpc/peerings?limit=2&marker=e5a0c88e-228e-4e62-a8b0-90825b1b7958&page_reverse=True

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------------------+----------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                             | Description                                                                                                                                                                                                                                                                                                                                                                      |
   +=======================+==================================================================================+==================================================================================================================================================================================================================================================================================================================================================================================+
   | {resources}_links     | Array of :ref:`{resources}_link <vpc_version_0003xx__table109221759807>` objects | Specifies the pagination information. For details, see :ref:`Table 3 <vpc_version_0003xx__table109221759807>`. **{resources}** indicates the resource name, for example, **ports**, **networks**, **subnets**, **routers**, **firewall_rules**, **firewall_policies**, **firewall_groups**, **security_groups**, **subnetpools**, **floatingips**, and **security_group_rules**. |
   |                       |                                                                                  |                                                                                                                                                                                                                                                                                                                                                                                  |
   |                       |                                                                                  | Only when **limit** is used for filtering and the number of resources exceeds the value of **limit** or 2000 (default value of **limit**), value **next** will be returned for **rel** and a link for **href**.                                                                                                                                                                  |
   +-----------------------+----------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_version_0003xx__table109221759807:

.. table:: **Table 3** {resources}_link object

   +-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                              |
   +===========+========+==========================================================================================================================================+
   | href      | String | Specifies the API link.                                                                                                                  |
   +-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------+
   | rel       | String | The API link is used to query the next or previous page. **next**: The next page is queried. **previous**: The previous page is queried. |
   +-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

-  When **page_reverse** is set to **False**:

.. code-block::

   {
       "networks": [
           {
               "status": "ACTIVE",
               "subnets": [],
               "name": "liudongtest ",
               "admin_state_up": false,
               "tenant_id": "6fbe9263116a4b68818cf1edce16bc4f",
               "id": "60c809cb-6731-45d0-ace8-3bf5626421a9"
           },
           {
               "status": "ACTIVE",
               "subnets": [
                   "132dc12d-c02a-4c90-9cd5-c31669aace04"
               ],
               "name": "publicnet",
               "admin_state_up": true,
               "tenant_id": "6fbe9263116a4b68818cf1edce16bc4f",
               "id": "9daeac7c-a98f-430f-8e38-67f9c044e299"
           }
       ],
       "networks_links": [
           {
               "href": "http://192.168.82.231:9696/v2.0/networks?limit=2&marker=9daeac7c-a98f-430f-8e38-67f9c044e299",
               "rel": "next"
           },
           {
               "href": "http://192.168.82.231:9696/v2.0/networks?limit=2&marker=60c809cb-6731-45d0-ace8-3bf5626421a9&page_reverse=True",
               "rel": "previous"
           }
       ]
   }

-  When **page_reverse** is set to **True**:

.. code-block::

   {
       "peerings_links": [
           {
               "marker": "dd442819-5638-401c-bd48-a82703cf0464",
               "rel": "next"
           },
           {
               "marker": "1e13cbaf-3ce4-413d-941f-66d855dbfa7f",
               "rel": "previous"
           }
       ],
       "peerings": [
           {
               "status": "ACTIVE",
               "accept_vpc_info": {
                   "vpc_id": "83a48834-b9bc-4f70-aa46-074568594650",
                   "tenant_id": "e41a43bf06e249678413c6d61536eff9"
               },
               "request_vpc_info": {
                   "vpc_id": "db8e7687-e43b-4fc1-94cf-16f69f484d6d",
                   "tenant_id": "e41a43bf06e249678413c6d61536eff9"
               },
               "name": "peering1",
               "id": "1e13cbaf-3ce4-413d-941f-66d855dbfa7f"
           },
           {
               "status": "ACTIVE",
               "accept_vpc_info": {
                   "vpc_id": "83a48834-b9bc-4f70-aa46-074568594650",
                   "tenant_id": "e41a43bf06e249678413c6d61536eff9"
               },
               "request_vpc_info": {
                   "vpc_id": "bd63cc9e-e7b8-4d4e-a0e9-055031470ffc",
                   "tenant_id": "e41a43bf06e249678413c6d61536eff9"
               },
               "name": "peering2",
               "id": "dd442819-5638-401c-bd48-a82703cf0464"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
