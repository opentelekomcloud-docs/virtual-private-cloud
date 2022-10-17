:original_name: vpc_firewall_0001.html

.. _vpc_firewall_0001:

Querying Firewall Rules
=======================

Function
--------

This API is used to query all firewall rules accessible to the tenant submitting the request.

URI
---

GET /v2.0/fwaas/firewall_rules

Example:

.. code-block:: text

   GET https://{Endpoint}/v2.0/fwaas/firewall_rules?name={firewall_rule_name}&tenant_id={tenant_id}&public={is_public}&protocol={protocol}&ip_version={ip_version}&action={action}&enabled={is_enabled}

Example of querying rules by page

.. code-block:: text

   GET https://{Endpoint}/v2.0/fwaas/firewall_rules?limit=2&marker=2a193015-4a88-4aa1-84ad-d4955adae707&page_reverse=False

:ref:`Table 1 <vpc_firewall_0001__table997509428>` describes the parameters.

.. _vpc_firewall_0001__table997509428:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================+
   | id              | No              | String          | Specifies that the firewall rule ID is used as the filtering condition.                                                                                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Specifies that the firewall rule name is used as the filtering condition.                                                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | Specifies that the firewall rule description is used as the filtering condition.                                                                                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_version      | No              | Integer         | Specifies that the IP address version is used as the filtering condition.                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | The value can be **4** (IPv4) or **6** (IPv6).                                                                                                                                                                         |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action          | No              | String          | Specifies that the firewall rule action is used as the filtering condition.                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | The value can be **allow** or **deny**.                                                                                                                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enabled         | No              | Boolean         | Specifies that the firewall rule is enabled is used as the filtering condition.                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | The value can be **true** or **false**.                                                                                                                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id       | No              | String          | Specifies that the project ID is used as the filtering condition.                                                                                                                                                      |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Specifies a resource ID for pagination query, indicating that the query starts from the next record of the specified resource ID.                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | This parameter can work together with the parameter **limit**.                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | -  If parameters **marker** and **limit** are not passed, all resource records will be returned.                                                                                                                       |
   |                 |                 |                 | -  If the parameter **marker** is not passed and the value of parameter **limit** is set to **10**, the first 10 resource records will be returned.                                                                    |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the value of parameter **limit** is set to **10**, the 11th to 20th resource records will be returned.                    |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the parameter **limit** is not passed, resource records starting from the 11th records (including 11th) will be returned. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax.                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

None

Response Message
----------------

.. table:: **Table 2** Response parameter

   +-----------------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                               | Description                                                                                                                                                                                                          |
   +=======================+====================================================================================+======================================================================================================================================================================================================================+
   | firewall_rules        | Array of :ref:`Firewall Rule <vpc_firewall_0001__table38646929121127>` objects     | Specifies the firewall rule list. For details, see :ref:`Table 4 <vpc_firewall_0001__table38646929121127>`.                                                                                                          |
   +-----------------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | firewall_rules_links  | Array of :ref:`firewall_rules_link <vpc_firewall_0001__table2049004519490>` Object | Specifies the pagination information. For details, see :ref:`Table 3 <vpc_firewall_0001__table2049004519490>`.                                                                                                       |
   |                       |                                                                                    |                                                                                                                                                                                                                      |
   |                       |                                                                                    | The value of **rel** will be **next** and that of **href** will be a link only when **limit** is used for filtering and the number of resources exceeds the value of **limit** or 2000 (default value of **limit**). |
   +-----------------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0001__table2049004519490:

.. table:: **Table 3** **firewall_rules_link** object

   +-----------+--------+----------------------------------------------------------------------+
   | Parameter | Type   | Description                                                          |
   +===========+========+======================================================================+
   | href      | String | Specifies the API link.                                              |
   +-----------+--------+----------------------------------------------------------------------+
   | rel       | String | Specifies the relationship between the API link and the API version. |
   +-----------+--------+----------------------------------------------------------------------+

.. _vpc_firewall_0001__table38646929121127:

.. table:: **Table 4** **Firewall Rule** objects

   +------------------------+---------+-------------------------------------------------------------------------+
   | Attribute              | Type    | Description                                                             |
   +========================+=========+=========================================================================+
   | id                     | String  | Specifies the UUID of the firewall rule.                                |
   +------------------------+---------+-------------------------------------------------------------------------+
   | name                   | String  | Specifies the firewall rule name.                                       |
   +------------------------+---------+-------------------------------------------------------------------------+
   | description            | String  | Provides supplementary information about the firewall rule.             |
   +------------------------+---------+-------------------------------------------------------------------------+
   | tenant_id              | String  | Specifies the project ID.                                               |
   +------------------------+---------+-------------------------------------------------------------------------+
   | public                 | Boolean | Specifies whether the firewall rule can be shared by different tenants. |
   +------------------------+---------+-------------------------------------------------------------------------+
   | protocol               | String  | Specifies the IP protocol.                                              |
   +------------------------+---------+-------------------------------------------------------------------------+
   | source_port            | String  | Specifies the source port number or port number range.                  |
   +------------------------+---------+-------------------------------------------------------------------------+
   | destination_port       | String  | Specifies the destination port number or port number range.             |
   +------------------------+---------+-------------------------------------------------------------------------+
   | ip_version             | Integer | Specifies the IP protocol version.                                      |
   +------------------------+---------+-------------------------------------------------------------------------+
   | source_ip_address      | String  | Specifies the source IP address or CIDR block.                          |
   +------------------------+---------+-------------------------------------------------------------------------+
   | destination_ip_address | String  | Specifies the destination IP address or CIDR block.                     |
   +------------------------+---------+-------------------------------------------------------------------------+
   | action                 | String  | Specifies action performed on traffic passing through the firewall.     |
   +------------------------+---------+-------------------------------------------------------------------------+
   | enabled                | Boolean | Specifies whether the firewall rule is enabled.                         |
   +------------------------+---------+-------------------------------------------------------------------------+
   | project_id             | String  | Specifies the project ID.                                               |
   +------------------------+---------+-------------------------------------------------------------------------+

Example:
--------

Example request

.. code-block:: text

   GET https://{Endpoint}/v2.0/fwaas/firewall_rules

Example response

.. code-block::

   {
       "firewall_rules": [
           {
               "protocol": "tcp",
               "name": "crhfwruleupdate",
               "mode": "normal",
               "tenant_id": "f480f5d250824e5fafedcf05acf1419c",
               "rule_profile": "",
               "enabled": true,
               "source_port": null,
               "source_ip_address": null,
               "destination_ip_address": null,
               "firewall_policy_id": "b4f81251-c47a-4fe1-8579-6f9271d015d1",
               "action": "deny",
               "position": 1,
               "ip_version": 4,
               "shared": false,
               "destination_port": null,
               "id": "2a193015-4a88-4aa1-84ad-d4955adae707",
               "description": "",
               "project_id": "f480f5d250824e5fafedcf05acf1419c"
           },
           {
               "protocol": "tcp",
               "name": "update_firewall-role-tommy",
               "mode": "mix",
               "tenant_id": "a1c6f90c94334bd2953d9a61b8031a68",
               "rule_profile": "",
               "enabled": false,
               "source_port": "20:50",
               "source_ip_address": null,
               "destination_ip_address": null,
               "firewall_policy_id": null,
               "action": "deny",
               "position": null,
               "ip_version": 4,
               "shared": true,
               "destination_port": "40:60",
               "id": "db7a204c-9eb1-40a2-9bd6-ed5cfd3cff32",
               "description": "update check parameter",
               "project_id": "a1c6f90c94334bd2953d9a61b8031a68"
           }
       ],
       "firewall_rules_links": [
          {    "rel": "previous",
               "href": "https://{Endpoint}/v2.0/
   fwaas/firewall_rules?marker=2a193015-4a88-4aa1-84ad-d4955adae707&page_reverse=True"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
