:original_name: CreateFirewallTag.html

.. _CreateFirewallTag:

Adding a Tag to a Network ACL
=============================

Function
--------

This API is used to add a tag to a specific network ACL. This is an idempotent API. If the new tag has the same key as an existing tag, the tag will be created and overwrite the existing one.

URI
---

POST /v3/{project_id}/firewalls/{firewall_id}/tags

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

.. table:: **Table 2** Request body parameters

   +-----------+-----------+--------------------------------------------------------------------+------------------------------------------------+
   | Parameter | Mandatory | Type                                                               | Description                                    |
   +===========+===========+====================================================================+================================================+
   | tag       | Yes       | :ref:`ResourceTag <createfirewalltag__request_resourcetag>` object | Request body for adding tags to a network ACL. |
   +-----------+-----------+--------------------------------------------------------------------+------------------------------------------------+

.. _createfirewalltag__request_resourcetag:

.. table:: **Table 3** ResourceTag

   +-----------------+-----------------+-----------------+------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                          |
   +=================+=================+=================+======================================================+
   | key             | Yes             | String          | -  Tag key                                           |
   |                 |                 |                 |                                                      |
   |                 |                 |                 | -  Tag keys must be unique for each resource.        |
   |                 |                 |                 |                                                      |
   |                 |                 |                 | -  The value can contain 1 to 128 characters.        |
   +-----------------+-----------------+-----------------+------------------------------------------------------+
   | value           | Yes             | String          | -  Tag value.                                        |
   |                 |                 |                 |                                                      |
   |                 |                 |                 | -  The value can contain no more than 255 characters |
   +-----------------+-----------------+-----------------+------------------------------------------------------+

Response Parameters
-------------------

**Status code: 204**

Normal request response. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

None

Example Requests
----------------

Add a tag to a network ACL. Set the tag key to **key4** and tag value to **value4**.

.. code-block:: text

   POST https://{Endpoint}/v3/{project_id}/firewalls/{firewall_id}/tags

   {
     "tag" : {
       "key" : "key4",
       "value" : "value4"
     }
   }

Example Responses
-----------------

None

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------+
| Status Code | Description                                                                             |
+=============+=========================================================================================+
| 204         | Normal request response. For more status codes, see :ref:`Status Codes <vpc_api_0002>`. |
+-------------+-----------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <vpc_api_0003>`.
