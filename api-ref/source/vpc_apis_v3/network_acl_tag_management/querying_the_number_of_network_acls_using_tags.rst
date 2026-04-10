:original_name: CountFirewallsByTags.html

.. _CountFirewallsByTags:

Querying the Number of Network ACLs Using Tags
==============================================

Function
--------

This API is used to query the number of network ACLs using tags.

URI
---

POST /v3/{project_id}/firewalls/resource-instances/count

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------+-----------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
   +===========+===========+=========================================================================+=======================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | matches   | No        | Array of :ref:`Match <countfirewallsbytags__request_match>` objects     | The key-value pair to be matched in the query. The key is a fixed dictionary value and must be a unique and supported key. The key can only be **resource_name**.                                                                                                                                                                                                                                                                                                                                                                                     |
   +-----------+-----------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags      | No        | Array of :ref:`ListTag <countfirewallsbytags__request_listtag>` objects | The resources to be queried contain all tags listed in tags. A maximum of 50 tags can be specified. Each tag key can have a maximum of 10 tag values. Each tag value can be an empty array but the structure cannot be missing. Each tag key must be unique, and each tag value of a tag must also be unique. Resources with all tags listed in tags will be returned. Keys in this list are in an AND relationship while values in each key-value structure are in an OR relationship. If **tags** is not specified, all resources will be returned. |
   +-----------+-----------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _countfirewallsbytags__request_match:

.. table:: **Table 3** Match

   +-----------+-----------+--------+------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                            |
   +===========+===========+========+========================================================================+
   | key       | Yes       | String | Tag key. Currently, the tag key can only be the resource name.         |
   +-----------+-----------+--------+------------------------------------------------------------------------+
   | value     | Yes       | String | Tag value. Each value can contain a maximum of 255 Unicode characters. |
   +-----------+-----------+--------+------------------------------------------------------------------------+

.. _countfirewallsbytags__request_listtag:

.. table:: **Table 4** ListTag

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                      |
   +=================+=================+==================+==================================================================================================================================+
   | key             | Yes             | String           | Tag key.                                                                                                                         |
   |                 |                 |                  |                                                                                                                                  |
   |                 |                 |                  | The key cannot be left blank.                                                                                                    |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | values          | Yes             | Array of strings | Tag values. If **values** is left blank, it indicates **any_value** (querying any value). The values are in the OR relationship. |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   =========== ======= =================
   Parameter   Type    Description
   =========== ======= =================
   request_id  String  Request ID
   total_count Integer Resource quantity
   =========== ======= =================

Example Requests
----------------

Query network ACLs using tags and matches.

.. code-block:: text

   POST https://{{Endpoint}}/v3/{project_id}/firewalls/resource-instances/count

   {
     "tags" : [ {
       "key" : "key1",
       "values" : [ "value1" ]
     } ],
     "matches" : [ {
       "key" : "resource_name",
       "value" : "network_aclv3_test"
     } ]
   }

Example Responses
-----------------

**Status code: 200**

Normal request response. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

.. code-block::

   {
     "request_id" : "239df34e-a651-4631-aaa1-d5fef231933a",
     "total_count" : 2
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------+
| Status Code | Description                                                                             |
+=============+=========================================================================================+
| 200         | Normal request response. For more status codes, see :ref:`Status Codes <vpc_api_0002>`. |
+-------------+-----------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
