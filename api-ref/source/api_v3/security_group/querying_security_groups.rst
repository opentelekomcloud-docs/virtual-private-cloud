:original_name: vpc_apiv3_0011.html

.. _vpc_apiv3_0011:

Querying Security Groups
========================

Function
--------

This API is used to query all security groups of a tenant.

Constraints
-----------

You can query all security groups under your account. A maximum of 2,000 records can be returned for each query. If the number of records exceeds 2,000, the pagination marker will be returned.

URI
---

GET /v3/{project_id}/vpc/security-groups

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type             | Description                                                                                                                                                          |
   +=======================+=================+==================+======================================================================================================================================================================+
   | limit                 | No              | Integer          | -  Number of records returned on each page.                                                                                                                          |
   |                       |                 |                  |                                                                                                                                                                      |
   |                       |                 |                  | -  Value range: 0 to 2000                                                                                                                                            |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker                | No              | String           | Start resource ID of pagination query. If the parameter is left blank, only resources on the first page are queried.                                                 |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | No              | Array of strings | -  Security group ID. This field can be used to filter security groups. Multiple IDs can be specified for filtering.                                                 |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | No              | Array of strings | -  Security group name. This field can be used to filter security groups. Multiple names can be specified for filtering.                                             |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | No              | Array of strings | -  Supplementary information about the security group. This field can be used to filter security groups. Multiple descriptions can be specified for filtering.       |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | Array of strings | -  Enterprise project ID. This field can be used to filter the security groups associated with an enterprise project.                                                |
   |                       |                 |                  |                                                                                                                                                                      |
   |                       |                 |                  | -  The project ID can be **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). **0** indicates the default enterprise project. |
   |                       |                 |                  |                                                                                                                                                                      |
   |                       |                 |                  | -  To obtain the security groups associated with all enterprise projects, specify **all_granted_eps**.                                                               |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | No              | Array of strings | Project ID.                                                                                                                                                          |
   +-----------------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------+--------------------------------------------------------------------------------+---------------------------------------------+
   | Parameter       | Type                                                                           | Description                                 |
   +=================+================================================================================+=============================================+
   | security_groups | Array of :ref:`SecurityGroup <vpc_apiv3_0011__response_securitygroup>` objects | Response body for querying security groups. |
   +-----------------+--------------------------------------------------------------------------------+---------------------------------------------+
   | request_id      | String                                                                         | Request ID.                                 |
   +-----------------+--------------------------------------------------------------------------------+---------------------------------------------+
   | page_info       | :ref:`PageInfo <vpc_apiv3_0011__response_pageinfo>` object                     | Pagination information.                     |
   +-----------------+--------------------------------------------------------------------------------+---------------------------------------------+

.. _vpc_apiv3_0011__response_securitygroup:

.. table:: **Table 4** SecurityGroup

   +-----------------------+------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                       | Description                                                                                                                                                          |
   +=======================+============================================================+======================================================================================================================================================================+
   | id                    | String                                                     | -  Security group ID, which uniquely identifies the security group.                                                                                                  |
   |                       |                                                            |                                                                                                                                                                      |
   |                       |                                                            | -  The value is in UUID format with hyphens (-).                                                                                                                     |
   +-----------------------+------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                     | -  Security group name.                                                                                                                                              |
   |                       |                                                            |                                                                                                                                                                      |
   |                       |                                                            | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                               |
   +-----------------------+------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                     | -  Description about the security group.                                                                                                                             |
   |                       |                                                            |                                                                                                                                                                      |
   |                       |                                                            | -  The value can contain up to 255 characters and cannot contain angle brackets (< or >).                                                                            |
   +-----------------------+------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                     | -  ID of the project to which the security group belongs.                                                                                                            |
   +-----------------------+------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                     | -  Time when the security group was created.                                                                                                                         |
   |                       |                                                            |                                                                                                                                                                      |
   |                       |                                                            | -  The value is a UTC time in the format of *yyyy-MM-ddTHH:mm:ssZ*.                                                                                                  |
   +-----------------------+------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                     | -  Time when the security group was updated.                                                                                                                         |
   |                       |                                                            |                                                                                                                                                                      |
   |                       |                                                            | -  The value is a UTC time in the format of *yyyy-MM-ddTHH:mm:ssZ*.                                                                                                  |
   +-----------------------+------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | String                                                     | -  ID of the enterprise project to which the security group belongs.                                                                                                 |
   |                       |                                                            |                                                                                                                                                                      |
   |                       |                                                            | -  The project ID can be **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). **0** indicates the default enterprise project. |
   +-----------------------+------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Array of :ref:`Tag <vpc_apiv3_0011__response_tag>` objects | -  Security group tags. For details, see the tag objects.                                                                                                            |
   |                       |                                                            |                                                                                                                                                                      |
   |                       |                                                            | -  Value range: 0 to 20 key-value pairs.                                                                                                                             |
   +-----------------------+------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0011__response_tag:

.. table:: **Table 5** Tag

   +-----------------------+-----------------------+----------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                      |
   +=======================+=======================+==================================================================================+
   | key                   | String                | -  Tag key.                                                                      |
   |                       |                       |                                                                                  |
   |                       |                       | -  Value ranges:                                                                 |
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
   | value                 | String                | -  Tag value.                                                                    |
   |                       |                       |                                                                                  |
   |                       |                       | -  Value range:                                                                  |
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

.. _vpc_apiv3_0011__response_pageinfo:

.. table:: **Table 6** PageInfo

   +-----------------+---------+---------------------------------------------------------------------------------------------+
   | Parameter       | Type    | Description                                                                                 |
   +=================+=========+=============================================================================================+
   | previous_marker | String  | First record on the current page.                                                           |
   +-----------------+---------+---------------------------------------------------------------------------------------------+
   | current_count   | Integer | Total number of records on the current page.                                                |
   +-----------------+---------+---------------------------------------------------------------------------------------------+
   | next_marker     | String  | Last record on the current page. This parameter does not exist if the page is the last one. |
   +-----------------+---------+---------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying security groups.

.. code-block:: text

   GET https://{Endpoint}/v3/{project_id}/vpc/security-groups

Example Responses
-----------------

**Status code: 200**

Normal response to the GET operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

-  .. code-block::

      {
        "request_id" : "d31cb32ca06f3c1a294fa24e6cbc5a56",
        "security_groups" : [ {
          "id" : "0552091e-b83a-49dd-88a7-4a5c86fd9ec3",
          "name" : "sg-test",
          "project_id" : "060576782980d5762f9ec014dd2f1148",
          "description" : "test",
          "enterprise_project_id" : 0,
          "created_at" : "2019-10-16T11:11:14.000+00:00",
          "updated_at" : "2020-03-25T10:53:46.000+00:00",
          "tags" : [ ]
        }, {
          "id" : "0b8cb773-197c-4c91-94f1-e051f0563e5a",
          "name" : "test-sg",
          "project_id" : "060576782980d5762f9ec014dd2f1148",
          "description" : "The security group is for general-purpose web servers and includes default rules that allow all inbound ICMP traffic and allow inbound traffic on ports 22, 3389, 80, and 443. This security group is suitable for ECSs that require remote login, public network ping, and website services.",
          "enterprise_project_id" : 0,
          "created_at" : "2019-12-03T09:02:11.000+00:00",
          "updated_at" : "2019-12-03T09:02:11.000+00:00",
          "tags" : [ ]
        } ],
        "page_info" : {
          "previous_marker" : "0552091e-b83a-49dd-88a7-4a5c86fd9ec3",
          "current_count" : 2
        }
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
