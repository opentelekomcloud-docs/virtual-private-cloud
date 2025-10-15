:original_name: vpc_apiv3_0011.html

.. _vpc_apiv3_0011:

Querying Security Groups
========================

Function
--------

After a security group is created, you can call this API to query all information about the security group, including the name, ID, and description.

Constraints
-----------

You can query all security groups under your account. A maximum of 2,000 records can be returned for each query. If the number of records exceeds 2,000, the pagination marker will be returned.

URI
---

GET /v3/{project_id}/vpc/security-groups

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                        |
   +=================+=================+=================+====================================================================+
   | project_id      | Yes             | String          | -  Definition: ID of the project that a security group belongs to. |
   |                 |                 |                 |                                                                    |
   |                 |                 |                 | -  Range: None                                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type             | Description                                                                                                                                                               |
   +=======================+=================+==================+===========================================================================================================================================================================+
   | limit                 | No              | Integer          | -  Definition: Number of resources returned on each page.                                                                                                                 |
   |                       |                 |                  |                                                                                                                                                                           |
   |                       |                 |                  | -  Range: 0-2000                                                                                                                                                          |
   +-----------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker                | No              | String           | -  Definition: ID of the resource from which the pagination query starts. If the parameter is left blank, only resources on the first page are queried.                   |
   |                       |                 |                  |                                                                                                                                                                           |
   |                       |                 |                  | -  Range: Security group ID.                                                                                                                                              |
   +-----------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | No              | Array of strings | -  Definition: ID of a security group. This field can be used to precisely filter security groups. Multiple IDs can be specified for filtering.                           |
   |                       |                 |                  |                                                                                                                                                                           |
   |                       |                 |                  | -  Range: None                                                                                                                                                            |
   +-----------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | No              | Array of strings | -  Definition: Name of a security group. This field can be used to precisely filter security groups. Multiple names can be specified for filtering.                       |
   |                       |                 |                  |                                                                                                                                                                           |
   |                       |                 |                  | -  Range: None                                                                                                                                                            |
   +-----------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | No              | Array of strings | -  Definition: Description of a security group. This field can be used to precisely filter security groups. Multiple descriptions can be specified for filtering.         |
   |                       |                 |                  |                                                                                                                                                                           |
   |                       |                 |                  | -  Range: None                                                                                                                                                            |
   +-----------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | String           | -  Definition: ID of the enterprise project that a security group belongs to. This field can be used to filter the security groups associated with an enterprise project. |
   |                       |                 |                  |                                                                                                                                                                           |
   |                       |                 |                  | -  Range:                                                                                                                                                                 |
   |                       |                 |                  |                                                                                                                                                                           |
   |                       |                 |                  |    -  The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). **0** indicates the default enterprise project.            |
   |                       |                 |                  |                                                                                                                                                                           |
   |                       |                 |                  |    -  To obtain the security groups associated with all enterprise projects that a user has permissions to view, specify **all_granted_eps**.                             |
   +-----------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | No              | Array of strings | -  Definition: ID of the project that a security group belongs to.                                                                                                        |
   |                       |                 |                  |                                                                                                                                                                           |
   |                       |                 |                  | -  Range: None                                                                                                                                                            |
   +-----------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+--------------------------------------------------------------------------------+------------------------------------------------------------+
   | Parameter             | Type                                                                           | Description                                                |
   +=======================+================================================================================+============================================================+
   | security_groups       | Array of :ref:`SecurityGroup <vpc_apiv3_0011__response_securitygroup>` objects | -  Definition: Response body for querying security groups. |
   |                       |                                                                                |                                                            |
   |                       |                                                                                | -  Range: None                                             |
   +-----------------------+--------------------------------------------------------------------------------+------------------------------------------------------------+
   | request_id            | String                                                                         | -  Definition: Request ID.                                 |
   |                       |                                                                                |                                                            |
   |                       |                                                                                | -  Range: None                                             |
   +-----------------------+--------------------------------------------------------------------------------+------------------------------------------------------------+
   | page_info             | :ref:`PageInfo <vpc_apiv3_0011__response_pageinfo>` object                     | -  Definition: Pagination information.                     |
   |                       |                                                                                |                                                            |
   |                       |                                                                                | -  Range: None                                             |
   +-----------------------+--------------------------------------------------------------------------------+------------------------------------------------------------+

.. _vpc_apiv3_0011__response_securitygroup:

.. table:: **Table 4** SecurityGroup

   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                       | Description                                                                                                                                                         |
   +=======================+============================================================================+=====================================================================================================================================================================+
   | id                    | String                                                                     | -  Definition: ID of a security group. After a security group is created, a security group ID is generated, which uniquely identifies the security group.           |
   |                       |                                                                            |                                                                                                                                                                     |
   |                       |                                                                            | -  Range: The value is in UUID format with hyphens (-).                                                                                                             |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                     | -  Definition: Name of a security group.                                                                                                                            |
   |                       |                                                                            |                                                                                                                                                                     |
   |                       |                                                                            | -  Range: The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                       |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                     | -  Definition: Description of a security group.                                                                                                                     |
   |                       |                                                                            |                                                                                                                                                                     |
   |                       |                                                                            | -  Range: The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                                             |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                                     | -  Definition: ID of the project that a security group belongs to.                                                                                                  |
   |                       |                                                                            |                                                                                                                                                                     |
   |                       |                                                                            | -  Range: None                                                                                                                                                      |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                     | -  Definition: Time when a security group was created.                                                                                                              |
   |                       |                                                                            |                                                                                                                                                                     |
   |                       |                                                                            | -  Range: UTC time in the format of yyyy-MM-ddTHH:mm:ssZ                                                                                                            |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                     | -  Definition: Time when a security group was updated.                                                                                                              |
   |                       |                                                                            |                                                                                                                                                                     |
   |                       |                                                                            | -  Range: UTC time in the format of yyyy-MM-ddTHH:mm:ssZ                                                                                                            |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | String                                                                     | -  Definition: ID of the enterprise project that a security group belongs to.                                                                                       |
   |                       |                                                                            |                                                                                                                                                                     |
   |                       |                                                                            | -  Range: The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). **0** indicates the default enterprise project.  |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Array of :ref:`ResponseTag <vpc_apiv3_0011__response_responsetag>` objects | -  Definition: Tags of a security group, including tag keys and tag values, which can be used to classify and identify resources. For details, see the tag objects. |
   |                       |                                                                            |                                                                                                                                                                     |
   |                       |                                                                            | -  Range: None                                                                                                                                                      |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_apiv3_0011__response_responsetag:

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

.. _vpc_apiv3_0011__response_pageinfo:

.. table:: **Table 6** PageInfo

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

Querying security groups

.. code-block:: text

   GET https://{Endpoint}/v3/{project_id}/vpc/security-groups

Example Responses
-----------------

**Status code: 200**

Normal response to the GET operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

.. code-block::

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
