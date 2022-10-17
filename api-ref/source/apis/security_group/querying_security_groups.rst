:original_name: vpc_sg01_0003.html

.. _vpc_sg01_0003:

Querying Security Groups
========================

Function
--------

This API is used to query security groups using search criteria and to display the security groups in a list.

URI
---

GET /v1/{project_id}/security-groups

Example:

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/security-groups?limit=10&marker=4779ab1c-7c1a-44b1-a02e-93dfc361b32d&vpc_id=3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85

:ref:`Table 1 <vpc_sg01_0003__table1939240195259>` describes the parameters.

.. _vpc_sg01_0003__table1939240195259:

.. table:: **Table 1** Parameter description

   +-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name                    | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                         |
   +=========================+=================+=================+=====================================================================================================================================================================================================================================================================================================================================================+
   | project_id              | Yes             | String          | Specifies the project ID.                                                                                                                                                                                                                                                                                                                           |
   +-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker                  | No              | String          | Specifies a resource ID for pagination query, indicating that the query starts from the next record of the specified resource ID.                                                                                                                                                                                                                   |
   |                         |                 |                 |                                                                                                                                                                                                                                                                                                                                                     |
   |                         |                 |                 | This parameter can work together with the parameter **limit**.                                                                                                                                                                                                                                                                                      |
   |                         |                 |                 |                                                                                                                                                                                                                                                                                                                                                     |
   |                         |                 |                 | -  If parameters **marker** and **limit** are not passed, all resource records will be returned.                                                                                                                                                                                                                                                    |
   |                         |                 |                 | -  If the parameter **marker** is not passed and the value of parameter **limit** is set to **10**, the first 10 resource records will be returned.                                                                                                                                                                                                 |
   |                         |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the value of parameter **limit** is set to **10**, the 11th to 20th resource records will be returned.                                                                                                                                                 |
   |                         |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the parameter **limit** is not passed, resource records starting from the 11th records (including 11th) will be returned.                                                                                                                              |
   +-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit                   | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax.                                                                                                                                                                                                                                                  |
   |                         |                 |                 |                                                                                                                                                                                                                                                                                                                                                     |
   |                         |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                                                                                                                                                           |
   +-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id                  | No              | String          | Specifies that the VPC ID is used as the filtering condition.                                                                                                                                                                                                                                                                                       |
   +-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id   | No              | String          | -  Specifies the enterprise project ID. This field can be used to filter the security groups of an enterprise project.                                                                                                                                                                                                                              |
   |                         |                 |                 | -  The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). Value **0** indicates the default enterprise project. To obtain the security groups bound to all enterprise projects of the user or to display the security group list for enterprise project member accounts, set **all_granted_eps**. |
   |                         |                 |                 |                                                                                                                                                                                                                                                                                                                                                     |
   |                         |                 |                 | .. note::                                                                                                                                                                                                                                                                                                                                           |
   |                         |                 |                 |                                                                                                                                                                                                                                                                                                                                                     |
   |                         |                 |                 |    This parameter is unsupported. Do not use it.                                                                                                                                                                                                                                                                                                    |
   +-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_address_group_id | No              | String          | -  Specifies the remote IP address group ID. You can log in to the management console and view the ID on the IP address group page.                                                                                                                                                                                                                 |
   |                         |                 |                 | -  The value is exclusive with parameters **remote_ip_prefix** and **remote_group_id**.                                                                                                                                                                                                                                                             |
   +-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

-  Request parameter

   None

-  Example request

   .. code-block:: text

      GET https://{Endpoint}/v1/{project_id}/security-groups

Response Message
----------------

-  Response parameter

   .. table:: **Table 2** Response parameter

      +-----------------+---------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
      | Name            | Type                                                                      | Description                                                                                               |
      +=================+===========================================================================+===========================================================================================================+
      | security_groups | Array of :ref:`security_group <vpc_sg01_0003__table333218689520>` objects | Specifies the security group objects. For details, see :ref:`Table 3 <vpc_sg01_0003__table333218689520>`. |
      +-----------------+---------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+

   .. _vpc_sg01_0003__table333218689520:

   .. table:: **Table 3** Description of **security_group** fields

      +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                                                                           | Description                                                                                                                                                       |
      +=======================+================================================================================+===================================================================================================================================================================+
      | name                  | String                                                                         | Specifies the security group name.                                                                                                                                |
      +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                                                                         | Provides supplementary information about the security group.                                                                                                      |
      +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id                    | String                                                                         | Specifies the security group ID, which uniquely identifies the security group.                                                                                    |
      +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | vpc_id                | String                                                                         | Specifies the resource ID of the VPC to which the security group belongs.                                                                                         |
      |                       |                                                                                |                                                                                                                                                                   |
      |                       |                                                                                | .. note::                                                                                                                                                         |
      |                       |                                                                                |                                                                                                                                                                   |
      |                       |                                                                                |    This parameter has been discarded. Do not use it.                                                                                                              |
      +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | security_group_rules  | Array of :ref:`security_group_rule <vpc_sg01_0003__table488727239520>` objects | Specifies the default security group rules, which ensure that resources in the security group can communicate with one another.                                   |
      +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | enterprise_project_id | String                                                                         | -  Specifies the enterprise project ID. When creating a security group, associate the enterprise project ID with the security group.                              |
      |                       |                                                                                | -  The value is **0** or a string that contains a maximum of 36 characters in UUID format with hyphens (-). Value **0** indicates the default enterprise project. |
      |                       |                                                                                |                                                                                                                                                                   |
      |                       |                                                                                | .. note::                                                                                                                                                         |
      |                       |                                                                                |                                                                                                                                                                   |
      |                       |                                                                                |    This parameter is unsupported. Do not use it.                                                                                                                  |
      +-----------------------+--------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _vpc_sg01_0003__table488727239520:

   .. table:: **Table 4** **security_group_rule** objects

      +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                    | Type                  | Description                                                                                                                                                                                                                                               |
      +=========================+=======================+===========================================================================================================================================================================================================================================================+
      | id                      | String                | Specifies the security group rule ID, which uniquely identifies the security group rule.                                                                                                                                                                  |
      +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description             | String                | -  Provides supplementary information about the security group rule.                                                                                                                                                                                      |
      |                         |                       | -  The value can contain no more than 255 characters, including letters and digits.                                                                                                                                                                       |
      +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | security_group_id       | String                | Specifies the security group rule ID, which uniquely identifies the security group rule.                                                                                                                                                                  |
      +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | direction               | String                | -  Specifies the direction of access control.                                                                                                                                                                                                             |
      |                         |                       | -  Possible values are as follows:                                                                                                                                                                                                                        |
      |                         |                       |                                                                                                                                                                                                                                                           |
      |                         |                       |    -  **egress**                                                                                                                                                                                                                                          |
      |                         |                       |    -  **ingress**                                                                                                                                                                                                                                         |
      +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ethertype               | String                | -  Specifies the IP protocol version.                                                                                                                                                                                                                     |
      |                         |                       | -  The value can be **IPv4** or **IPv6**.                                                                                                                                                                                                                 |
      +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | protocol                | String                | -  Specifies the protocol type.                                                                                                                                                                                                                           |
      |                         |                       | -  The value can be **icmp**, **tcp**, or **udp**.                                                                                                                                                                                                        |
      |                         |                       | -  If the parameter is left blank, all protocols are supported.                                                                                                                                                                                           |
      +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | port_range_min          | Integer               | -  Specifies the start port number.                                                                                                                                                                                                                       |
      |                         |                       | -  The value ranges from 1 to 65535.                                                                                                                                                                                                                      |
      |                         |                       | -  The value cannot be greater than the **port_range_max** value. An empty value indicates all ports. If the protocol is **icmp**, the value range is shown in :ref:`ICMP-Port Range Relationship Table <vpc_api_0009>`.                                  |
      +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | port_range_max          | Integer               | -  Specifies the end port number.                                                                                                                                                                                                                         |
      |                         |                       | -  The value ranges from 1 to 65535.                                                                                                                                                                                                                      |
      |                         |                       | -  If the protocol is not **icmp**, the value cannot be smaller than the **port_range_min** value. An empty value indicates all ports. If the protocol is **icmp**, the value range is shown in :ref:`ICMP-Port Range Relationship Table <vpc_api_0009>`. |
      +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | remote_ip_prefix        | String                | -  Specifies the remote IP address. If the access control direction is set to **egress**, the parameter specifies the source IP address. If the access control direction is set to **ingress**, the parameter specifies the destination IP address.       |
      |                         |                       | -  The value can be in the CIDR format or IP addresses.                                                                                                                                                                                                   |
      |                         |                       | -  The parameter is exclusive with parameter **remote_group_id**.                                                                                                                                                                                         |
      +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | remote_group_id         | String                | -  Specifies the ID of the peer security group.                                                                                                                                                                                                           |
      |                         |                       | -  The value is exclusive with parameter **remote_ip_prefix**.                                                                                                                                                                                            |
      +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | remote_address_group_id | String                | -  Specifies the remote IP address group ID.                                                                                                                                                                                                              |
      |                         |                       | -  The value is exclusive with parameters **remote_ip_prefix** and **remote_group_id**.                                                                                                                                                                   |
      +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tenant_id               | String                | -  Specifies the ID of the project to which the security group rule belongs.                                                                                                                                                                              |
      +-------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "security_groups": [
              {
                  "id": "16b6e77a-08fa-42c7-aa8b-106c048884e6",
                  "name": "qq",
                  "description": "qq",
                  "vpc_id": "3ec3b33f-ac1c-4630-ad1c-7dba1ed79d85",
                  "enterprise_project_id ": "0aad99bc-f5f6-4f78-8404-c598d76b0ed2",
                  "security_group_rules": [
                      {
                          "direction": "egress",
                          "ethertype": "IPv4",
                          "id": "369e6499-b2cb-4126-972a-97e589692c62",
                          "description": "",
                          "security_group_id": "16b6e77a-08fa-42c7-aa8b-106c048884e6",
                          "remote_address_group_id": null
                      },
                      {
                          "direction": "ingress",
                          "ethertype": "IPv4",
                          "id": "0222556c-6556-40ad-8aac-9fd5d3c06171",
                          "description": "",
                          "remote_group_id": "16b6e77a-08fa-42c7-aa8b-106c048884e6",
                          "security_group_id": "16b6e77a-08fa-42c7-aa8b-106c048884e6"
                      }
                  ]
              },
              {
                  "id": "9c0f56be-a9ac-438c-8c57-fce62de19419",
                  "name": "default",
                  "description": "qq",
                  "vpc_id": "13551d6b-755d-4757-b956-536f674975c0",
                  "enterprise_project_id ": "0",
                  "security_group_rules": [
                      {
                          "direction": "egress",
                          "ethertype": "IPv4",
                          "id": "95479e0a-e312-4844-b53d-a5e4541b783f",
                          "description": "",
                          "security_group_id": "9c0f56be-a9ac-438c-8c57-fce62de19419"
                      },
                      {
                          "direction": "ingress",
                          "ethertype": "IPv4",
                          "id": "0c4a2336-b036-4fa2-bc3c-1a291ed4c431",
                          "description": "",
                          "remote_group_id": "9c0f56be-a9ac-438c-8c57-fce62de19419",
                          "security_group_id": "9c0f56be-a9ac-438c-8c57-fce62de19419"
                      }
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
