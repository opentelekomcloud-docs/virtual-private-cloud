:original_name: vpc_faq_0019.html

.. _vpc_faq_0019:

Can I Bind an EIP to Multiple ECSs?
===================================

Each EIP can be bound to only one ECS at a time.

Multiple ECSs cannot share the same EIP. An ECS and its EIP must be in the same region. To enable ECSs across AZs in a VPC to share an EIP, you can use a NAT gateway by referring to `NAT Gateway User Guide <https://docs.otc.t-systems.com/nat-gateway/umn/overview/what_is_nat_gateway.html>`__.
