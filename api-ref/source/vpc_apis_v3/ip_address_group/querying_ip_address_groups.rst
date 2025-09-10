:original_name: vpc_apiv3_0023.html

.. _vpc_apiv3_0023:

Querying IP Address Groups
==========================

Function
--------

This API is used to query IP address groups based on filter criteria.

URI
---

GET /v3/{project_id}/vpc/address-groups

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                              |
   +=================+=================+==================+==========================================================================================================================================================+
   | limit           | No              | Integer          | -  Number of records returned on each page.                                                                                                              |
   |                 |                 |                  |                                                                                                                                                          |
   |                 |                 |                  | -  Value range: 0 to 2000.                                                                                                                               |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String           | Start resource ID of pagination query. If the parameter is left blank, only resources on the first page are queried.                                     |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id              | No              | Array of strings | Unique ID of an IP address group, which is used to filter the IP address group. Multiple IDs can be specified for filtering.                             |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | Array of strings | IP address group name, which is used to filter the IP address group. Multiple names can be specified for filtering.                                      |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_version      | No              | Integer          | -  IP address version, which is used to filter the IP address group.                                                                                     |
   |                 |                 |                  |                                                                                                                                                          |
   |                 |                 |                  | -  Value range: **4**, **6**.                                                                                                                            |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | Array of strings | Supplementary information about an IP address group, which is used to filter the IP address group. Multiple descriptions can be specified for filtering. |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +----------------+------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter      | Type                                                                         | Description                                   |
   +================+==============================================================================+===============================================+
   | request_id     | String                                                                       | Request ID.                                   |
   +----------------+------------------------------------------------------------------------------+-----------------------------------------------+
   | address_groups | Array of :ref:`AddressGroup <vpc_apiv3_0023__response_addressgroup>` objects | Response body for querying IP address groups. |
   +----------------+------------------------------------------------------------------------------+-----------------------------------------------+
   | page_info      | :ref:`PageInfo <vpc_apiv3_0023__response_pageinfo>` object                   | Pagination information.                       |
   +----------------+------------------------------------------------------------------------------+-----------------------------------------------+

.. _vpc_apiv3_0023__response_addressgroup:

.. table:: **Table 4** AddressGroup

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
   | ip_extra_set          | Array of :ref:`IpExtraSetRespOption <vpc_apiv3_0023__response_ipextrasetrespoption>` objects | -  IP address sets and their remarks in an IP address group.                                                                                 |
   +-----------------------+----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 5** ResponseTag

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

.. _vpc_apiv3_0023__response_ipextrasetrespoption:

.. table:: **Table 6** IpExtraSetRespOption

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                      |
   +=======================+=======================+==================================================================================================+
   | ip                    | String                | -  An IP address, IP address range, or CIDR block. Both IPv4 and IPv6 are supported.             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | remarks               | String                | -  Supplementary information about the IP address, IP address range, or CIDR block.              |
   |                       |                       |                                                                                                  |
   |                       |                       | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >). |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0023__response_pageinfo:

.. table:: **Table 7** PageInfo

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                   |
   +=======================+=======================+===============================================================================================================================+
   | previous_marker       | String                | -  Definition: The first record on the current page.                                                                          |
   |                       |                       |                                                                                                                               |
   |                       |                       | -  Range: None                                                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | current_count         | Integer               | -  Definition: Total number of records on the current page.                                                                   |
   |                       |                       |                                                                                                                               |
   |                       |                       | -  Range: None                                                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | next_marker           | String                | -  Definition: The last record on the current page. The parameter **next_marker** does not exist if the page is the last one. |
   |                       |                       |                                                                                                                               |
   |                       |                       | -  Range: None                                                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Query address groups based on combined filter criteria.

.. code-block:: text

   GET https://{{endpoint}}/v3/b2782e6708b8475c993e6064bc456bf8/vpc/address-groups?name=vkvgykvsvhjaaaa1&description=xxxxxxxxxx&ip_version=4

Example Responses
-----------------

**Status code: 200**

Normal response to the GET operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

.. code-block::

   {
     "address_groups" : [ {
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
     } ],
     "page_info" : {
       "previous_marker" : "dd18a501-fcd5-4adc-acfe-b0e2384baf08",
       "current_count" : 1
     },
     "request_id" : "e51fa17c-3259-4122-afb1-9c03d4ef5408"
   }

Status Codes
------------

+-------------+------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                          |
+=============+======================================================================================================+
| 200         | Normal response to the GET operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`. |
+-------------+------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
