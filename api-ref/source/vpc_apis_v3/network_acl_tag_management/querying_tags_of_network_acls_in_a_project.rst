:original_name: ListFirewallTags.html

.. _ListFirewallTags:

Querying Tags of Network ACLs in a Project
==========================================

Function
--------

This API is used to query all tags of network ACLs in a specific project.

URI
---

GET /v3/{project_id}/firewalls/tags

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================+
   | limit           | No              | Integer         | Number of records to be queried.                                                                                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | The index position. The query starts from the next piece of data indexed by this parameter.                                          |
   |                 |                 |                 |                                                                                                                                      |
   |                 |                 |                 | The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-------------+----------------------------------------------------------------------+--------------------+
   | Parameter   | Type                                                                 | Description        |
   +=============+======================================================================+====================+
   | tags        | Array of :ref:`ListTag <listfirewalltags__response_listtag>` objects | Tags               |
   +-------------+----------------------------------------------------------------------+--------------------+
   | request_id  | String                                                               | Request ID.        |
   +-------------+----------------------------------------------------------------------+--------------------+
   | total_count | Integer                                                              | Resource quantity. |
   +-------------+----------------------------------------------------------------------+--------------------+

.. _listfirewalltags__response_listtag:

.. table:: **Table 4** ListTag

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                      |
   +=======================+=======================+==================================================================================================================================+
   | key                   | String                | Tag key.                                                                                                                         |
   |                       |                       |                                                                                                                                  |
   |                       |                       | The key cannot be left blank.                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | values                | Array of strings      | Tag values. If **values** is left blank, it indicates **any_value** (querying any value). The values are in the OR relationship. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Query tags of network ACLs by project ID.

.. code-block:: text

   GET https://{Endpoint}/v3/{project_id}/firewalls/tags

Example Responses
-----------------

**Status code: 200**

Normal request response. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

.. code-block::

   {
     "request_id" : "65ae533b-f32c-49df-9b5d-e55eda8f2c25",
     "tags" : [ {
       "key" : "key1",
       "values" : [ "value1", "value2" ]
     }, {
       "key" : "key2",
       "values" : [ "value2" ]
     }, {
       "key" : "key3",
       "values" : [ "value3" ]
     }, {
       "key" : "key4",
       "values" : [ "value4" ]
     }, {
       "key" : "key5",
       "values" : [ "value5" ]
     }, {
       "key" : "keyyyy",
       "values" : [ "value2" ]
     } ]
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
