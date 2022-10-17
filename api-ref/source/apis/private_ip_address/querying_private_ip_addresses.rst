:original_name: vpc_privateip_0003.html

.. _vpc_privateip_0003:

Querying Private IP Addresses
=============================

Function
--------

This API is used to query private IP addresses using search criteria and to display the private IP addresses in a list.

URI
---

GET /v1/{project_id}/subnets/{subnet_id}/privateips

Example:

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/subnets/{subnet_id}/privateips?limit=10&marker=4779ab1c-7c1a-44b1-a02e-93dfc361b32d

:ref:`Table 1 <vpc_privateip_0003__table12098568>` describes the parameters.

.. _vpc_privateip_0003__table12098568:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================+
   | project_id      | Yes             | String          | Specifies the project ID.                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnet_id       | Yes             | String          | Specifies the unique ID of the subnet to which the private IP address belongs.                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | If you use the management console, the value of this parameter is the **Network ID** value.                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Specifies a resource ID for pagination query, indicating that the query starts from the next record of the specified resource ID.                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | This parameter can work together with the parameter **limit**.                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | -  If parameters **marker** and **limit** are not passed, all resource records will be returned.                                                                                                                       |
   |                 |                 |                 | -  If the parameter **marker** is not passed and the value of parameter **limit** is set to **10**, the first 10 resource records will be returned.                                                                    |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the value of parameter **limit** is set to **10**, the 11th to 20th resource records will be returned.                    |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the parameter **limit** is not passed, resource records starting from the 11th records (including 11th) will be returned. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax.                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

-  Request parameter

   None

-  Example request

   .. code-block:: text

      GET https://{Endpoint}/v1/{project_id}/subnets/{subnet_id}/privateips

Response Message
----------------

-  Request parameter

   .. table:: **Table 2** Request parameter

      +------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
      | Name       | Type                                                                  | Description                                                                                                    |
      +============+=======================================================================+================================================================================================================+
      | privateips | Array of :ref:`privateip <vpc_privateip_0003__table21538022>` objects | Specifies the private IP address objects. For details, see :ref:`Table 3 <vpc_privateip_0003__table21538022>`. |
      +------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

   .. _vpc_privateip_0003__table21538022:

   .. table:: **Table 3** Description of the **privateip** field

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                                                                                                                                                                            |
      +=======================+=======================+========================================================================================================================================================================================================================================================================================================+
      | status                | String                | -  Specifies the status of the private IP address.                                                                                                                                                                                                                                                     |
      |                       |                       | -  Possible values are as follows:                                                                                                                                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                                                                                                                                        |
      |                       |                       |    -  **ACTIVE**                                                                                                                                                                                                                                                                                       |
      |                       |                       |    -  **DOWN**                                                                                                                                                                                                                                                                                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id                    | String                | Specifies the ID of the private IP address, which uniquely identifies the private IP address.                                                                                                                                                                                                          |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | subnet_id             | String                | Specifies the ID of the subnet from which IP addresses are assigned.                                                                                                                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                                                                                                                                        |
      |                       |                       | If you use the management console, the value of this parameter is the **Network ID** value.                                                                                                                                                                                                            |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tenant_id             | String                | Specifies the project ID.                                                                                                                                                                                                                                                                              |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | device_owner          | String                | -  Specifies the resource using the private IP address. The parameter is left blank if it is not used.                                                                                                                                                                                                 |
      |                       |                       | -  The value can be **network:dhcp**, **network:router_interface_distributed**, **compute:xxx**, or **neutron:VIP_PORT**. (In value **compute:xxx**, **xxx** specifies the AZ name, for example, **compute:aa-bb-cc** indicates that the private IP address is used by an ECS in the **aa-bb-cc** AZ). |
      |                       |                       | -  The value range specifies only the type of private IP addresses supported by the current service.                                                                                                                                                                                                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ip_address            | String                | Specifies the assigned private IP address.                                                                                                                                                                                                                                                             |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "privateips": [
              {
                  "status": "DOWN",
                  "id": "d600542a-b231-45ed-af05-e9930cb14f78",
                  "subnet_id": "531dec0f-3116-411b-a21b-e612e42349fd",
                  "tenant_id": "8b7e35ad379141fc9df3e178bd64f55c",
                  "device_owner": "",
                  "ip_address": "192.168.1.11"
              },
              {
                  "status": "DOWN",
                  "id": "d600542a-b231-45ed-af05-e9930cb14f79",
                  "subnet_id": "531dec0f-3116-411b-a21b-e612e42349fd",
                  "tenant_id": "8b7e35ad379141fc9df3e178bd64f55c",
                  "device_owner": "",
                  "ip_address": "192.168.1.12"
              }
          ]
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
