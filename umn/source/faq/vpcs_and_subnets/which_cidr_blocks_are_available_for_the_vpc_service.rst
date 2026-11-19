:original_name: vpc_faq_0004.html

.. _vpc_faq_0004:

Which CIDR Blocks Are Available for the VPC Service?
====================================================

The following table lists the private CIDR blocks that you can specify when creating a VPC. Consider the following when selecting a VPC CIDR block:

-  Number of IP addresses: Reserve sufficient IP addresses in case of business growth.
-  IP address range: Avoid IP address conflicts if you need to connect a VPC to an on-premises data center or connect two VPCs.

When you create a VPC, we recommend that you use a private IPv4 address range specified in `RFC 1918 <https://www.rfc-editor.org/rfc/rfc1918.txt>`__ as the CIDR block, as described in :ref:`Table 1 <vpc_faq_0004__table86319264813>`.

.. _vpc_faq_0004__table86319264813:

.. table:: **Table 1** VPC CIDR blocks (RFC 1918)

   +-------------------+-----------------------------+----------+--------------------+
   | VPC CIDR blocks   | IP Address Range            | Netmask  | Example CIDR Block |
   +===================+=============================+==========+====================+
   | 10.0.0.0/8-24     | 10.0.0.0-10.255.255.255     | 8 to 24  | 10.0.0.0/8         |
   +-------------------+-----------------------------+----------+--------------------+
   | 172.16.0.0/12-24  | 172.16.0.0-172.31.255.255   | 12 to 24 | 172.30.0.0/16      |
   +-------------------+-----------------------------+----------+--------------------+
   | 192.168.0.0/16-24 | 192.168.0.0-192.168.255.255 | 16 to 24 | 192.168.0.0/24     |
   +-------------------+-----------------------------+----------+--------------------+

In addition to these addresses, you can create a VPC with a publicly routable CIDR block that falls outside the private IPv4 address ranges specified in RFC 1918. However, the reserved system and public CIDR blocks listed in :ref:`Table 2 <vpc_faq_0004__table1655419159385>` must be excluded:

.. _vpc_faq_0004__table1655419159385:

.. table:: **Table 2** Reserved system and public CIDR blocks

   +-----------------------------------+-----------------------------------+
   | Reserved System CIDR Block        | Reserved Public CIDR Block        |
   +===================================+===================================+
   | -  100.64.0.0/10                  | -  0.0.0.0/8                      |
   | -  214.0.0.0/7                    | -  127.0.0.0/8                    |
   | -  198.18.0.0/15                  | -  240.0.0.0/4                    |
   | -  169.254.0.0/16                 |                                   |
   +-----------------------------------+-----------------------------------+

The IPv4 CIDR block you specify when you create a VPC is the primary one. The primary CIDR block cannot be changed after the VPC is created. If IP addresses in the primary CIDR block are insufficient, you can add a secondary IPv4 CIDR block to the VPC by referring to :ref:`Using a Secondary IPv4 CIDR Block <vpc_vpc_0007>`.
