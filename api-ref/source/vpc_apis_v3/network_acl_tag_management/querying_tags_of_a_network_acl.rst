:original_name: ShowFirewallTags.html

.. _ShowFirewallTags:

Querying Tags of a Network ACL
==============================

Function
--------

This API is used to query tags of a specific network ACL.

URI
---

GET /v3/{project_id}/firewalls/{firewall_id}/tags

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+---------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                 |
   +=================+=================+=================+=============================================+
   | firewall_id     | Yes             | String          | The unique ID of a network ACL.             |
   |                 |                 |                 |                                             |
   |                 |                 |                 | The value is a string in UUID format.       |
   |                 |                 |                 |                                             |
   |                 |                 |                 | The network ACL with a given ID must exist. |
   +-----------------+-----------------+-----------------+---------------------------------------------+
   | project_id      | Yes             | String          | Project ID                                  |
   +-----------------+-----------------+-----------------+---------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +------------+------------------------------------------------------------------------------+-------------+
   | Parameter  | Type                                                                         | Description |
   +============+==============================================================================+=============+
   | tags       | Array of :ref:`ResourceTag <showfirewalltags__response_resourcetag>` objects | Tags        |
   +------------+------------------------------------------------------------------------------+-------------+
   | request_id | String                                                                       | Request ID  |
   +------------+------------------------------------------------------------------------------+-------------+

.. _showfirewalltags__response_resourcetag:

.. table:: **Table 3** ResourceTag

   +-----------------------+-----------------------+------------------------------------------------------+
   | Parameter             | Type                  | Description                                          |
   +=======================+=======================+======================================================+
   | key                   | String                | -  Tag key                                           |
   |                       |                       |                                                      |
   |                       |                       | -  Tag keys must be unique for each resource.        |
   |                       |                       |                                                      |
   |                       |                       | -  The value can contain 1 to 128 characters.        |
   +-----------------------+-----------------------+------------------------------------------------------+
   | value                 | String                | -  Tag value.                                        |
   |                       |                       |                                                      |
   |                       |                       | -  The value can contain no more than 255 characters |
   +-----------------------+-----------------------+------------------------------------------------------+

Example Requests
----------------

Query tags of a network ACL.

.. code-block:: text

   GET https://{Endpoint}/v3/{project_id}/firewalls/{firewall_id}/tags

Example Responses
-----------------

**Status code: 200**

Normal response to the GET operation

.. code-block::

   {
     "request_id" : "95cedc2b-4b3d-4e5c-af29-74576daf5513",
     "tags" : [ {
       "key" : "key5",
       "value" : "value5"
     }, {
       "key" : "key1",
       "value" : "value1"
     } ]
   }

Status Codes
------------

=========== ====================================
Status Code Description
=========== ====================================
200         Normal response to the GET operation
=========== ====================================

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
