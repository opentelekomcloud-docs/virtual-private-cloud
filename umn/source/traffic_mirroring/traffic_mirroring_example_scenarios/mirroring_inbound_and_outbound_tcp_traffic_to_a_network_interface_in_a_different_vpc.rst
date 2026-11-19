:original_name: vpc_mirror_24.html

.. _vpc_mirror_24:

Mirroring Inbound and Outbound TCP Traffic to a Network Interface in a Different VPC
====================================================================================

Solution Architecture
---------------------

To mirror inbound and outbound TCP traffic between a mirror source (network interface) and a given instance to a mirror target (network interface) in a VPC different from the mirror source, you can refer to the configurations in this section. In :ref:`Figure 1 <vpc_mirror_24__en-us_topic_0000002093274237_fig18617152242120>`, mirror source **ECS-source** and mirror target **ECS-target** are running in different VPCs (**VPC-A** and **VPC-B** that are connected by a VPC peering connection). Traffic between **ECS-source** and **ECS-test-A** does not need to be mirrored. To mirror TCP traffic between **ECS-source** and **ECS-test-B** to **ECS-target**, a mirror session needs to be created. In this example, mirror session **mirror-session-01** is created. You can configure it as follows:

-  Set the mirror source to **network-interface-s** on **ECS-source**. The inbound and outbound TCP traffic on this network interface will be mirrored.
-  Set the mirror target to **network-interface-t** on **ECS-target**. The inbound and outbound TCP traffic on **network-interface-s** will be mirrored to **network-interface-t**.
-  Create a mirror filter (**mirror-filter-01**) and add the following rules:

   -  Two outbound rules: Rule 1 rejects TCP traffic from **ECS-source** to **ECS-test-A**. Rule 2 accepts TCP traffic from **ECS-source** to **ECS-test-B**.
   -  Two inbound rules: Rule 1 rejects TCP traffic from **ECS-test-A** to **ECS-source**. Rule 2 accepts TCP traffic from **ECS-test-B** to **ECS-source**.

.. _vpc_mirror_24__en-us_topic_0000002093274237_fig18617152242120:

.. figure:: /_static/images/en-us_image_0000002611828103.png
   :alt: **Figure 1** Mirroring inbound and outbound TCP traffic to a mirror target in a different VPC

   **Figure 1** Mirroring inbound and outbound TCP traffic to a mirror target in a different VPC

Notes and Constraints
---------------------

See :ref:`Notes and Constraints <vpc_mirror_02__en-us_topic_0000001651378981_section1412134042913>`.

Resource Planning
-----------------

In this example, the VPCs, subnets, EIP, and ECSs must be in the same region but can be in different AZs.

.. note::

   The following resource details are only for your reference. You can modify them if needed.

.. table:: **Table 1** Resource details for mirroring inbound and outbound TCP traffic

   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Resource               | Quantity              | Description                                                                                                                                                                                                                                                                                                                                                       |
   +========================+=======================+===================================================================================================================================================================================================================================================================================================================================================================+
   | VPC and subnet         | VPC: 2                | Configure the VPCs as follows:                                                                                                                                                                                                                                                                                                                                    |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        | Subnet: 2             | -  **Name**: Set it as needed. In this example, **VPC-A** and **VPC-B** are used.                                                                                                                                                                                                                                                                                 |
   |                        |                       | -  **VPC IPv4 CIDR Block**: Set it as needed. In this example, **192.168.0.0/16** is used for **VPC-A**, and **10.0.0.0/16** is used for **VPC-B**.                                                                                                                                                                                                               |
   |                        |                       | -  **Subnet Name**: Set it as needed. In this example, there are two subnets: **Subnet-A01** in **VPC-A** and **Subnet-B01** in **VPC-B**.                                                                                                                                                                                                                        |
   |                        |                       | -  **Subnet IPv4 CIDR Block**: Set it as needed. In this example, the CIDR block of **Subnet-A01** is **192.168.0.0/24** and that of **Subnet-B01** is **10.0.1.0/24**.                                                                                                                                                                                           |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ECS                    | 4                     | Configure the ECSs as follows:                                                                                                                                                                                                                                                                                                                                    |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  **ECS Name**: Set it as needed. In this example, the ECSs are named **ECS-source**, **ECS-target**, **ECS-test-A**, and **ECS-test-B**.                                                                                                                                                                                                                        |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  **ECS Type**: In this example, the type of **ECS-source** is **General computing-plus c7t**. Currently, only network interfaces of ECSs of certain types can be used as mirror sources. For details, see :ref:`Notes and Constraints <vpc_mirror_02__en-us_topic_0000001651378981_section1412134042913>`. There are no constraints on the types of other ECSs. |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  **Image**: Set it as needed. In this example, public image **EulerOS 2.0 Standard 64 bit** is used.                                                                                                                                                                                                                                                            |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  **System Disk**: In this example, a general-purpose SSD disk of 40 GiB is used.                                                                                                                                                                                                                                                                                |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  **Data Disk**: Set it as needed. In this example, no data disk is used.                                                                                                                                                                                                                                                                                        |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  **Network**                                                                                                                                                                                                                                                                                                                                                    |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       |    -  **VPC**: Select VPCs. In this example, select **VPC-A** for **ECS-source** and **ECS-test-A**, and **VPC-B** for **ECS-target** and **ECS-test-B**.                                                                                                                                                                                                         |
   |                        |                       |    -  **Subnet**: Select subnets. In this example, select **Subnet-A01** for **ECS-source** and **ECS-test-A**, and **Subnet-B01** for **ECS-target** and **ECS-test-B**.                                                                                                                                                                                         |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  **Security Group**: In this example, the four ECSs are associated with the same security group (**Sg-X**). Ensure that all rules in :ref:`Table 2 <vpc_mirror_24__en-us_topic_0000002052878369_en-us_topic_0285680794_table102261597217>` are added.                                                                                                           |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       |    If the ECSs are associated with different security groups, you also need to add additional rules.                                                                                                                                                                                                                                                              |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       |    -  If **ECS-test-A** is associated with **Sg-X** but **ECS-source** is associated with **Sg-A**, add the rules in :ref:`Table 3 <vpc_mirror_24__en-us_topic_0000002093274237_en-us_topic_0285680794_table164981355467>` to **Sg-A** and **Sg-X** to allow traffic between **ECS-test-A** and **ECS-source**. The same applies to **ECS-test-B**.               |
   |                        |                       |    -  If **ECS-source** is associated with **Sg-A** but **ECS-target** is associated with **Sg-B**, add the rules in :ref:`Table 4 <vpc_mirror_24__en-us_topic_0000002093274237_table686503122416>` to **Sg-B** to allow UDP packets encapsulated by the mirror source to access the mirror target over port 4789.                                                |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  EIP: Select **Not required**.                                                                                                                                                                                                                                                                                                                                  |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  Private IP address: In this example, use **192.168.0.230** for **ECS-source**, **10.0.1.97** for **ECS-target**, **192.168.0.161** for **ECS-test-A**, and **10.0.1.156** for **ECS-test-B**.                                                                                                                                                                  |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EIP                    | 1                     | -  **Billing Mode**: Set it as needed. In this example, **Pay-per-use** is used.                                                                                                                                                                                                                                                                                  |
   |                        |                       | -  **EIP Name**: Set it as needed. In this example, **EIP-A** is used.                                                                                                                                                                                                                                                                                            |
   |                        |                       | -  EIP: The EIP is randomly assigned. In this example, **124.X.X.187** is used.                                                                                                                                                                                                                                                                                   |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | VPC peering connection | 1                     | -  **VPC Peering Connection Name**: Set it as needed. In this example, **Peering-AB** is used.                                                                                                                                                                                                                                                                    |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  **Local VPC**: Select a VPC as needed. In this example, select **VPC-A** and its CIDR block is **192.168.0.0/16**.                                                                                                                                                                                                                                             |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  **Account**: In this example, **VPC-A** and **VPC-B** are in the same account. Select **My account**.                                                                                                                                                                                                                                                          |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       |    Traffic cannot be mirrored across VPCs in different accounts.                                                                                                                                                                                                                                                                                                  |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  **Peer Project**: Retain the default value.                                                                                                                                                                                                                                                                                                                    |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  **Peer VPC**: Select a VPC as needed. In this example, select **VPC-B** and its CIDR block is **10.0.0.0/16**.                                                                                                                                                                                                                                                 |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  Add the routes in :ref:`Table 5 <vpc_mirror_24__en-us_topic_0000002093274237_table139835561968>` for the VPC peering connection.                                                                                                                                                                                                                               |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mirror filter          | 1                     | -  **Name**: Set it as needed. In this example, **mirror-filter-01** is used.                                                                                                                                                                                                                                                                                     |
   |                        |                       | -  Inbound rules: Add the two inbound rules in :ref:`Table 6 <vpc_mirror_24__en-us_topic_0000002093274237_table42954412446>`.                                                                                                                                                                                                                                     |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       |    -  Rule 1: rejects TCP traffic from all instances, including **ECS-test-A**, in **VPC-A** to mirror source **ECS-source**.                                                                                                                                                                                                                                     |
   |                        |                       |    -  Rule 2: accepts TCP traffic from all instances, including **ECS-test-B**, in **VPC-B** to mirror source **ECS-source**.                                                                                                                                                                                                                                     |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  Outbound rules: Add the two outbound rules in :ref:`Table 6 <vpc_mirror_24__en-us_topic_0000002093274237_table42954412446>`.                                                                                                                                                                                                                                   |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       |    -  Rule 1: rejects TCP traffic from mirror source **ECS-source** to instances, including **ECS-test-A**, in **VPC-A**.                                                                                                                                                                                                                                         |
   |                        |                       |    -  Rule 2: accepts TCP traffic from mirror source **ECS-source** to instances, including **ECS-test-B**, in **VPC-B**.                                                                                                                                                                                                                                         |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mirror session         | 1                     | -  **Basic Information**                                                                                                                                                                                                                                                                                                                                          |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       |    -  **Name**: Set it as needed. In this example, **mirror-session-01** is used.                                                                                                                                                                                                                                                                                 |
   |                        |                       |    -  **Priority**: Set it as needed. In this example, **1** is used.                                                                                                                                                                                                                                                                                             |
   |                        |                       |    -  **VNI**: Set it as needed. In this example, **1** is used.                                                                                                                                                                                                                                                                                                  |
   |                        |                       |    -  **Packet Length**: Set it as needed. In this example, **96** is used.                                                                                                                                                                                                                                                                                       |
   |                        |                       |    -  **Mirror Session**: Enable it to mirror the traffic from the mirror source.                                                                                                                                                                                                                                                                                 |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       | -  **Associate Mirror Filter**: Set it as needed. In this example, **mirror-filter-01** is used.                                                                                                                                                                                                                                                                  |
   |                        |                       | -  **Associate Mirror Sources**: Set it as needed. In this example, the private IP address (192.168.0.230) of the network interface on **ECS-source** is used.                                                                                                                                                                                                    |
   |                        |                       | -  **Associate Mirror Target**                                                                                                                                                                                                                                                                                                                                    |
   |                        |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                        |                       |    -  **Type**: **Network interface**                                                                                                                                                                                                                                                                                                                             |
   |                        |                       |    -  Network interface: Set it as needed. In this example, the private IP address (10.0.1.97) of the network interface of **ECS-target** is used.                                                                                                                                                                                                                |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_mirror_24__en-us_topic_0000002052878369_en-us_topic_0285680794_table102261597217:

.. table:: **Table 2** Security group **Sg-X** rules

   +-----------+--------+------+-----------------+-------------------------------------------+---------------------------------------------------------------------------------------------+
   | Direction | Action | Type | Protocol & Port | Source/Destination                        | Description                                                                                 |
   +===========+========+======+=================+===========================================+=============================================================================================+
   | Inbound   | Allow  | IPv4 | TCP: 22         | Source: 0.0.0.0/0                         | Allows remote logins to Linux ECSs over SSH port 22.                                        |
   +-----------+--------+------+-----------------+-------------------------------------------+---------------------------------------------------------------------------------------------+
   | Inbound   | Allow  | IPv4 | TCP: 3389       | Source: 0.0.0.0/0                         | Allows remote logins to Windows ECSs over RDP port 3389.                                    |
   +-----------+--------+------+-----------------+-------------------------------------------+---------------------------------------------------------------------------------------------+
   | Inbound   | Allow  | IPv4 | All             | Source: current security group (**Sg-X**) | Allows the ECSs in this security group to communicate with each other using IPv4 addresses. |
   +-----------+--------+------+-----------------+-------------------------------------------+---------------------------------------------------------------------------------------------+
   | Inbound   | Allow  | IPv6 | All             | Source: current security group (**Sg-X**) | Allows the ECSs in this security group to communicate with each other using IPv6 addresses. |
   +-----------+--------+------+-----------------+-------------------------------------------+---------------------------------------------------------------------------------------------+
   | Outbound  | Allow  | IPv4 | All             | Destination: 0.0.0.0/0                    | Allows ECSs in this security group to access the external networks using IPv4 addresses.    |
   +-----------+--------+------+-----------------+-------------------------------------------+---------------------------------------------------------------------------------------------+
   | Outbound  | Allow  | IPv6 | All             | Destination: ::/0                         | Allows ECSs in this security group to access the external networks using IPv6 addresses.    |
   +-----------+--------+------+-----------------+-------------------------------------------+---------------------------------------------------------------------------------------------+

.. caution::

   If the source of an inbound rule is set to 0.0.0.0/0, all external IP addresses are allowed to remotely log in to your cloud server. Exposing port 22 or 3389 to the public network will leave your instances vulnerable to network risks. To address this issue, set the source to a known IP address, for example, the IP address of your local PC.

.. _vpc_mirror_24__en-us_topic_0000002093274237_en-us_topic_0285680794_table164981355467:

.. table:: **Table 3** Rules for security groups **Sg-A** and **Sg-X** to allow traffic between ECSs

   +----------------+-----------+---------+---------+-----------------+------------------------------------------------------------+--------------------------------------------------------------------------+
   | Security Group | Direction | Action  | Type    | Protocol & Port | Source                                                     | Description                                                              |
   +================+===========+=========+=========+=================+============================================================+==========================================================================+
   | Sg-A           | Inbound   | Allow   | IPv4    | TCP: 1234       | The security group that **ECS-test-A** is associated with: | Allows TCP packets from **ECS-test-A** to **ECS-source** over port 1234. |
   |                |           |         |         |                 |                                                            |                                                                          |
   |                |           |         |         |                 | **Sg-X**                                                   |                                                                          |
   +----------------+-----------+---------+---------+-----------------+------------------------------------------------------------+--------------------------------------------------------------------------+
   | Sg-X           | Inbound   | Allow   | IPv4    | TCP: All ports  | The security group that **ECS-source** is associated with: | Allows TCP packets from **ECS-source** to **ECS-test-A** over all ports. |
   |                |           |         |         |                 |                                                            |                                                                          |
   |                |           |         |         |                 | **Sg-A**                                                   |                                                                          |
   +----------------+-----------+---------+---------+-----------------+------------------------------------------------------------+--------------------------------------------------------------------------+

.. _vpc_mirror_24__en-us_topic_0000002093274237_table686503122416:

.. table:: **Table 4** Security group **Sg-B** rule

   +-----------+-----------+-----------+-----------------+---------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | Direction | Action    | Type      | Protocol & Port | Source                                                  | Description                                                                                |
   +===========+===========+===========+=================+=========================================================+============================================================================================+
   | Inbound   | Allow     | IPv4      | UDP: 4789       | The private IP address of mirror source **ECS-source**: | Allows UDP packets encapsulated by **ECS-source** to access **ECS-target** over port 4789. |
   |           |           |           |                 |                                                         |                                                                                            |
   |           |           |           |                 | 192.168.0.230/32                                        |                                                                                            |
   +-----------+-----------+-----------+-----------------+---------------------------------------------------------+--------------------------------------------------------------------------------------------+

.. _vpc_mirror_24__en-us_topic_0000002093274237_table139835561968:

.. table:: **Table 5** Routes for the VPC peering connection

   +-------------+---------------------+-------------------+----------------------------------------+-----------------------------------+
   | VPC         | Route Table         | Destination       | Next Hop                               | Description                       |
   +=============+=====================+===================+========================================+===================================+
   | VPC-A       | rtb-VPC-A (default) | VPC-B CIDR block: | VPC peering connection: **Peering-AB** | Route from **VPC-A** to **VPC-B** |
   |             |                     |                   |                                        |                                   |
   |             |                     | 10.0.0.0/16       |                                        |                                   |
   +-------------+---------------------+-------------------+----------------------------------------+-----------------------------------+
   | VPC-B       | rtb-VPC-B (default) | VPC-A CIDR block: | VPC peering connection: **Peering-AB** | Route from **VPC-B** to **VPC-A** |
   |             |                     |                   |                                        |                                   |
   |             |                     | 192.168.0.0/16    |                                        |                                   |
   +-------------+---------------------+-------------------+----------------------------------------+-----------------------------------+

.. _vpc_mirror_24__en-us_topic_0000002093274237_table42954412446:

.. table:: **Table 6** Inbound and outbound rules of the mirror filter

   +-----------+----------+----------+--------+-------+-------------------------------------------+-------------------+-------------------------------------------+-------------------------+
   | Direction | Priority | Protocol | Action | Type  | Source                                    | Source Port Range | Destination                               | Destination Port Range  |
   +===========+==========+==========+========+=======+===========================================+===================+===========================================+=========================+
   | Inbound   | 1        | TCP      | Reject | IPv4  | **VPC-A** CIDR block:                     | All               | **VPC-A** CIDR block:                     | All                     |
   |           |          |          |        |       |                                           |                   |                                           |                         |
   |           |          |          |        |       | 192.168.0.0/16                            |                   | 192.168.0.0/16                            |                         |
   +-----------+----------+----------+--------+-------+-------------------------------------------+-------------------+-------------------------------------------+-------------------------+
   | Inbound   | 2        | TCP      | Accept | IPv4  | **VPC-B** CIDR block:                     | All               | The private IP address of **ECS-source**: | Port of **ECS-source**: |
   |           |          |          |        |       |                                           |                   |                                           |                         |
   |           |          |          |        |       | 10.0.0.0/16                               |                   | 192.168.0.230/32                          | 1234-1234               |
   +-----------+----------+----------+--------+-------+-------------------------------------------+-------------------+-------------------------------------------+-------------------------+
   | Outbound  | 1        | TCP      | Reject | IPv4  | **VPC-A** CIDR block:                     | All               | **VPC-A** CIDR block:                     | All                     |
   |           |          |          |        |       |                                           |                   |                                           |                         |
   |           |          |          |        |       | 192.168.0.0/16                            |                   | 192.168.0.0/16                            |                         |
   +-----------+----------+----------+--------+-------+-------------------------------------------+-------------------+-------------------------------------------+-------------------------+
   | Outbound  | 2        | TCP      | Accept | IPv4  | The private IP address of **ECS-source**: | All               | **VPC-B** CIDR block:                     | Port of **ECS-test-B**: |
   |           |          |          |        |       |                                           |                   |                                           |                         |
   |           |          |          |        |       | 192.168.0.230/32                          |                   | 10.0.0.0/16                               | 1234-1234               |
   +-----------+----------+----------+--------+-------+-------------------------------------------+-------------------+-------------------------------------------+-------------------------+

Procedure
---------

:ref:`Figure 2 <vpc_mirror_24__en-us_topic_0000002093274237_fig142558410317>` shows the procedure required to mirror the inbound and outbound TCP traffic between a mirror source (network interface) and a given instance to a mirror target (network interface) in a different VPC from the mirror source.

.. _vpc_mirror_24__en-us_topic_0000002093274237_fig142558410317:

.. figure:: /_static/images/en-us_image_0000002581268350.png
   :alt: **Figure 2** Mirroring inbound and outbound TCP traffic to a mirror target in a different VPC

   **Figure 2** Mirroring inbound and outbound TCP traffic to a mirror target in a different VPC

Step 1: Create Cloud Resources
------------------------------

#. Create two VPCs, each with a subnet.

   For details, see :ref:`Creating a VPC with a Subnet <en-us_topic_0013935842>`.

#. Create four ECSs.

   For details, see `Creating an ECS <https://docs.otc.t-systems.com/elastic-cloud-server/umn/getting_started/creating_an_ecs/index.html#en-us-topic-0021831611>`__.

#. Assign an EIP.

   For details, see :ref:`Assigning an EIP <en-us_topic_0013748738>`.

Step 2: Create a VPC Peering Connection
---------------------------------------

Create a VPC peering connection to connect **VPC-A** and **VPC-B** by referring to :ref:`Creating a VPC Peering Connection to Connect Two VPCs in the Same Account <en-us_topic_0046655037>`.

Add forward and return routes to the route tables of **VPC-A** and **VPC-B** so that the two VPCs can communicate with each other. For details, see :ref:`Table 5 <vpc_mirror_24__en-us_topic_0000002093274237_table139835561968>`.

Step 3: Create a Mirror Filter and a Mirror Session
---------------------------------------------------

#. Create a mirror filter.

   For details, see :ref:`Creating a Mirror Filter <vpc_mirror_04>`.

#. Create a mirror session, and associate the mirror filter, mirror source, and mirror target with this mirror session.

   For details, see :ref:`Creating a Mirror Session <vpc_mirror_12>`.

Step 4: Install Netcat (nc) to Simulate Traffic
-----------------------------------------------

The nc utility reads and writes data across network connections using TCP or UDP. It is usually used to test ports for accessibility. You need to install nc on **ECS-source**, **ECS-test-A**, and **ECS-test-B**.

#. Install nc on **ECS-source**.

   a. .. _vpc_mirror_24__en-us_topic_0000002093274237_en-us_topic_0000002015687352_en-us_topic_0285680794_li3716337101011:

      Bind the EIP to **ECS-source** to connect to the Internet for downloading the nc utility.

   b. Remotely log in to **ECS-source**.

   c. Run the following commands in sequence to install nc:

      **sudo yum update**

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-source ~]# sudo yum update
         HCE 2.0 base                                                                                                                                                 55 MB/s | 6.1 MB     00:00
         HCE 2.0 updates                                                                                                                                              98 MB/s |  14 MB     00:00
         Last metadata expiration check: 0:00:01 ago on Tue 10 Sep 2024 05:54:28 PM CST.
         Dependencies resolved.
         Nothing to do.
         Complete!

      **sudo yum install nc**

      If information similar to the following is displayed, enter **y** as prompted and press **Enter**:

      .. code-block:: console

         [root@ecs-source ~]# sudo yum install nc
         Last metadata expiration check: 0:00:12 ago on Tue 10 Sep 2024 05:54:28 PM CST.
         Dependencies resolved.
         ...
         Install  2 Packages

         Total download size: 6.1 M
         Installed size: 25 M
         Is this ok [y/N]: y
         Downloading Packages:
         ...
         Importing GPG key 0xA8DEF926:
          Userid     : "XXX"
          Fingerprint: C1BA 9CD4 9D03 A206 E241 F176 28DA 5B77 A8DE F926
          From       : http://.../XX/2.0/updates/RPM-GPG-KEY-HCE-2
         Is this ok [y/N]: y
         ...
         Installed:
           libssh2-1.10.0-2.r10.hce2.x86_64                                                               nmap-2:7.92-2.r4.hce2.x86_64

         Complete!

   d. .. _vpc_mirror_24__en-us_topic_0000002093274237_en-us_topic_0000002015687352_li9477162552613:

      Unbind the EIP from **ECS-source** after nc is installed.

#. Repeat :ref:`1.a <vpc_mirror_24__en-us_topic_0000002093274237_en-us_topic_0000002015687352_en-us_topic_0285680794_li3716337101011>` to :ref:`1.d <vpc_mirror_24__en-us_topic_0000002093274237_en-us_topic_0000002015687352_li9477162552613>` on **ECS-test-A**.
#. Repeat :ref:`1.a <vpc_mirror_24__en-us_topic_0000002093274237_en-us_topic_0000002015687352_en-us_topic_0285680794_li3716337101011>` to :ref:`1.d <vpc_mirror_24__en-us_topic_0000002093274237_en-us_topic_0000002015687352_li9477162552613>` on **ECS-test-B**.
#. Release the EIP.

Step 5: Check Whether the Mirror Session Rejects the Traffic Between **ECS-source** and **ECS-test-A**
------------------------------------------------------------------------------------------------------

Check whether the mirror session rejects the traffic between **ECS-source** and **ECS-test-A**.

#. Establish a TCP connection between **ECS-source** and **ECS-test-A**.

   Use **ECS-source** to send TCP packets to **ECS-test-A** and check whether **ECS-test-A** can receive the packets.

   a. Run the following command on **ECS-source** to listen on port 1234:

      **nc -l** *<listening-port-of-mirror-source-ECS-source>*

      Example command:

      **nc -l 1234**

      If the command output is empty, the port is opened for listening.

   b. Run the following command on **ECS-test-A** to establish a TCP connection between **ECS-source** and **ECS-test-A**:

      **nc** *<private-IP-address-of-mirror-source-ECS-source> <listening-port-of-mirror-source-ECS-source>*

      Example command:

      **nc 192.168.0.230 1234**

      If the command output is empty, the TCP connection has been established.

   c. Enter any information (for example, **hello**) on **ECS-source** and press **Enter** to check whether requests can be sent over the TCP connection.

      .. code-block:: console

         [root@ecs-source ~]# nc -l 1234
         hello

   d. Check whether **ECS-test-A** can receive "hello" from **ECS-source**.

      If information similar to the following is displayed, the information can be received and the TCP connection is successfully established.

      .. code-block:: console

         [root@ecs-test-a ~]# nc 192.168.0.230 1234
         hello

#. Check whether the outbound TCP packet from **ECS-source** to **ECS-test-A** can be mirrored to **ECS-target**.

   When **ECS-source** sends a TCP packet to **ECS-test-A**, run **tcpdump** to check whether **ECS-target** can receive the packet. If **ECS-target** does not receive the packet, the mirror session rejects the outbound TCP traffic.

   a. Remotely log in to **ECS-target**.

   b. Run the following command on **ECS-target** to view its network interface name:

      **ifconfig**

      Information similar to the following is displayed. In this example, the network interface of the mirror target is **eth0**.

      .. code-block:: console

         [root@ecs-target ~]# ifconfig
         eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
                 inet 10.0.1.97  netmask 255.255.255.0  broadcast 10.0.1.255
                 inet6 fe80::f816:3eff:fea0:a101  prefixlen 64  scopeid 0x20<link>
                 ether fa:16:3e:a0:a1:01  txqueuelen 1000  (Ethernet)
                 RX packets 103445  bytes 119352826 (113.8 MiB)
                 RX errors 0  dropped 0  overruns 0  frame 0
                 TX packets 34118  bytes 15630293 (14.9 MiB)
                 TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
         ...

   c. Run the following command on **ECS-target** to check whether it can receive the packet:

      **tcpdump -i** *<network-interface-name-of-the-mirror-target>* **udp port 4789 -nne**

      Example command:

      **tcpdump -i eth0 udp port 4789 -nne**

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-target ~]# tcpdump -i eth0 udp port 4789 -nne
         dropped privs to tcpdump
         tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
         listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes

   d. Enter any information (for example, **to testa**) on **ECS-source** and press **Enter** to send a TCP packet to **ECS-test-A**.

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-source ~]# nc -l 1234
         hello
         to testa

   e. Check whether **ECS-test-A** can receive "to testa" from **ECS-source**.

      If information similar to the following is displayed, **ECS-test-A** can receive "to testa" from **ECS-source**.

      .. code-block:: console

         [root@ecs-test-a ~]# nc 192.168.0.230 1234
         hello
         to testa

   f. Check whether **ECS-target** can receive the packet.

      If the information similar to the following is displayed, the packet containing "to testa" from **ECS-source** is not sent to **ECS-test-A** after running **tcpdump**. This means the reject rule works.

      .. code-block:: console

         [root@ecs-target ~]# tcpdump -i eth0 udp port 4789 -nne
         dropped privs to tcpdump
         tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
         listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes

#. Check whether the inbound TCP packets from **ECS-test-A** to **ECS-source** can be mirrored to **ECS-target**.

   When **ECS-test-A** sends a TCP packet to **ECS-source**, run **tcpdump** to check whether **ECS-target** can receive the packet. If **ECS-target** does not receive the packet, the mirror session rejects the inbound TCP traffic.

   a. Enter any information (for example, **testa to source**) on **ECS-test-A** and press **Enter** to send a TCP packet to **ECS-source**.

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-test-a ~]# nc 192.168.0.230 1234
         hello
         to testa
         testa to source

   b. Check whether **ECS-source** can receive "testa to source" from **ECS-test-A**.

      If information similar to the following is displayed, **ECS-source** can receive "testa to source" from **ECS-test-A**.

      .. code-block:: console

         [root@ecs-source ~]# nc -l 1234
         hello
         to testa
         testa to source

   c. Check whether **ECS-target** can receive the packet.

      If the information similar to the following is displayed, the packet containing "testa to source" from **ECS-test-A** is not sent to **ECS-source** after running **tcpdump**. This means the reject rule works.

      .. code-block:: console

         [root@ecs-target ~]# tcpdump -i eth0 udp port 4789 -nne
         dropped privs to tcpdump
         tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
         listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes

Step 6: Check Whether the Mirror Session Accepts the Traffic Between **ECS-source** and **ECS-test-B**
------------------------------------------------------------------------------------------------------

Check whether the mirror session accepts the traffic between **ECS-source** and **ECS-test-B**.

#. Establish a TCP connection between **ECS-source** and **ECS-test-B**.

   Use **ECS-test-B** to send TCP packets to **ECS-source** and check whether **ECS-source** can receive the packets.

   a. Run the following command on **ECS-test-B** to listen on port 1234:

      **nc -l** *<listening-port-of-ECS-test-B>*

      Example command:

      **nc -l 1234**

      If the command output is empty, the port is opened for listening.

   b. Run the following command on **ECS-source** to establish a TCP connection between **ECS-source** and **ECS-test-B**:

      **nc** *<private-IP-address-of-ECS-test-B> <listening-port-of-ECS-test-B>*

      Example command:

      **nc 10.0.1.156 1234**

      If the command output is empty, the TCP connection has been established.

   c. Enter any information (for example, **hello**) on **ECS-test-B** and press **Enter** to check whether requests can be sent over the TCP connection.

      .. code-block:: console

         [root@ecs-test-b ~]# nc -l 1234
         hello

   d. Check whether **ECS-source** can receive "hello" from **ECS-test-B**.

      If information similar to the following is displayed, the information can be received and the TCP connection is successfully established.

      .. code-block:: console

         [root@ecs-source ~]# nc 10.0.1.156 1234
         hello

2. Check whether the outbound TCP packet from **ECS-source** to **ECS-test-B** can be mirrored to **ECS-target**.

   When **ECS-source** sends a TCP packet to **ECS-test-B**, run **tcpdump** to check whether **ECS-target** can receive the packet. If **ECS-target** receives the packet, the mirror session accepts the outbound TCP traffic.

   a. Remotely log in to **ECS-target**.

   b. Run the following command on **ECS-target** to view its network interface name:

      **ifconfig**

      Information similar to the following is displayed. In this example, the network interface of the mirror target is **eth0**.

      .. code-block:: console

         [root@ecs-target ~]# ifconfig
         eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
                 inet 10.0.1.97  netmask 255.255.255.0  broadcast 10.0.1.255
                 inet6 fe80::f816:3eff:fea0:a101  prefixlen 64  scopeid 0x20<link>
                 ether fa:16:3e:a0:a1:01  txqueuelen 1000  (Ethernet)
                 RX packets 103445  bytes 119352826 (113.8 MiB)
                 RX errors 0  dropped 0  overruns 0  frame 0
                 TX packets 34118  bytes 15630293 (14.9 MiB)
                 TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
         ...

   c. Run the following command on **ECS-target** to check whether it can receive packets:

      **tcpdump -i** *<network-interface-name-of-the-mirror-target>* **udp port 4789 -nne**

      Example command:

      **tcpdump -i eth0 udp port 4789 -nne**

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-target ~]# tcpdump -i eth0 udp port 4789 -nne
         dropped privs to tcpdump
         tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
         listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes

   d. Enter any information (for example, **to testb**) on **ECS-source** and press **Enter** to send a TCP packet to **ECS-test-B**.

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-source ~]# nc 10.0.1.156 1234
         hello
         to testb

   e. Check whether **ECS-test-B** can receive "to testb" from **ECS-source**.

      If information similar to the following is displayed, **ECS-test-B** can receive "to testb" from **ECS-source**.

      .. code-block:: console

         [root@ecs-test-b ~]# nc -l 1234
         hello
         to testb

   f. Check whether **ECS-target** can receive the packet.

      If the information similar to the following is displayed, the packet containing "to testb" (time: **17:28:48.772658**) from **ECS-source** is sent to **ECS-test-B** after running **tcpdump**. This means the accept rule works. In this packet, **vni 1** is the identifier of **mirror-session-01**, indicating that **ECS-target** can receive the packet through this mirror session. The packet content has two parts: a VXLAN packet encapsulated by traffic mirroring and the original packet. For details, see :ref:`Table 6 <vpc_mirror_22__en-us_topic_0000002015687352_table223316435223>`.

      .. code-block:: console

         [root@ecs-target ~]# tcpdump -i eth0 udp port 4789 -nne
         dropped privs to tcpdump
         tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
         listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
         17:28:48.772658 fa:16:3e:6e:42:80 > fa:16:3e:a0:a1:01, ethertype IPv4 (0x0800), length 125: 192.168.0.230.32821 > 10.0.1.97.4789: VXLAN, flags [I] (0x08), vni 1
         fa:16:3e:7e:d6:bc > fa:16:3e:d1:6b:5d, ethertype IPv4 (0x0800), length 75: 192.168.0.230.44906 > 10.0.1.156.1234: Flags [P.], seq 935460393:935460402, ack 4279496885, win 502, options [nop,nop,TS val 1414482596 ecr 3323401462], length 9

3. Check whether the inbound TCP packets from **ECS-test-B** to **ECS-source** can be mirrored to **ECS-target**.

   When **ECS-test-B** sends a TCP packet to **ECS-source**, run **tcpdump** to check whether **ECS-target** can receive the packet. If **ECS-target** receives the packet, the mirror session accepts the inbound TCP traffic.

   a. Enter any information (for example, **testb to source**) on **ECS-test-B** and press **Enter** to send a TCP packet to **ECS-source**.

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-test-b ~]# nc -l 1234
         hello
         to testb
         testb to source

   b. Check whether **ECS-source** can receive "testb to source" from **ECS-test-B**.

      If information similar to the following is displayed, **ECS-source** can receive "testb to source" from **ECS-test-B**.

      .. code-block:: console

         [root@ecs-source ~]# nc 10.0.1.156 1234
         hello
         to testb
         testb to source

   c. Check whether **ECS-target** can receive the packet.

      If the information similar to the following is displayed, the packet containing "testb to source" (time: **17:30:26.193420**) from **ECS-test-B** is sent to **ECS-source** after running **tcpdump**. This means the accept rule works. In this packet, **vni 1** is the identifier of **mirror-session-01**, indicating that **ECS-target** can receive the packet through this mirror session. The packet content has two parts: a VXLAN packet encapsulated by traffic mirroring and the original packet. For details, see :ref:`Table 6 <vpc_mirror_22__en-us_topic_0000002015687352_table223316435223>`.

      .. code-block:: console

         [root@ecs-target ~]# tcpdump -i eth0 udp port 4789 -nne
         dropped privs to tcpdump
         tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
         listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
         17:28:48.772658 fa:16:3e:6e:42:80 > fa:16:3e:a0:a1:01, ethertype IPv4 (0x0800), length 125: 192.168.0.230.32821 > 10.0.1.97.4789: VXLAN, flags [I] (0x08), vni 1
         fa:16:3e:7e:d6:bc > fa:16:3e:d1:6b:5d, ethertype IPv4 (0x0800), length 75: 192.168.0.230.44906 > 10.0.1.156.1234: Flags [P.], seq 935460393:935460402, ack 4279496885, win 502, options [nop,nop,TS val 1414482596 ecr 3323401462], length 9
         17:30:26.193420 fa:16:3e:6e:42:80 > fa:16:3e:a0:a1:01, ethertype IPv4 (0x0800), length 116: 192.168.0.230.32821 > 10.0.1.97.4789: VXLAN, flags [I] (0x08), vni 1
         fa:16:3e:7e:d6:bc > fa:16:3e:d1:6b:5d, ethertype IPv4 (0x0800), length 66: 192.168.0.230.44906 > 10.0.1.156.1234: Flags [.], ack 17, win 502, options [nop,nop,TS val 1414580016 ecr 3323563970], length 0
