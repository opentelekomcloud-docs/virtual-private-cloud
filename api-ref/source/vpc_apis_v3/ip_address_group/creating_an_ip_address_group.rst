:original_name: vpc_apiv3_0022.html

.. _vpc_apiv3_0022:

Creating an IP Address Group
============================

Function
--------

This API is used to create an IP address group.

Constraints
-----------

The default IP address group quota for each account is 50.

URI
---

POST /v3/{project_id}/vpc/address-groups

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+-------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                      | Description                                                                                                                                                                                                                                                                       |
   +=================+=================+===========================================================================================+===================================================================================================================================================================================================================================================================================+
   | dry_run         | No              | Boolean                                                                                   | -  Whether to only send the check request.                                                                                                                                                                                                                                        |
   |                 |                 |                                                                                           |                                                                                                                                                                                                                                                                                   |
   |                 |                 |                                                                                           | -  The value can be one of the following:                                                                                                                                                                                                                                         |
   |                 |                 |                                                                                           |                                                                                                                                                                                                                                                                                   |
   |                 |                 |                                                                                           |    -  **true**: A check request will be sent and the IP address group will not be created. Check items include mandatory parameters, request format, and constraints. If the check fails, the system returns an error. If the check succeeds, response code 202 will be returned. |
   |                 |                 |                                                                                           |                                                                                                                                                                                                                                                                                   |
   |                 |                 |                                                                                           |    -  **false** (default value): A request will be sent and an IP address group will be created.                                                                                                                                                                                  |
   +-----------------+-----------------+-------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | address_group   | Yes             | :ref:`CreateAddressGroupOption <vpc_apiv3_0022__request_createaddressgroupoption>` object | Request body for creating an IP address group.                                                                                                                                                                                                                                    |
   +-----------------+-----------------+-------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0022__request_createaddressgroupoption:

.. table:: **Table 3** CreateAddressGroupOption

   +-----------------+-----------------+-------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                | Description                                                                                                                                  |
   +=================+=================+=====================================================================================+==============================================================================================================================================+
   | name            | Yes             | String                                                                              | -  IP address group name.                                                                                                                    |
   |                 |                 |                                                                                     |                                                                                                                                              |
   |                 |                 |                                                                                     | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                       |
   +-----------------+-----------------+-------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String                                                                              | -  Description about the IP address group.                                                                                                   |
   |                 |                 |                                                                                     |                                                                                                                                              |
   |                 |                 |                                                                                     | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                             |
   +-----------------+-----------------+-------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_version      | Yes             | Integer                                                                             | -  Whether it is an IPv4 or IPv6 address group.                                                                                              |
   |                 |                 |                                                                                     |                                                                                                                                              |
   |                 |                 |                                                                                     | -  The value can be:                                                                                                                         |
   |                 |                 |                                                                                     |                                                                                                                                              |
   |                 |                 |                                                                                     |    -  **4**, IPv4 address groups.                                                                                                            |
   |                 |                 |                                                                                     |                                                                                                                                              |
   |                 |                 |                                                                                     |    -  **6**, IPv6 address groups.                                                                                                            |
   +-----------------+-----------------+-------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_set          | No              | Array of strings                                                                    | -  IP address sets in an IP address group.                                                                                                   |
   |                 |                 |                                                                                     |                                                                                                                                              |
   |                 |                 |                                                                                     | -  The value can be a single IP address, IP address range, or CIDR block.                                                                    |
   |                 |                 |                                                                                     |                                                                                                                                              |
   |                 |                 |                                                                                     | -  The default maximum number of IP address sets, including IP addresses, IP address ranges, and CIDR blocks, in an IP address group, is 20. |
   +-----------------+-----------------+-------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_extra_set    | No              | Array of :ref:`IpExtraSetOption <vpc_apiv3_0022__request_ipextrasetoption>` objects | -  IP addresses and their remarks in an IP address group.                                                                                    |
   |                 |                 |                                                                                     |                                                                                                                                              |
   |                 |                 |                                                                                     | -  The default quota is 20. Either this parameter or **ip_set** must be specified.                                                           |
   +-----------------+-----------------+-------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0022__request_ipextrasetoption:

.. table:: **Table 4** IpExtraSetOption

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                      |
   +=================+=================+=================+==================================================================================================+
   | ip              | Yes             | String          | -  An IP address, IP address range, or CIDR block. Both IPv4 and IPv6 are supported.             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
   | remarks         | No              | String          | -  Supplementary information about the IP address, IP address range, or CIDR block.              |
   |                 |                 |                 |                                                                                                  |
   |                 |                 |                 | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 5** Response body parameters

   +---------------+--------------------------------------------------------------------+-------------------------------------------------+
   | Parameter     | Type                                                               | Description                                     |
   +===============+====================================================================+=================================================+
   | request_id    | String                                                             | Request ID.                                     |
   +---------------+--------------------------------------------------------------------+-------------------------------------------------+
   | address_group | :ref:`AddressGroup <vpc_apiv3_0022__response_addressgroup>` object | Response body for creating an IP address group. |
   +---------------+--------------------------------------------------------------------+-------------------------------------------------+

.. _vpc_apiv3_0022__response_addressgroup:

.. table:: **Table 6** AddressGroup

   +-----------------------+----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                         | Description                                                                                                                                  |
   +=======================+==============================================================================================+==============================================================================================================================================+
   | id                    | String                                                                                       | -  IP address group ID that uniquely identifies the IP address group.                                                                        |
   |                       |                                                                                              |                                                                                                                                              |
   |                       |                                                                                              | -  The value is a string in UUID format.                                                                                                     |
   +-----------------------+----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                                       | -  IP address group name.                                                                                                                    |
   |                       |                                                                                              |                                                                                                                                              |
   |                       |                                                                                              | -  The value can contain no more than 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).               |
   +-----------------------+----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                                       | -  Description about the IP address group.                                                                                                   |
   |                       |                                                                                              |                                                                                                                                              |
   |                       |                                                                                              | -  The value can contain no more than 255 characters.                                                                                        |
   |                       |                                                                                              |                                                                                                                                              |
   |                       |                                                                                              | -  The value cannot contain angle brackets (< or >).                                                                                         |
   +-----------------------+----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_set                | Array of strings                                                                             | -  IP address sets in an IP address group.                                                                                                   |
   |                       |                                                                                              |                                                                                                                                              |
   |                       |                                                                                              | -  The value can be a single IP address, IP address range, or CIDR block.                                                                    |
   |                       |                                                                                              |                                                                                                                                              |
   |                       |                                                                                              | -  The default maximum number of IP address sets, including IP addresses, IP address ranges, and CIDR blocks, in an IP address group, is 20. |
   +-----------------------+----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_version            | Integer                                                                                      | -  Whether it is an IPv4 or IPv6 address group.                                                                                              |
   |                       |                                                                                              |                                                                                                                                              |
   |                       |                                                                                              | -  The value can be one of the following:                                                                                                    |
   |                       |                                                                                              |                                                                                                                                              |
   |                       |                                                                                              |    -  **4** (IPv4 address groups).                                                                                                           |
   |                       |                                                                                              |                                                                                                                                              |
   |                       |                                                                                              |    -  **6** (IPv6 address groups).                                                                                                           |
   +-----------------------+----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                                       | -  Time when the IP address group was created.                                                                                               |
   |                       |                                                                                              |                                                                                                                                              |
   |                       |                                                                                              | -  The value is a UTC time in the format of *yyyy-MM-ddTHH:mm:ss*, which is automatically generated by the system.                           |
   +-----------------------+----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                                       | -  Time when the IP address group was last updated.                                                                                          |
   |                       |                                                                                              |                                                                                                                                              |
   |                       |                                                                                              | -  The value is a UTC time in the format of *yyyy-MM-ddTHH:mm:ss*, which is automatically generated by the system.                           |
   +-----------------------+----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                                                                                       | -  ID of the project where the IP address group is used.                                                                                     |
   +-----------------------+----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_extra_set          | Array of :ref:`IpExtraSetRespOption <vpc_apiv3_0022__response_ipextrasetrespoption>` objects | -  IP address sets and their remarks in an IP address group.                                                                                 |
   +-----------------------+----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 7** ResponseTag

   +-----------------------+-----------------------+----------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                      |
   +=======================+=======================+==================================================================================+
   | key                   | String                | -  Definition: Tag key.                                                          |
   |                       |                       |                                                                                  |
   |                       |                       | -  Range:                                                                        |
   |                       |                       |                                                                                  |
   |                       |                       |    -  Each key can contain up to 36 Unicode characters and cannot be left blank. |
   |                       |                       |                                                                                  |
   |                       |                       |    -  Each key value of a resource must be unique.                               |
   |                       |                       |                                                                                  |
   |                       |                       |    -  The value can contain:                                                     |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Letters                                                                 |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Digits                                                                  |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Special characters: underscores (_) ,at signs (@), and hyphens (-)      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------+
   | value                 | String                | -  Definition: Tag value.                                                        |
   |                       |                       |                                                                                  |
   |                       |                       | -  Range:                                                                        |
   |                       |                       |                                                                                  |
   |                       |                       |    -  Each value can contain up to 43 Unicode characters and can be left blank.  |
   |                       |                       |                                                                                  |
   |                       |                       |    -  The value can contain:                                                     |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Letters                                                                 |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Digits                                                                  |
   |                       |                       |                                                                                  |
   |                       |                       |       -  Special characters: underscore (_), at signs (@), and hyphen (-)        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------+

.. _vpc_apiv3_0022__response_ipextrasetrespoption:

.. table:: **Table 8** IpExtraSetRespOption

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                      |
   +=======================+=======================+==================================================================================================+
   | ip                    | String                | -  An IP address, IP address range, or CIDR block. Both IPv4 and IPv6 are supported.             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | remarks               | String                | -  Supplementary information about the IP address, IP address range, or CIDR block.              |
   |                       |                       |                                                                                                  |
   |                       |                       | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >). |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

Example Requests
----------------

Create an IP address group named **AutoTester746010.580123789**, set the IP version to IPv4, and specify the IP set as 192.168.3.2, 192.168.3.40, 192.168.3.20-192.168.3.100, and 192.168.5.0/24.

.. code-block:: text

   POST https://{{endpoint}}/v3/b2782e6708b8475c993e6064bc456bf8/vpc/address-groups

   {
     "address_group" : {
       "ip_version" : 4,
       "name" : "AutoTester746010.580123789",
       "ip_set" : [ "192.168.3.2", "192.168.3.40", "192.168.3.20-192.168.3.100", "192.168.5.0/24" ],
       "description" : "test",
       "enterprise_project_id" : "0aad99bc-f5f6-4f78-8404-c598d76b0ed2",
       "max_capacity" : 20
     }
   }

Example Responses
-----------------

**Status code: 201**

Normal response to the POST operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

.. code-block::

   {
     "address_group" : {
       "id" : "dd18a501-fcd5-4adc-acfe-b0e2384baf08",
       "name" : "AutoTester746010.580123789",
       "tenant_id" : "b2782e6708b8475c993e6064bc456bf8",
       "ip_version" : 4,
       "max_capacity" : 20,
       "ip_set" : [ "192.168.5.0/24", "192.168.3.20-192.168.3.100", "192.168.3.40", "192.168.3.2" ],
       "ip_extra_set" : [ {
         "ip" : "192.168.5.0/24",
         "remarks" : null
       }, {
         "ip" : "192.168.3.20-192.168.3.100",
         "remarks" : null
       }, {
         "ip" : "192.168.3.40",
         "remarks" : null
       }, {
         "ip" : "192.168.3.2",
         "remarks" : null
       } ],
       "enterprise_project_id" : "0aad99bc-f5f6-4f78-8404-c598d76b0ed2",
       "created_at" : "2019-06-28T02:06:38.000+00:00",
       "updated_at" : "2019-06-28T02:06:38.000+00:00",
       "description" : "test",
       "status" : "NORMAL",
       "status_message" : "",
       "tags" : [ ]
     },
     "request_id" : "f568db7a-2675-4271-8747-3e3f1c6381ba"
   }

Status Codes
------------

+-------------+-------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                           |
+=============+=======================================================================================================+
| 201         | Normal response to the POST operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`. |
+-------------+-------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
