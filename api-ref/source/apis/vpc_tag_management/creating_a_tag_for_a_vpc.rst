:original_name: vpc_tag_0001.html

.. _vpc_tag_0001:

Creating a Tag for a VPC
========================

Function
--------

This API is used to create a tag for a VPC.

URI
---

POST /v2.0/{project_id}/vpcs/{vpc_id}/tags

:ref:`Table 1 <vpc_tag_0001__table27380479>` describes the parameters.

.. _vpc_tag_0001__table27380479:

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

-  Request parameter

   .. table:: **Table 2** Request parameter

      +-----------+-------------------------------------------------------+-----------+-----------------------------------------------------------------------------------------------------+
      | Parameter | Type                                                  | Mandatory | Description                                                                                         |
      +===========+=======================================================+===========+=====================================================================================================+
      | tag       | :ref:`tag <vpc_tag_0001__table13242848193719>` object | Yes       | Specifies the **tag** objects. For details, see :ref:`Table 3 <vpc_tag_0001__table13242848193719>`. |
      +-----------+-------------------------------------------------------+-----------+-----------------------------------------------------------------------------------------------------+

   .. _vpc_tag_0001__table13242848193719:

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

-  Example request

   .. code-block:: text

      POST https://{Endpoint}/v2.0/{project_id}/vpcs/{vpc_id}/tags

      {
          "tag": {
              "key": "key1",
              "value": "value1"
          }
      }

Response Message
----------------

-  Response parameter

   None

-  Example response

   None

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
