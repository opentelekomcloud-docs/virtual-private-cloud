:original_name: ListFirewall.html

.. _ListFirewall:

Querying Network ACLs
=====================

Function
--------

This API is used to query information about all network ACLs, including the network ACL name and status.

URI
---

GET /v3/{project_id}/vpc/firewalls

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                        |
   +=================+=================+=================+====================================================+
   | project_id      | Yes             | String          | **Definition**:                                    |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | ID of the project that the network ACL belongs to. |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | **Range**:                                         |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | N/A                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type             | Description                                                                                                                                                 |
   +=======================+=================+==================+=============================================================================================================================================================+
   | limit                 | No              | Integer          | **Definition**:                                                                                                                                             |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | Number of resources on each page.                                                                                                                           |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | **Range**:                                                                                                                                                  |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | 0 to 2000                                                                                                                                                   |
   +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker                | No              | String           | **Definition**:                                                                                                                                             |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | Start resource ID of pagination query. If the parameter is left blank, only resources on the first page are queried.                                        |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | **Range**:                                                                                                                                                  |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | Network ACL ID.                                                                                                                                             |
   +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | No              | Array of strings | **Definition**:                                                                                                                                             |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | ID of the network ACL, which can be used to filter the network ACL. Multiple IDs can be specified for filtering.                                            |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | **Range**:                                                                                                                                                  |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | N/A                                                                                                                                                         |
   +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | No              | Array of strings | **Definition**:                                                                                                                                             |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | Name of the network ACL, which can be used to filter the network ACL. Multiple names can be specified for filtering.                                        |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | **Range**:                                                                                                                                                  |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | N/A                                                                                                                                                         |
   +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | No              | String           | **Definition**:                                                                                                                                             |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | Network ACL status, which indicates whether the network ACL has been associated with a subnet. This value can be used to filter the network ACL.            |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | **Range**:                                                                                                                                                  |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | -  ACTIVE: Filter network ACLs that have been associated with subnets.                                                                                      |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | -  INACTIVE: Filter network ACLs that have not been associated with subnets.                                                                                |
   +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up        | No              | Boolean          | **Definition**:                                                                                                                                             |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | Administrative status of a network ACL, which indicates whether the network ACL is enabled or disabled and can be used to filter the network ACL.           |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | **Range**:                                                                                                                                                  |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | -  true: Filter network ACLs that are enabled.                                                                                                              |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | -  false: Filter network ACLs that are disabled.                                                                                                            |
   +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | Array of strings | **Definition**:                                                                                                                                             |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | ID of the enterprise project that the network ACL belongs to. You can use this field to filter network ACLs in an enterprise project.                       |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | **Range**:                                                                                                                                                  |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | -  The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). **0** indicates the default enterprise project. |
   |                       |                 |                  |                                                                                                                                                             |
   |                       |                 |                  | -  To obtain network ACLs of all enterprise projects, set this parameter to **all_granted_eps**.                                                            |
   +-----------------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+----------------------------------------------------------------------------------------+------------------------------------------+
   | Parameter             | Type                                                                                   | Description                              |
   +=======================+========================================================================================+==========================================+
   | firewalls             | Array of :ref:`ListFirewallDetail <listfirewall__response_listfirewalldetail>` objects | **Definition**:                          |
   |                       |                                                                                        |                                          |
   |                       |                                                                                        | Response body for querying network ACLs. |
   |                       |                                                                                        |                                          |
   |                       |                                                                                        | **Range**:                               |
   |                       |                                                                                        |                                          |
   |                       |                                                                                        | N/A                                      |
   +-----------------------+----------------------------------------------------------------------------------------+------------------------------------------+
   | page_info             | :ref:`PageInfo <listfirewall__response_pageinfo>` object                               | **Definition**:                          |
   |                       |                                                                                        |                                          |
   |                       |                                                                                        | Pagination information.                  |
   |                       |                                                                                        |                                          |
   |                       |                                                                                        | **Range**:                               |
   |                       |                                                                                        |                                          |
   |                       |                                                                                        | N/A                                      |
   +-----------------------+----------------------------------------------------------------------------------------+------------------------------------------+
   | request_id            | String                                                                                 | **Definition**:                          |
   |                       |                                                                                        |                                          |
   |                       |                                                                                        | Request ID.                              |
   |                       |                                                                                        |                                          |
   |                       |                                                                                        | **Range**:                               |
   |                       |                                                                                        |                                          |
   |                       |                                                                                        | N/A                                      |
   +-----------------------+----------------------------------------------------------------------------------------+------------------------------------------+

.. _listfirewall__response_listfirewalldetail:

.. table:: **Table 4** ListFirewallDetail

   +-----------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                     | Description                                                                                                                                              |
   +=======================+==========================================================================================+==========================================================================================================================================================+
   | id                    | String                                                                                   | **Definition**:                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | Network ACL ID. Each network ACL comes with an ID, which uniquely identifies the network ACL.                                                            |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | **Range**:                                                                                                                                               |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | The value is in UUID format with hyphens (-).                                                                                                            |
   +-----------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                                   | **Definition**:                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | Name of the network ACL.                                                                                                                                 |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | **Range**:                                                                                                                                               |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods.                                          |
   +-----------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                                   | **Definition**:                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | Supplementary information about the network ACL.                                                                                                         |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | **Range**:                                                                                                                                               |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | The value can contain 0 to 255 characters and cannot contain angle brackets (< or >).                                                                    |
   +-----------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                                                   | **Definition**:                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | ID of the project that the network ACL belongs to.                                                                                                       |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | **Range**:                                                                                                                                               |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | N/A                                                                                                                                                      |
   +-----------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                                                   | **Definition**:                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | Time when the network ACL was created. The value is automatically generated by the system.                                                               |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | **Range**:                                                                                                                                               |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | The value is a UTC time in the format of *yyyy-MM-ddTHH:mm:ssZ*.                                                                                         |
   +-----------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                                                   | **Definition**:                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | Time when the network ACL was last updated. The value is automatically generated by the system.                                                          |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | **Range**:                                                                                                                                               |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | The value is a UTC time in the format of *yyyy-MM-ddTHH:mm:ssZ*.                                                                                         |
   +-----------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up        | Boolean                                                                                  | **Definition**:                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | Network ACL administrative status.                                                                                                                       |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | **Range**:                                                                                                                                               |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | -  true: The network ACL is enabled.                                                                                                                     |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | -  false: The network ACL is disabled.                                                                                                                   |
   +-----------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                                                   | **Definition**:                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | Network ACL status.                                                                                                                                      |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | **Range**:                                                                                                                                               |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | -  ACTIVE: The network ACL is associated with a subnet.                                                                                                  |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | -  INACTIVE: The network ACL is not associated with a subnet.                                                                                            |
   +-----------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | String                                                                                   | **Definition**:                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | ID of the enterprise project that the network ACL belongs to.                                                                                            |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | **Range**:                                                                                                                                               |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). **0** indicates the default enterprise project. |
   +-----------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Array of :ref:`ResponseTag <listfirewall__response_responsetag>` objects                 | **Definition**:                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | Tags of a network ACL, including tag keys and tag values, which can be used to classify and identify resources. For details, see the tag objects.        |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | **Range**:                                                                                                                                               |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | N/A                                                                                                                                                      |
   +-----------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | associations          | Array of :ref:`FirewallAssociation <listfirewall__response_firewallassociation>` objects | **Definition**:                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | Subnets associated with the network ACL.                                                                                                                 |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | **Range**:                                                                                                                                               |
   |                       |                                                                                          |                                                                                                                                                          |
   |                       |                                                                                          | N/A                                                                                                                                                      |
   +-----------------------+------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listfirewall__response_responsetag:

.. table:: **Table 5** ResponseTag

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                        |
   +=======================+=======================+====================================================================================================================================+
   | key                   | String                | **Definition**:                                                                                                                    |
   |                       |                       |                                                                                                                                    |
   |                       |                       | Tag key.                                                                                                                           |
   |                       |                       |                                                                                                                                    |
   |                       |                       | **Range**:                                                                                                                         |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  A tag key can contain a maximum of 128 Unicode characters and cannot be left blank.                                             |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  Each tag key of a resource must be unique.                                                                                      |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  The value can contain:                                                                                                          |
   |                       |                       |                                                                                                                                    |
   |                       |                       |    -  Letters                                                                                                                      |
   |                       |                       |                                                                                                                                    |
   |                       |                       |    -  Digits                                                                                                                       |
   |                       |                       |                                                                                                                                    |
   |                       |                       |    -  Special characters: underscores (_), periods (.), colons (:), plus signs (+), hyphens (-), at signs (@), and equal signs (=) |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | value                 | String                | **Definition**:                                                                                                                    |
   |                       |                       |                                                                                                                                    |
   |                       |                       | Tag value.                                                                                                                         |
   |                       |                       |                                                                                                                                    |
   |                       |                       | **Range**:                                                                                                                         |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  Each value can contain a maximum of 255 Unicode characters and can be left blank.                                               |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  The value can contain:                                                                                                          |
   |                       |                       |                                                                                                                                    |
   |                       |                       |    -  Letters                                                                                                                      |
   |                       |                       |                                                                                                                                    |
   |                       |                       |    -  Digits                                                                                                                       |
   |                       |                       |                                                                                                                                    |
   |                       |                       |    -  Special characters: underscores (_), colons (:), plus signs (+), hyphens (-), at signs (@), and equal signs (=)              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+

.. _listfirewall__response_firewallassociation:

.. table:: **Table 6** FirewallAssociation

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                              |
   +=======================+=======================+==========================================================================================+
   | virsubnet_id          | String                | **Definition**:                                                                          |
   |                       |                       |                                                                                          |
   |                       |                       | ID of the subnet associated with the network ACL.                                        |
   |                       |                       |                                                                                          |
   |                       |                       | **Range**:                                                                               |
   |                       |                       |                                                                                          |
   |                       |                       | -  If the network ACL type is normal, it can only be associated with common subnets.     |
   |                       |                       |                                                                                          |
   |                       |                       | -  If the network ACL type is CloudDCN, it can only be associated with CloudDCN subnets. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+

.. _listfirewall__response_pageinfo:

.. table:: **Table 7** PageInfo

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                |
   +=======================+=======================+============================================================================================================+
   | previous_marker       | String                | **Definition**:                                                                                            |
   |                       |                       |                                                                                                            |
   |                       |                       | The first record on the current page.                                                                      |
   |                       |                       |                                                                                                            |
   |                       |                       | **Range**:                                                                                                 |
   |                       |                       |                                                                                                            |
   |                       |                       | N/A                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | current_count         | Integer               | **Definition**:                                                                                            |
   |                       |                       |                                                                                                            |
   |                       |                       | Total number of resources on the current page.                                                             |
   |                       |                       |                                                                                                            |
   |                       |                       | **Range**:                                                                                                 |
   |                       |                       |                                                                                                            |
   |                       |                       | N/A                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | next_marker           | String                | **Definition**:                                                                                            |
   |                       |                       |                                                                                                            |
   |                       |                       | The last record on the current page. The **next_marker** field does not exist if the page is the last one. |
   |                       |                       |                                                                                                            |
   |                       |                       | **Range**:                                                                                                 |
   |                       |                       |                                                                                                            |
   |                       |                       | N/A                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying network ACLs

.. code-block:: text

   GET https://{Endpoint}/v3/{project_id}/vpc/firewalls

Example Responses
-----------------

**Status code: 200**

Normal response to the GET operation. For more status codes, see :ref:`Status Codes <vpc_api_0002>`.

.. code-block::

   {
     "firewalls" : [ {
       "id" : "e9a7731d-5bd9-4250-a524-b9a076fd5629",
       "name" : "network_acl_test1",
       "description" : "network_acl_test1",
       "project_id" : "9476ea5a8a9849c38358e43c0c3a9e12",
       "created_at" : "2022-04-07T07:30:46.000+00:00",
       "updated_at" : "2022-04-07T07:30:46.000+00:00",
       "admin_state_up" : true,
       "enterprise_project_id" : "158ad39a-dab7-45a3-9b5a-2836b3cf93f9",
       "status" : "ACTIVE",
       "tags" : [ ],
       "associations" : [ {
         "virsubnet_id" : "8359e5b0-353f-4ef3-a071-98e67a34a143"
       } ]
     } ]
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
