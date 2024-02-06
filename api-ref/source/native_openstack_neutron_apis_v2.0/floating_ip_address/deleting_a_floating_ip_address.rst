:original_name: vpc_floatingiP_0005.html

.. _vpc_floatingiP_0005:

Deleting a Floating IP Address
==============================

Function
--------

This API is used to delete a floating IP address.

.. note::

   Note the following when you use EIPs of the Dedicated Load Balancer (**5_gray**) type:

   -  In **eu-de**, EIPs of the Dedicated Load Balancer (**5_gray**) type cannot be assigned anymore. You can assign EIPs of the BGP (**5_bgp**) type.
   -  Existing EIPs of the Dedicated Load Balancer (**5_gray**) type can be bound to dedicated or shared load balancers.

      -  The EIP console cannot be used to bind EIPs to or unbind them from dedicated load balancers.
      -  You can use APIs to bind EIPs to or unbind them from dedicated load balancers. For details, see `Binding an EIP <https://docs.otc.t-systems.com/elastic-ip/api-ref/api_v3/eips/binding_an_eip.html>`__ and `Unbinding an EIP <https://docs.otc.t-systems.com/elastic-ip/api-ref/api_v3/eips/unbinding_an_eip.html>`__.
      -  EIPs of this type can be bound to or unbound from shared load balancers using the EIP console or APIs.
      -  You are advised to bind BGP EIPs to or unbind them from dedicated load balancers.

   -  Do not add EIPs of the dedicated load balancer type (**5_gray**) and other types to the same shared bandwidth. Otherwise, the bandwidth limit policy will not take effect.

URI
---

DELETE /v2.0/floatingips/{floatingip_id}

:ref:`Table 1 <vpc_floatingip_0005__table49321613135118>` describes the parameters.

.. _vpc_floatingip_0005__table49321613135118:

.. table:: **Table 1** Parameter description

   ============= ========= ====== =====================================
   Parameter     Mandatory Type   Description
   ============= ========= ====== =====================================
   floatingip_id Yes       String Specifies the floating IP address ID.
   ============= ========= ====== =====================================

Request Message
---------------

None

Response Message
----------------

None

Example Request
---------------

Delete the floating IP address whose ID is a95ec431-8473-463b-aede-34fb048ee3a7.

.. code-block:: text

   DELETE https://{Endpoint}/v2.0/floatingips/a95ec431-8473-463b-aede-34fb048ee3a7

Example Response
----------------

None

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
