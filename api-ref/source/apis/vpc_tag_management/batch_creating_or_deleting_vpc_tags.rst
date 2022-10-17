:original_name: vpc_tag_0004.html

.. _vpc_tag_0004:

Batch Creating or Deleting VPC Tags
===================================

Function
--------

This API is used to add multiple tags to or delete multiple tags from a VPC at a time.

This API is idempotent.

If there are duplicate keys in the request body when you add tags, an error is reported.

During tag creation, duplicate keys are not allowed. If a key already exists in the database, its value will be overwritten by the new duplicate key.

During tag deletion, if some tags do not exist, the operation is considered to be successful by default. The character set of the tags will not be checked. When you delete tags, the tag structure cannot be missing, and the key cannot be left blank or be an empty string.

URI
---

POST /v2.0/{project_id}/vpcs/{vpc_id}/tags/action

:ref:`Table 1 <vpc_tag_0004__table27380479>` describes the parameters.

.. _vpc_tag_0004__table27380479:

.. table:: **Table 1** Parameter description

   +------------+-----------+----------------------------------------------------------+
   | Name       | Mandatory | Description                                              |
   +============+===========+==========================================================+
   | project_id | Yes       | Specifies the project ID.                                |
   +------------+-----------+----------------------------------------------------------+
   | vpc_id     | Yes       | Specifies the VPC ID, which uniquely identifies the VPC. |
   +------------+-----------+----------------------------------------------------------+

Request Message
---------------

Request parameter

.. table:: **Table 2** Request parameter

   +-----------------+---------------------------------------------------------------+-----------------+---------------------------------------------------------------------------------------------------+
   | Parameter       | Type                                                          | Mandatory       | Description                                                                                       |
   +=================+===============================================================+=================+===================================================================================================+
   | tags            | Array of :ref:`tag <vpc_tag_0004__table244913515593>` objects | Yes             | Specifies the **tag** objects. For details, see :ref:`Table 3 <vpc_tag_0004__table244913515593>`. |
   +-----------------+---------------------------------------------------------------+-----------------+---------------------------------------------------------------------------------------------------+
   | action          | String                                                        | Yes             | Specifies the operation. Possible values are as follows:                                          |
   |                 |                                                               |                 |                                                                                                   |
   |                 |                                                               |                 | -  **create**                                                                                     |
   |                 |                                                               |                 | -  **delete**                                                                                     |
   +-----------------+---------------------------------------------------------------+-----------------+---------------------------------------------------------------------------------------------------+

.. _vpc_tag_0004__table244913515593:

.. table:: **Table 3** **tag** objects

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | Attribute       | Type            | Mandatory       | Description                                                         |
   +=================+=================+=================+=====================================================================+
   | key             | String          | Yes             | -  Specifies the tag key.                                           |
   |                 |                 |                 | -  Cannot be left blank.                                            |
   |                 |                 |                 | -  Can contain a maximum of 36 characters.                          |
   |                 |                 |                 | -  Can contain only the following character types:                  |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 |    -  Uppercase letters                                             |
   |                 |                 |                 |    -  Lowercase letters                                             |
   |                 |                 |                 |    -  Digits                                                        |
   |                 |                 |                 |    -  Special characters, including hyphens (-) and underscores (_) |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | -  The tag key of a VPC must be unique.                             |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | value           | String          | Yes             | -  Specifies the tag value.                                         |
   |                 |                 |                 | -  Can contain a maximum of 43 characters.                          |
   |                 |                 |                 | -  Can contain only the following character types:                  |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 |    -  Uppercase letters                                             |
   |                 |                 |                 |    -  Lowercase letters                                             |
   |                 |                 |                 |    -  Digits                                                        |
   |                 |                 |                 |    -  Special characters, including hyphens (-) and underscores (_) |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+

Request example 1: Creating tags in batches

.. code-block:: text

   POST https://{Endpoint}/v2.0/{project_id}/vpcs/{vpc_id}/tags/action

   {
       "action": "create",
       "tags": [
           {
               "key": "key1",
               "value": "value1"
           },
           {
               "key": "key2",
               "value": "value3"
           }
       ]
   }

Request example 2: Deleting tags in batches

.. code-block:: text

   POST https://{Endpoint}/v2.0/{project_id}/vpcs/{vpc_id}/tags/action

   {
       "action": "delete",
       "tags": [
           {
               "key": "key1",
               "value": "value1"
           },
           {
               "key": "key2",
               "value": "value3"
           }
       ]
   }

Response Message
----------------

Response parameter

None

Example response

None

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
