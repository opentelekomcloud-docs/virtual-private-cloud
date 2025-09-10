:original_name: vpc_apiv3_0024.html

.. _vpc_apiv3_0024:

Querying an IP Address Group
============================

Function
--------

This API is used to query the details of an IP address group.

URI
---

GET /v3/{project_id}/vpc/address-groups/{address_group_id}

.. table:: **Table 1** Path Parameters

   +------------------+-----------+--------+--------------------------------------------------------------------+
   | Parameter        | Mandatory | Type   | Description                                                        |
   +==================+===========+========+====================================================================+
   | address_group_id | Yes       | String | IP address group ID that uniquely identifies the IP address group. |
   +------------------+-----------+--------+--------------------------------------------------------------------+
   | project_id       | Yes       | String | Project ID.                                                        |
   +------------------+-----------+--------+--------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +---------------+--------------------------------------------------------------------+-------------------------------------------------+
   | Parameter     | Type                                                               | Description                                     |
   +===============+====================================================================+=================================================+
   | request_id    | String                                                             | Request ID.                                     |
   +---------------+--------------------------------------------------------------------+-------------------------------------------------+
   | address_group | :ref:`AddressGroup <vpc_apiv3_0024__response_addressgroup>` object | Response body for querying an IP address group. |
   +---------------+--------------------------------------------------------------------+-------------------------------------------------+

.. _vpc_apiv3_0024__response_addressgroup:

.. table:: **Table 3** AddressGroup

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
   | ip_extra_set          | Array of :ref:`IpExtraSetRespOption <vpc_apiv3_0024__response_ipextrasetrespoption>` objects | -  IP address sets and their remarks in an IP address group.                                                                                 |
   +-----------------------+----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** ResponseTag

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

.. _vpc_apiv3_0024__response_ipextrasetrespoption:

.. table:: **Table 5** IpExtraSetRespOption

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

Querying the details of an IP address group

.. code-block:: text

   GET https://{Endpoint}/v3/2bc7a67b35a64a79ad1d3bb8b5f61fc9/vpc/address-groups/dd18a501-fcd5-4adc-acfe-b0e2384baf08

Example Responses
-----------------

**Status code: 200**

Normal response to the GET operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

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
       "description" : "10.10.4.0/23",
       "status" : "NORMAL",
       "status_message" : "",
       "tags" : [ ]
     },
     "request_id" : "ce6c359b-9002-41e5-a0b1-232759bd6637"
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
