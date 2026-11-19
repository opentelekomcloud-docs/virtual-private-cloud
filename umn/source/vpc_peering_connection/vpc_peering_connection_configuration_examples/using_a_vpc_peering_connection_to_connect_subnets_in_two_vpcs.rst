:original_name: vpc_peering_0010.html

.. _vpc_peering_0010:

Using a VPC Peering Connection to Connect Subnets in Two VPCs
=============================================================

You can configure a VPC peering connection and set the destination of the routes added to VPC route tables to the subnet CIDR block of the peer VPC. In this way, all resources in the VPC subnets are connected. :ref:`Table 1 <vpc_peering_0010__en-us_topic_0000001252060183_table187875614582>` shows example scenarios.

.. _vpc_peering_0010__en-us_topic_0000001252060183_table187875614582:

.. table:: **Table 1** Scenario description

   +-------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scenario                                                    | Scenario Description                                                                                                                                                                                                                              | IP Address Version | Example                                                                                                                                         |
   +=============================================================+===================================================================================================================================================================================================================================================+====================+=================================================================================================================================================+
   | Two VPCs peered to two subnets in a central VPC             | You have a central VPC that requires access to the multiple other VPCs. The other VPCs need to be isolated from each other.                                                                                                                       | IPv4               | :ref:`Two VPCs Peered to Two Subnets in a Central VPC (IPv4) <vpc_peering_0010__en-us_topic_0000001252060183_section689211541612>`              |
   |                                                             |                                                                                                                                                                                                                                                   |                    |                                                                                                                                                 |
   |                                                             | -  The central VPC has separate sets of resources in different subnets.                                                                                                                                                                           |                    |                                                                                                                                                 |
   |                                                             | -  The other VPCs require access to some of the resources, but not all of them.                                                                                                                                                                   |                    |                                                                                                                                                 |
   +-------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   |                                                             |                                                                                                                                                                                                                                                   | IPv6/IPv4          | :ref:`Two VPCs Peered to Two Subnets in a Central VPC (IPv6/IPv4) <vpc_peering_0010__en-us_topic_0000001252060183_section15574181124110>`       |
   +-------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | One central VPC peered to specific subnets in two VPCs      | You have a central VPC that requires access to two other VPCs. The other VPCs need to be isolated from each other.                                                                                                                                | IPv4               | :ref:`One Central VPC Peered to Specific Subnets in Two VPCs (IPv4) <vpc_peering_0010__en-us_topic_0000001252060183_section1572192052614>`      |
   |                                                             |                                                                                                                                                                                                                                                   |                    |                                                                                                                                                 |
   |                                                             | -  The central VPC has public resources deployed and the other VPCs require access to all resources in the central VPC.                                                                                                                           |                    |                                                                                                                                                 |
   |                                                             | -  Other VPCs have multiple subnets and only one in each VPC is used for accessing resources in the central VPC.                                                                                                                                  |                    |                                                                                                                                                 |
   +-------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | One central VPC peered to overlapping subnets from two VPCs | This scenario is similar to the preceding one. If two VPCs with overlapping subnets need to peer with the central VPC, traffic may fail to be forwarded to the required destination. To prevent this, plan the network according to this example. | IPv4               | :ref:`One Central VPC Peered to Overlapping Subnets from Two VPCs (IPv4) <vpc_peering_0010__en-us_topic_0000001252060183_section5726217181413>` |
   +-------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_peering_0010__en-us_topic_0000001252060183_section689211541612:

Two VPCs Peered to Two Subnets in a Central VPC (IPv4)
------------------------------------------------------

The central VPC-A has two subnets, Subnet-A01 and Subnet-A02. The subnets are associated with different route tables. You need to create Peering-AB between Subnet-A01 and VPC-B, and Peering-AC between Subnet-A02 and VPC-C. VPC-B and VPC-C have the same CIDR block. However, there will be no route conflicts because the two subnets in VPC-A are associated with different route tables.

-  For details about resource planning, see :ref:`Table 2 <vpc_peering_0010__en-us_topic_0000001252060183_en-us_topic_0000001135431190_table195012516413>`.
-  For details about VPC peering relationships, see :ref:`Table 3 <vpc_peering_0010__en-us_topic_0000001252060183_table143498013410>`.


.. figure:: /_static/images/en-us_image_0000002555955815.png
   :alt: **Figure 1** Networking diagram (IPv4)

   **Figure 1** Networking diagram (IPv4)

.. _vpc_peering_0010__en-us_topic_0000001252060183_en-us_topic_0000001135431190_table195012516413:

.. table:: **Table 2** Resource planning details (IPv4)

   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   | VPC Name | VPC CIDR Block | Subnet Name | Subnet CIDR Block | VPC Route Table | ECS Name | Security Group                     | Private IP Address |
   +==========+================+=============+===================+=================+==========+====================================+====================+
   | VPC-A    | 172.16.0.0/16  | Subnet-A01  | 172.16.0.0/24     | rtb-VPC-A01     | ECS-A01  | sg-web: general-purpose web server | 172.16.0.111       |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   |          |                | Subnet-A02  | 172.16.1.0/24     | rtb-VPC-A02     | ECS-A02  |                                    | 172.16.1.91        |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   | VPC-B    | 10.0.0.0/16    | Subnet-B01  | 10.0.0.0/24       | rtb-VPC-B       | ECS-B01  |                                    | 10.0.0.139         |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   | VPC-C    | 10.0.0.0/16    | Subnet-C01  | 10.0.0.0/24       | rtb-VPC-C       | ECS-C01  |                                    | 10.0.0.71          |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+

.. note::

   VPC-A has two route tables. Route table rtb-VPC-A01 is associated with Subnet-A01, and route table rtb-VPC-A02 is associated with Subnet-A02. The two subnets can communicate with each other.

.. _vpc_peering_0010__en-us_topic_0000001252060183_table143498013410:

.. table:: **Table 3** Peering relationships (IPv4)

   +-----------------------------------------+-------------------------+-----------+----------+
   | Peering Relationship                    | Peering Connection Name | Local VPC | Peer VPC |
   +=========================================+=========================+===========+==========+
   | Subnet-A01 of VPC-A is peered to VPC-B. | Peering-AB              | VPC-A     | VPC-B    |
   +-----------------------------------------+-------------------------+-----------+----------+
   | Subnet-A02 of VPC-A is peered to VPC-C. | Peering-AC              | VPC-A     | VPC-C    |
   +-----------------------------------------+-------------------------+-----------+----------+

After the VPC peering connections are created, add the following routes to the route tables of the local and peer VPCs:

.. table:: **Table 4** VPC route table details (IPv4)

   +-------------+----------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   | Route Table | Destination                | Next Hop   | Route Type | Description                                                                                      |
   +=============+============================+============+============+==================================================================================================+
   | rtb-VPC-A01 | 172.16.0.0/24              | Local      | System     | Local routes are automatically added by the system for communications within a VPC.              |
   +-------------+----------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 172.16.1.0/24              | Local      | System     |                                                                                                  |
   +-------------+----------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 10.0.0.0/16 (VPC-B)        | Peering-AB | Custom     | Add a route with the CIDR block of VPC-B as the destination and Peering-AB as the next hop.      |
   +-------------+----------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   | rtb-VPC-A02 | 172.16.0.0/24              | Local      | System     | Local routes are automatically added by the system for communications within a VPC.              |
   +-------------+----------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 172.16.1.0/24              | Local      | System     |                                                                                                  |
   +-------------+----------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 10.0.0.0/16 (VPC-C)        | Peering-AC | Custom     | Add a route with the CIDR block of VPC-C as the destination and Peering-AC as the next hop.      |
   +-------------+----------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   | rtb-VPC-B   | 10.0.0.0/24                | Local      | System     | Local routes are automatically added by the system for communications within a VPC.              |
   +-------------+----------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 172.16.0.0/24 (Subnet-A01) | Peering-AB | Custom     | Add a route with the CIDR block of Subnet-A01 as the destination and Peering-AB as the next hop. |
   +-------------+----------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   | rtb-VPC-C   | 10.0.0.0/24                | Local      | System     | Local routes are automatically added by the system for communications within a VPC.              |
   +-------------+----------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 172.16.1.0/24 (Subnet-A02) | Peering-AC | Custom     | Add a route with the CIDR block of Subnet-A02 as the destination and Peering-AC as the next hop. |
   +-------------+----------------------------+------------+------------+--------------------------------------------------------------------------------------------------+

.. _vpc_peering_0010__en-us_topic_0000001252060183_section15574181124110:

Two VPCs Peered to Two Subnets in a Central VPC (IPv6/IPv4)
-----------------------------------------------------------

The central VPC-A has two subnets, Subnet-A01 and Subnet-A02. The subnets are associated with different route tables. You need to create Peering-AB between Subnet-A01 and VPC-B for IPv6 communication, and Peering-AC between Subnet-A02 and VPC-C for IPv4 communication. VPC-B and VPC-C have the same CIDR block. However, there will be no route conflicts because the two subnets in VPC-A are associated with different route tables.

-  For details about resource planning, see :ref:`Table 5 <vpc_peering_0010__en-us_topic_0000001252060183_table1557416134110>`.
-  For details about VPC peering relationships, see :ref:`Table 6 <vpc_peering_0010__en-us_topic_0000001252060183_table19575121104114>`.


.. figure:: /_static/images/en-us_image_0000002524875908.png
   :alt: **Figure 2** Networking diagram (IPv6/IPv4)

   **Figure 2** Networking diagram (IPv6/IPv4)

.. _vpc_peering_0010__en-us_topic_0000001252060183_table1557416134110:

.. table:: **Table 5** Resource planning details (IPv6/IPv4)

   +----------+----------------+-------------+---------------------------------+-----------------+----------+------------------------------------+------------------------------------------------+
   | VPC Name | VPC CIDR Block | Subnet Name | Subnet CIDR Block               | VPC Route Table | ECS Name | Security Group                     | Private IP Address                             |
   +==========+================+=============+=================================+=================+==========+====================================+================================================+
   | VPC-A    | 172.16.0.0/16  | Subnet-A01  | -  IPv4: 172.16.0.0/24          | rtb-VPC-A01     | ECS-A01  | sg-web: general-purpose web server | -  IPv4: 172.16.0.111                          |
   |          |                |             | -  IPv6: 2407:c080:802:c34::/64 |                 |          |                                    | -  IPv6: 2407:c080:802:c34:a925:f12e:cfa0:8edb |
   +----------+----------------+-------------+---------------------------------+-----------------+----------+------------------------------------+------------------------------------------------+
   |          |                | Subnet-A02  | 172.16.1.0/24                   | rtb-VPC-A02     | ECS-A02  |                                    | 172.16.1.91                                    |
   +----------+----------------+-------------+---------------------------------+-----------------+----------+------------------------------------+------------------------------------------------+
   | VPC-B    | 10.0.0.0/16    | Subnet-B01  | -  IPv4: 10.0.0.0/24            | rtb-VPC-B       | ECS-B01  |                                    | -  IPv4: 10.0.0.139                            |
   |          |                |             | -  IPv6: 2407:c080:802:c35::/64 |                 |          |                                    | -  IPv6: 2407:c080:802:c35:493:33f4:4531:5162  |
   +----------+----------------+-------------+---------------------------------+-----------------+----------+------------------------------------+------------------------------------------------+
   | VPC-C    | 10.0.0.0/16    | Subnet-C01  | 10.0.0.0/24                     | rtb-VPC-C       | ECS-C01  |                                    | 10.0.0.71                                      |
   +----------+----------------+-------------+---------------------------------+-----------------+----------+------------------------------------+------------------------------------------------+

.. note::

   VPC-A has two route tables. Route table rtb-VPC-A01 is associated with Subnet-A01, and route table rtb-VPC-A02 is associated with Subnet-A02. The two subnets can communicate with each other.

.. _vpc_peering_0010__en-us_topic_0000001252060183_table19575121104114:

.. table:: **Table 6** Peering relationships (IPv6/IPv4)

   +------------------------------------------------+-------------------------+-----------+----------+
   | Peering Relationship                           | Peering Connection Name | Local VPC | Peer VPC |
   +================================================+=========================+===========+==========+
   | Subnet-A01 of VPC-A is peered to VPC-B. (IPv6) | Peering-AB              | VPC-A     | VPC-B    |
   +------------------------------------------------+-------------------------+-----------+----------+
   | Subnet-A02 of VPC-A is peered to VPC-C. (IPv4) | Peering-AC              | VPC-A     | VPC-C    |
   +------------------------------------------------+-------------------------+-----------+----------+

After the VPC peering connections are created, add the following routes to the route tables of the local and peer VPCs:

.. table:: **Table 7** VPC route table details (IPv6/IPv4)

   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   | Route Table | Destination                         | Next Hop   | Route Type | Description                                                                                                                  |
   +=============+=====================================+============+============+==============================================================================================================================+
   | rtb-VPC-A01 | 172.16.0.0/24                       | Local      | System     | Local routes are automatically added by the system for communications within a VPC.                                          |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   |             | 2407:c080:802:c34::/64              | Local      | System     |                                                                                                                              |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   |             | 172.16.1.0/24                       | Local      | System     |                                                                                                                              |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   |             | 10.0.0.0/16 (VPC-B)                 | Peering-AB | Custom     | Add a route with the CIDR block of VPC-B as the destination and Peering-AB as the next hop for IPv4 communication.           |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   |             | 2407:c080:802:c35::/64 (Subnet-B01) | Peering-AB | Custom     | Add a route with the IPv6 CIDR block of Subnet-B01 as the destination and Peering-AB as the next hop for IPv6 communication. |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   | rtb-VPC-A02 | 172.16.0.0/24                       | Local      | System     | Local routes are automatically added by the system for communications within a VPC.                                          |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   |             | 2407:c080:802:c34::/64              | Local      | System     |                                                                                                                              |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   |             | 172.16.1.0/24                       | Local      | System     |                                                                                                                              |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   |             | 10.0.0.0/16 (VPC-C)                 | Peering-AC | Custom     | Add a route with the CIDR block of VPC-C as the destination and Peering-AC as the next hop for IPv4 communication.           |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   | rtb-VPC-B   | 10.0.0.0/24                         | Local      | System     | Local routes are automatically added by the system for communications within a VPC.                                          |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   |             | 2407:c080:802:c35::/64              | Local      | System     |                                                                                                                              |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   |             | 172.16.0.0/24 (Subnet-A01)          | Peering-AB | Custom     | Add a route with the CIDR block of Subnet-A01 as the destination and Peering-AB as the next hop for IPv4 communication.      |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   |             | 2407:c080:802:c34::/64 (Subnet-A01) | Peering-AB | Custom     | Add a route with the IPv6 CIDR block of Subnet-A01 as the destination and Peering-AB as the next hop for IPv6 communication. |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   | rtb-VPC-C   | 10.0.0.0/24                         | Local      | System     | Local routes are automatically added by the system for communications within a VPC.                                          |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+
   |             | 172.16.1.0/24 (Subnet-A02)          | Peering-AC | Custom     | Add a route with the CIDR block of Subnet-A02 as the destination and Peering-AC as the next hop for IPv4 communication.      |
   +-------------+-------------------------------------+------------+------------+------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_peering_0010__en-us_topic_0000001252060183_section1572192052614:

One Central VPC Peered to Specific Subnets in Two VPCs (IPv4)
-------------------------------------------------------------

You need to create Peering-AB between central VPC-A and Subnet-B01 in VPC-B, and Peering-AC between central VPC-A and Subnet-C02 in VPC-C. VPC-B and VPC-C have the same CIDR block, but the CIDR blocks of Subnet-B01 and Subnet-C02 do not overlap. Therefore, there will be no route conflicts.

-  For details about resource planning, see :ref:`Table 8 <vpc_peering_0010__en-us_topic_0000001252060183_table17262052616>`.
-  For details about VPC peering relationships, see :ref:`Table 9 <vpc_peering_0010__en-us_topic_0000001252060183_table167392082617>`.


.. figure:: /_static/images/en-us_image_0000002555955817.png
   :alt: **Figure 3** Networking diagram (IPv4)

   **Figure 3** Networking diagram (IPv4)

.. _vpc_peering_0010__en-us_topic_0000001252060183_table17262052616:

.. table:: **Table 8** Resource planning details (IPv4)

   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   | VPC Name | VPC CIDR Block | Subnet Name | Subnet CIDR Block | VPC Route Table | ECS Name | Security Group                     | Private IP Address |
   +==========+================+=============+===================+=================+==========+====================================+====================+
   | VPC-A    | 172.16.0.0/16  | Subnet-A01  | 172.16.0.0/24     | rtb-VPC-A       | ECS-A01  | sg-web: general-purpose web server | 172.16.0.111       |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   | VPC-B    | 10.0.0.0/16    | Subnet-B01  | 10.0.0.0/24       | rtb-VPC-B       | ECS-B01  |                                    | 10.0.0.139         |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   |          |                | Subnet-B02  | 10.0.1.0/24       | rtb-VPC-B       | ECS-B02  |                                    | 10.0.1.167         |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   | VPC-C    | 10.0.0.0/16    | Subnet-C01  | 10.0.0.0/24       | rtb-VPC-C       | ECS-C01  |                                    | 10.0.0.71          |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   |          |                | Subnet-C02  | 10.0.1.0/24       | rtb-VPC-C       | ECS-C02  |                                    | 10.0.1.116         |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+

.. _vpc_peering_0010__en-us_topic_0000001252060183_table167392082617:

.. table:: **Table 9** Peering relationships (IPv4)

   +-----------------------------------------+-------------------------+-----------+----------+
   | Peering Relationship                    | Peering Connection Name | Local VPC | Peer VPC |
   +=========================================+=========================+===========+==========+
   | VPC-A is peered to Subnet-B01 of VPC-B. | Peering-AB              | VPC-A     | VPC-B    |
   +-----------------------------------------+-------------------------+-----------+----------+
   | VPC-A is peered to Subnet-C02 of VPC-C. | Peering-AC              | VPC-A     | VPC-C    |
   +-----------------------------------------+-------------------------+-----------+----------+

After the VPC peering connections are created, add the following routes to the route tables of the local and peer VPCs:

.. table:: **Table 10** VPC route table details (IPv4)

   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   | Route Table | Destination              | Next Hop   | Route Type | Description                                                                                      |
   +=============+==========================+============+============+==================================================================================================+
   | rtb-VPC-A   | 172.16.0.0/24            | Local      | System     | Local routes are automatically added by the system for communications within a VPC.              |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 10.0.0.0/24 (Subnet-B01) | Peering-AB | Custom     | Add a route with the CIDR block of Subnet-B01 as the destination and Peering-AB as the next hop. |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 10.0.1.0/24 (Subnet-C02) | Peering-AC | Custom     | Add a route with the CIDR block of Subnet-C02 as the destination and Peering-AC as the next hop. |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   | rtb-VPC-B   | 10.0.0.0/24              | Local      | System     | Local routes are automatically added by the system for communications within a VPC.              |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 10.0.1.0/24              | Local      | System     |                                                                                                  |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 172.16.0.0/16 (VPC-A)    | Peering-AB | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AB as the next hop.      |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   | rtb-VPC-C   | 10.0.0.0/24              | Local      | System     | Local routes are automatically added by the system for communications within a VPC.              |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 10.0.1.0/24              | Local      | System     |                                                                                                  |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 172.16.0.0/16 (VPC-A)    | Peering-AC | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AC as the next hop.      |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+

.. _vpc_peering_0010__en-us_topic_0000001252060183_section5726217181413:

One Central VPC Peered to Overlapping Subnets from Two VPCs (IPv4)
------------------------------------------------------------------

If you want to create VPC peering connections between a VPC and multiple overlapping subnets from different VPCs, ensure that the destinations of the routes added for the peering connections do not conflict and traffic can be correctly forwarded.

In this example, you need to create Peering-AB between central VPC-A and Subnet-B02 in VPC-B, and Peering-AC between central VPC-A and Subnet-C02 in VPC-C. Subnet-B02 and Subnet-C02 have the same CIDR block, and ECS-B02 and ECS-C02 have the same private IP address (10.0.1.167/32).

-  For details about resource planning, see :ref:`Table 11 <vpc_peering_0010__en-us_topic_0000001252060183_table3727121741417>`.
-  For details about VPC peering relationships, see :ref:`Table 12 <vpc_peering_0010__en-us_topic_0000001252060183_table137291117101413>`.


.. figure:: /_static/images/en-us_image_0000002524875910.png
   :alt: **Figure 4** Networking diagram (IPv4)

   **Figure 4** Networking diagram (IPv4)

.. _vpc_peering_0010__en-us_topic_0000001252060183_table3727121741417:

.. table:: **Table 11** Resource planning details (IPv4)

   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   | VPC Name | VPC CIDR Block | Subnet Name | Subnet CIDR Block | VPC Route Table | ECS Name | Security Group                     | Private IP Address |
   +==========+================+=============+===================+=================+==========+====================================+====================+
   | VPC-A    | 172.16.0.0/16  | Subnet-A01  | 172.16.0.0/24     | rtb-VPC-A       | ECS-A01  | sg-web: general-purpose web server | 172.16.0.111       |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   | VPC-B    | 10.0.0.0/16    | Subnet-B01  | 10.0.0.0/24       | rtb-VPC-B       | ECS-B01  |                                    | 10.0.0.139         |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   |          |                | Subnet-B02  | 10.0.1.0/24       | rtb-VPC-B       | ECS-B02  |                                    | 10.0.1.167         |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   | VPC-C    | 10.0.0.0/16    | Subnet-C01  | 10.0.0.0/24       | rtb-VPC-C       | ECS-C01  |                                    | 10.0.0.71          |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+
   |          |                | Subnet-C02  | 10.0.1.0/24       | rtb-VPC-C       | ECS-C02  |                                    | 10.0.1.167         |
   +----------+----------------+-------------+-------------------+-----------------+----------+------------------------------------+--------------------+

.. _vpc_peering_0010__en-us_topic_0000001252060183_table137291117101413:

.. table:: **Table 12** Peering relationships (IPv4)

   +-----------------------------------------+-------------------------+-----------+----------+
   | Peering Relationship                    | Peering Connection Name | Local VPC | Peer VPC |
   +=========================================+=========================+===========+==========+
   | VPC-A is peered to Subnet-B02 of VPC-B. | Peering-AB              | VPC-A     | VPC-B    |
   +-----------------------------------------+-------------------------+-----------+----------+
   | VPC-A is peered to Subnet-C02 of VPC-C. | Peering-AC              | VPC-A     | VPC-C    |
   +-----------------------------------------+-------------------------+-----------+----------+

If you add routes to the route tables of the local and peer VPCs according to :ref:`Table 13 <vpc_peering_0010__en-us_topic_0000001252060183_table117301117101418>`, the response traffic cannot be correctly forwarded. The details are as follows:

#. ECS-B02 in Subnet-B02 of VPC-B sends request traffic to VPC-A through the route with Peering-AB as the next hop in the rtb-VPC-B route table.
#. VPC-A receives the request traffic from ECS-B02 and expects to send the response traffic to ECS-B02. The rtb-VPC-A route table has the route with 10.0.1.167/32 as the destination, but its next hop is Peering-AC. The response traffic is incorrectly sent to VPC-C.
#. ECS-C02 in Subnet-C02 of VPC-C has the same private IP address (10.0.1.167/32) as ECS-B02. The response traffic is incorrectly sent to ECS-C02, and ECS-B02 cannot receive the response traffic.

.. _vpc_peering_0010__en-us_topic_0000001252060183_table117301117101418:

.. table:: **Table 13** VPC route table details (IPv4)

   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   | Route Table | Destination              | Next Hop   | Route Type | Description                                                                                      |
   +=============+==========================+============+============+==================================================================================================+
   | rtb-VPC-A   | 172.16.0.0/24            | Local      | System     | Local routes are automatically added by the system for communications within a VPC.              |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 10.0.1.0/24 (Subnet-C02) | Peering-AC | Custom     | Add a route with the CIDR block of Subnet-C02 as the destination and Peering-AC as the next hop. |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   | rtb-VPC-B   | 10.0.0.0/24              | Local      | System     | Local routes are automatically added by the system for communications within a VPC.              |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 10.0.1.0/24              | Local      | System     |                                                                                                  |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 172.16.0.0/16 (VPC-A)    | Peering-AB | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AB as the next hop.      |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   | rtb-VPC-C   | 10.0.0.0/24              | Local      | System     | Local routes are automatically added by the system for communications within a VPC.              |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 10.0.1.0/24              | Local      | System     |                                                                                                  |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
   |             | 172.16.0.0/16 (VPC-A)    | Peering-AC | Custom     | Add a route with the CIDR block of VPC-A as the destination and Peering-AC as the next hop.      |
   +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+

If there are overlapping subnets, configure routes as follows to prevent traffic from being incorrectly forwarded:

-  Suggestion 1: In the rtb-VPC-A route table, add a route with Peering-AB as the next hop and the private IP address of ECS-B02 (10.0.1.167/32) as the destination. The route with 10.0.1.167/32 as the destination is preferentially matched based on the longest prefix match rule to ensure that VPC-A sends the response traffic to ECS-B02. For more configurations, see :ref:`Using a VPC Peering Connection to Connect ECSs in Two VPCs <vpc_peering_0011>`.

   .. table:: **Table 14** VPC route table details

      +-------------+--------------------------+------------+------------+-------------------------------------------------------------------------------------------------------+
      | Route Table | Destination              | Next Hop   | Route Type | Description                                                                                           |
      +=============+==========================+============+============+=======================================================================================================+
      | rtb-VPC-A   | 172.16.0.0/24            | Local      | System     | Local routes are automatically added by the system for communications within a VPC.                   |
      +-------------+--------------------------+------------+------------+-------------------------------------------------------------------------------------------------------+
      |             | 10.0.1.167/32 (ECS-B02)  | Peering-AB | Custom     | Add a route with the private IP address of ECS-B02 as the destination and Peering-AB as the next hop. |
      +-------------+--------------------------+------------+------------+-------------------------------------------------------------------------------------------------------+
      |             | 10.0.1.0/24 (Subnet-C02) | Peering-AC | Custom     | Add a route with the CIDR block of Subnet-C02 as the destination and Peering-AC as the next hop.      |
      +-------------+--------------------------+------------+------------+-------------------------------------------------------------------------------------------------------+

-  Suggestion 2: In the rtb-VPC-A route table, change the destination of the route with Peering-AC as the next hop from Subnet-C02 to Subnet-C01. Add a route with Peering-AB as the next hop and Subnet-B02 as the destination to ensure that VPC-A can send the response traffic to Subnet-B02 in VPC-B.

   .. table:: **Table 15** VPC route table details

      +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
      | Route Table | Destination              | Next Hop   | Route Type | Description                                                                                      |
      +=============+==========================+============+============+==================================================================================================+
      | rtb-VPC-A   | 172.16.0.0/24            | Local      | System     | Local routes are automatically added by the system for communications within a VPC.              |
      +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
      |             | 10.0.1.0/24 (Subnet-B02) | Peering-AB | Custom     | Add a route with the CIDR block of Subnet-B02 as the destination and Peering-AB as the next hop. |
      +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
      |             | 10.0.0.0/24 (Subnet-C01) | Peering-AC | Custom     | Add a route with the CIDR block of Subnet-C01 as the destination and Peering-AC as the next hop. |
      +-------------+--------------------------+------------+------------+--------------------------------------------------------------------------------------------------+
