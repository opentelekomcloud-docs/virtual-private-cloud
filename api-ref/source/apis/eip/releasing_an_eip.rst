:original_name: vpc_eip_0005.html

.. _vpc_eip_0005:

Releasing an EIP
================

Function
--------

This API is used to release an EIP.

.. note::

   Note the following when you use EIPs of the Dedicated Load Balancer (**5_gray**) type:

   -  In **eu-de**, no more new EIPs of this type can be assigned. You can assign EIPs of the BGP (**5_bgp**) type.
   -  Existing EIPs of the Dedicated Load Balancer (**5_gray**) type can be bound to dedicated or shared load balancers.

      -  The EIP console cannot be used to bind EIPs to or unbind them from dedicated load balancers.
      -  You can use APIs to bind EIPs to or unbind them from dedicated load balancers. For details, see `Binding an EIP <https://docs.otc.t-systems.com/elastic-ip/api-ref/api_v3/eips/binding_an_eip.html>`__ and `Unbinding an EIP <https://docs.otc.t-systems.com/elastic-ip/api-ref/api_v3/eips/unbinding_an_eip.html>`__.
      -  EIPs of this type can be bound to or unbound from shared load balancers using the EIP console or APIs.
      -  You are advised to bind or unbind BGP EIPs to or from dedicated load balancers.

   -  **5_gray** EIPs cannot be added to the same shared bandwidth as EIPs of other types. If they are in the same shared bandwidth, the bandwidth limit settings will not take effect.

URI
---

DELETE /v1/{project_id}/publicips/{publicip_id}

:ref:`Table 1 <vpc_eip_0005__table45251091>` describes the parameters.

.. _vpc_eip_0005__table45251091:

.. table:: **Table 1** Parameter description

   =========== ========= ==========================================
   Parameter   Mandatory Description
   =========== ========= ==========================================
   project_id  Yes       Specifies the project ID.
   publicip_id Yes       Specifies the unique identifier of an EIP.
   =========== ========= ==========================================

Request Message
---------------

-  Request parameter

   None

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v1/{project_id}/publicips/{publicip_id}

Response Message
----------------

-  Response parameter

   None

-  Example response

   None

   Or

   .. code-block::

      {
             "code":"xxx",
             "message":"xxxxx"
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
