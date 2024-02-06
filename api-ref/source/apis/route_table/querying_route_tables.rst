:original_name: vpc_apiroutetab_0001.html

.. _vpc_apiroutetab_0001:

Querying Route Tables
=====================

Function
--------

This API is used to query all route tables of the tenant submitting the request. The route tables are filtered based on the filtering condition.

URI
---

GET /v1/{project_id}/routetables

Example:

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/routetables?limit=10&marker=4779ab1c-7c1a-44b1-a02e-93dfc361b32d&vpc_id=3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85&subnet_id=9873b33f-ac1c-4630-ad1c-7dba1ed79r78

:ref:`Table 1 <vpc_apiroutetab_0001__table135921530121310>` describes the parameters.

.. _vpc_apiroutetab_0001__table135921530121310:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================+
   | project_id      | Yes             | String          | Specifies the project ID.                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax (2^31-1). The default value is 2000.                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Specifies a resource ID for pagination query, indicating that the query starts from the next record of the specified resource ID.                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | This parameter can work together with the parameter **limit**.                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | -  If parameters **marker** and **limit** are not passed, resource records on the first page will be returned.                                                                                                         |
   |                 |                 |                 | -  If the parameter **marker** is not passed and the value of parameter **limit** is set to **10**, the first 10 resource records will be returned.                                                                    |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the value of parameter **limit** is set to **10**, the 11th to 20th resource records will be returned.                    |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the parameter **limit** is not passed, resource records starting from the 11th records (including 11th) will be returned. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id              | No              | String          | Specifies the route table ID, which can be used to filter the route table with the corresponding ID.                                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id          | No              | String          | Specifies the VPC UUID.                                                                                                                                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnet_id       | No              | String          | Specifies the subnet ID.                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | If you use the management console, the value of this parameter is the **Network ID** value.                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/routetables?limit=10&marker=4779ab1c-7c1a-44b1-a02e-93dfc361b32d&vpc_id=3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85&subnet_id=9873b33f-ac1c-4630-ad1c-7dba1ed79r78

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | Name        | Type                                                                          | Description                                                                                                 |
   +=============+===============================================================================+=============================================================================================================+
   | routetables | Array of :ref:`routetable <vpc_apiroutetab_0001__table5685153016131>` objects | Specifies the route table list. For details, see :ref:`Table 3 <vpc_apiroutetab_0001__table5685153016131>`. |
   +-------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0001__table5685153016131:

.. table:: **Table 3** Description of the **routetable** field

   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Type                                                                      | Description                                                                                                                           |
   +=======================+===========================================================================+=======================================================================================================================================+
   | id                    | String                                                                    | -  Specifies the route table ID, which uniquely identifies the route table.                                                           |
   |                       |                                                                           | -  The value must be in standard UUID format.                                                                                         |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                    | -  Specifies the route table name.                                                                                                    |
   |                       |                                                                           | -  The value can contain no more than 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).        |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | default               | Boolean                                                                   | -  Specifies whether the route table is the default one.                                                                              |
   |                       |                                                                           | -  The value can be **true** (default route table) or **false** (custom route table).                                                 |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | subnets               | Array of :ref:`subnet <vpc_apiroutetab_0001__table4856530131313>` objects | -  Specifies the subnets associated with the route table. For details, see :ref:`Table 4 <vpc_apiroutetab_0001__table4856530131313>`. |
   |                       |                                                                           | -  Only subnets in the VPC to which the route table belongs can be associated with the route table.                                   |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                                                                    | -  Specifies the project ID.                                                                                                          |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id                | String                                                                    | -  Specifies the ID of the VPC associated with the route table.                                                                       |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                    | -  Provides supplementary information about the route table.                                                                          |
   |                       |                                                                           | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                      |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                    | -  Specifies the time (UTC) when the route table is created.                                                                          |
   |                       |                                                                           | -  Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                      |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                    | -  Specifies the time (UTC) when the route table is updated.                                                                          |
   |                       |                                                                           | -  Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                      |
   +-----------------------+---------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiroutetab_0001__table4856530131313:

.. table:: **Table 4** Description of the **subnet** field

   +------+--------+-----------------------------------------------------------------+
   | Name | Type   | Description                                                     |
   +======+========+=================================================================+
   | id   | String | Specifies the ID of the subnet associated with the route table. |
   +------+--------+-----------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "routetables": [
           {
               "id": "3d42a0d4-a980-4613-ae76-a2cddecff054",
               "name": "routetable-1234",
               "vpc_id": "ab78be2d-782f-42a5-aa72-35879f6890ff",
               "subnets": [
                   {
                       "id": "8d4ce32f-d68a-4c4c-9f18-c68d8a5c7f2f"
                   }
               ],
               "tenant_id": "6fbe9263116a4b68818cf1edce16bc4f",
               "description": "abc",
               "created_at": "2022-12-15T02:56:40",
               "updated_at": "2022-12-15T02:56:40"
           },
           {
               "id": "3d42a0d4-a980-4613-ae76-a2cddecfff89",
               "name": "routetable-5678",
               "vpc_id": "ab78be2d-782f-42a5-aa72-35879f667809",
               "subnets": [
                   {
                       "id": "8d4ce32f-d68a-4c4c-9f18-c68d8a5c7f2f"
                   }
               ],
               "tenant_id": "6fbe9263116a4b68818cf1edce16bc4f",
               "description": "abc",
               "created_at": "2022-12-15T02:59:03",
               "updated_at": "2022-12-15T02:59:03"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
