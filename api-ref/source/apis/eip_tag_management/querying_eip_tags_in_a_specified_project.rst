:original_name: eip_tag_0006.html

.. _eip_tag_0006:

Querying EIP Tags in a Specified Project
========================================

Function
--------

This API is used to query all EIP tags of a tenant in a specified region.

URI
---

GET /v2.0/{project_id}/publicips/tags

:ref:`Table 1 <eip_tag_0006__table27380479>` describes the parameters.

.. _eip_tag_0006__table27380479:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Name       Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request Message
---------------

-  Request parameter

   None

-  Example request

   .. code-block:: text

      GET /v2.0/{project_id}/publicips/tags

Response Message
----------------

-  Response parameter

   .. table:: **Table 2** Response parameter

      +-----------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
      | Parameter | Type                                                          | Description                                                                                           |
      +===========+===============================================================+=======================================================================================================+
      | tags      | Array of :ref:`tag <eip_tag_0006__table043062842515>` objects | Specifies the **tag** object list. For details, see :ref:`Table 3 <eip_tag_0006__table043062842515>`. |
      +-----------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

   .. _eip_tag_0006__table043062842515:

   .. table:: **Table 3** Description of the **tag** field

      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                         |
      +=======================+=======================+=====================================================================+
      | key                   | String                | Specifies the tag key.                                              |
      |                       |                       |                                                                     |
      |                       |                       | -  Cannot be left blank.                                            |
      |                       |                       | -  Can contain a maximum of 36 characters.                          |
      |                       |                       | -  Can contain only the following character types:                  |
      |                       |                       |                                                                     |
      |                       |                       |    -  Uppercase letters                                             |
      |                       |                       |    -  Lowercase letters                                             |
      |                       |                       |    -  Digits                                                        |
      |                       |                       |    -  Special characters, including hyphens (-) and underscores (_) |
      +-----------------------+-----------------------+---------------------------------------------------------------------+
      | values                | Array of strings      | Specifies the tag value list.                                       |
      |                       |                       |                                                                     |
      |                       |                       | -  Can contain a maximum of 43 characters.                          |
      |                       |                       | -  Can contain only the following character types:                  |
      |                       |                       |                                                                     |
      |                       |                       |    -  Uppercase letters                                             |
      |                       |                       |    -  Lowercase letters                                             |
      |                       |                       |    -  Digits                                                        |
      |                       |                       |    -  Special characters, including hyphens (-) and underscores (_) |
      +-----------------------+-----------------------+---------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "tags": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              },
              {
                  "key": "key2",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ]
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
