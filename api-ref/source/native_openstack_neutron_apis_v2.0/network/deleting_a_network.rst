:original_name: vpc_network_0005.html

.. _vpc_network_0005:

Deleting a Network
==================

Function
--------

This API is used to delete a network.

URI
---

DELETE /v2.0/networks/{network_id}

:ref:`Table 1 <vpc_network_0005__table1710134691014>` describes the parameters.

.. _vpc_network_0005__table1710134691014:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Name       Mandatory Description
   ========== ========= =========================
   network_id Yes       Specifies the network ID.
   ========== ========= =========================

Request Message
---------------

None

Response Message
----------------

None

Example:
--------

Example request

.. code-block:: text

   DELETE https://{Endpoint}/v2.0/networks/60c809cb-6731-45d0-ace8-3bf5626421a9

Example response

None

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
