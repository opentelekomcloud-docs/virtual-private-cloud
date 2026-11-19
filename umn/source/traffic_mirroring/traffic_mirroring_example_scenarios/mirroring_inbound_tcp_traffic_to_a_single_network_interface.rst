:original_name: vpc_mirror_22.html

.. _vpc_mirror_22:

Mirroring Inbound TCP Traffic to a Single Network Interface
===========================================================

Solution Architecture
---------------------

To mirror inbound TCP traffic from a mirror source (network interface) to a single mirror target (network interface), you can refer to the configurations in this section. In :ref:`Figure 1 <vpc_mirror_22__en-us_topic_0000002015687352_fig18617152242120>`, when **ECS-test** accesses **ECS-source**, you can create a mirror session to mirror inbound TCP traffic on **ECS-source** to **ECS-target**.

-  Set the mirror source to **Network-interface-s** on **ECS-source**. The inbound TCP traffic on this network interface needs to be mirrored.
-  Set the mirror target to **Network-interface-t** on **ECS-target**. The inbound TCP traffic on **network-interface-s** is mirrored to **network-interface-t**.
-  Associate the mirror filter that has a rule for accepting inbound TCP traffic with the mirror session.

.. _vpc_mirror_22__en-us_topic_0000002015687352_fig18617152242120:

.. figure:: /_static/images/en-us_image_0000002611828099.png
   :alt: **Figure 1** Mirroring inbound TCP traffic

   **Figure 1** Mirroring inbound TCP traffic

Notes and Constraints
---------------------

See :ref:`Notes and Constraints <vpc_mirror_02__en-us_topic_0000001651378981_section1412134042913>`.

Resource Planning
-----------------

In this example, the VPC, subnet, EIP, and ECSs must be in the same region but can be in different AZs.

.. note::

   The following resource details are only for your reference. You can modify them if needed.

.. table:: **Table 1** Resource details for mirroring inbound TCP traffic

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Resource              | Quantity              | Description                                                                                                                                                                                                                                                                                                                                                       |
   +=======================+=======================+===================================================================================================================================================================================================================================================================================================================================================================+
   | VPC and subnet        | VPC: 1                | -  **Name**: Set it as needed. In this example, **VPC-A** is used.                                                                                                                                                                                                                                                                                                |
   |                       |                       | -  **VPC IPv4 CIDR Block**: Set it as needed. In this example, **192.168.0.0/16** is used.                                                                                                                                                                                                                                                                        |
   |                       | Subnet: 1             | -  **Subnet Name**: Set it as needed. In this example, **Subnet-A01** is used.                                                                                                                                                                                                                                                                                    |
   |                       |                       | -  **Subnet IPv4 CIDR Block**: Set it as needed. In this example, **192.168.0.0/24** is used.                                                                                                                                                                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ECS                   | 3                     | Configure the ECSs as follows:                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **ECS Name**: Set it as needed. In this example, the ECSs are named **ECS-source**, **ECS-target**, and **ECS-test**.                                                                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **ECS Type**: In this example, the type of **ECS-source** is **General computing-plus c7t**. Currently, only network interfaces of ECSs of certain types can be used as mirror sources. For details, see :ref:`Notes and Constraints <vpc_mirror_02__en-us_topic_0000001651378981_section1412134042913>`. There are no constraints on the types of other ECSs. |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **Image**: Set it as needed. In this example, public image **EulerOS 2.0 Standard 64 bit** is used.                                                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **System Disk**: In this example, a general-purpose SSD disk of 40 GiB is used.                                                                                                                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **Data Disk**: Set it as needed. In this example, no data disk is used.                                                                                                                                                                                                                                                                                        |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **Network**                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |    -  **VPC**: Select a VPC. In this example, **VPC-A** is used.                                                                                                                                                                                                                                                                                                  |
   |                       |                       |    -  **Subnet**: Select a subnet. In this example, **Subnet-A01** is used.                                                                                                                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **Security Group**: In this example, the three ECSs are associated with the same security group (**Sg-X**). Ensure that all rules in :ref:`Table 2 <vpc_mirror_22__en-us_topic_0000002015687352_en-us_topic_0285680794_table102261597217>` are added.                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |    If the ECSs are associated with different security groups, you also need to add additional rules.                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |    -  If **ECS-test** is associated with **Sg-X** and **ECS-source** is associated with **Sg-A**, add the rule in :ref:`Table 3 <vpc_mirror_22__en-us_topic_0000002015687352_en-us_topic_0285680794_table164981355467>` to **Sg-A** to allow traffic from **ECS-test**.                                                                                           |
   |                       |                       |    -  If **ECS-source** is associated with **Sg-A** but **ECS-target** is associated with **Sg-B**, add the rule in :ref:`Table 4 <vpc_mirror_22__en-us_topic_0000002015687352_table23263593125>` to **Sg-B** to allow UDP packets encapsulated by the mirror source to access the mirror target over port 4789.                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **EIP**: Select **Not required**.                                                                                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  Private IP address: In this example, use **192.168.0.230** for **ECS-source**, **192.168.0.164** for **ECS-target**, and **192.168.0.161** for **ECS-test**.                                                                                                                                                                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EIP                   | 1                     | -  **Billing Mode**: Set it as needed. In this example, **Pay-per-use** is used.                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **EIP Name**: Set it as needed. In this example, **EIP-A** is used.                                                                                                                                                                                                                                                                                            |
   |                       |                       | -  EIP: The EIP is randomly assigned. In this example, **124.X.X.187** is used.                                                                                                                                                                                                                                                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mirror filter         | 1                     | -  **Name**: Set it as needed. In this example, **mirror-filter-A** is used.                                                                                                                                                                                                                                                                                      |
   |                       |                       | -  Inbound rule: Add the inbound rule in :ref:`Table 5 <vpc_mirror_22__en-us_topic_0000002015687352_table42954412446>`. This rule allows TCP packets from **ECS-test** to **ECS-source** over port 1234 to be mirrored.                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mirror session        | 1                     | -  **Basic Information**                                                                                                                                                                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |    -  **Name**: Set it as needed. In this example, **mirror-session-A** is used.                                                                                                                                                                                                                                                                                  |
   |                       |                       |    -  **Priority**: Set it as needed. In this example, **1** is used.                                                                                                                                                                                                                                                                                             |
   |                       |                       |    -  **VNI**: Set it as needed. In this example, **1** is used.                                                                                                                                                                                                                                                                                                  |
   |                       |                       |    -  **Packet Length**: Set it as needed. In this example, **96** is used.                                                                                                                                                                                                                                                                                       |
   |                       |                       |    -  **Mirror Session**: Enable it to mirror the traffic from the mirror source.                                                                                                                                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **Associate Mirror Filter**: Set it as needed. In this example, **mirror-filter-A** is used.                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **Associate Mirror Sources**: Set it as needed. In this example, the private IP address (192.168.0.230) of the network interface on **ECS-source** is used.                                                                                                                                                                                                    |
   |                       |                       | -  **Associate Mirror Target**                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |    -  **Type**: **Network interface**                                                                                                                                                                                                                                                                                                                             |
   |                       |                       |    -  Network interface: Set it as needed. In this example, the private IP address (192.168.0.164) of the network interface on **ECS-target** is used.                                                                                                                                                                                                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_mirror_22__en-us_topic_0000002015687352_en-us_topic_0285680794_table102261597217:

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

.. _vpc_mirror_22__en-us_topic_0000002015687352_en-us_topic_0285680794_table164981355467:

.. table:: **Table 3** Security group **Sg-A** rules

   +-----------+-----------+-----------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | Direction | Action    | Type      | Protocol & Port | Source                                                                                                                          | Description                                                            |
   +===========+===========+===========+=================+=================================================================================================================================+========================================================================+
   | Inbound   | Allow     | IPv4      | TCP: 1234       | Private IP address of the ECS that accesses the mirror source. In this example, the private IP address of **ECS-test** is used: | Allows TCP packets from **ECS-test** to **ECS-source** over port 1234. |
   |           |           |           |                 |                                                                                                                                 |                                                                        |
   |           |           |           |                 | 192.168.0.161/32                                                                                                                |                                                                        |
   +-----------+-----------+-----------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+

.. _vpc_mirror_22__en-us_topic_0000002015687352_table23263593125:

.. table:: **Table 4** Security group **Sg-B** rules

   +-----------+-----------+-----------+-----------------+---------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | Direction | Action    | Type      | Protocol & Port | Source                                                  | Description                                                                                |
   +===========+===========+===========+=================+=========================================================+============================================================================================+
   | Inbound   | Allow     | IPv4      | UDP: 4789       | The private IP address of mirror source **ECS-source**: | Allows UDP packets encapsulated by **ECS-source** to access **ECS-target** over port 4789. |
   |           |           |           |                 |                                                         |                                                                                            |
   |           |           |           |                 | 192.168.0.230/32                                        |                                                                                            |
   +-----------+-----------+-----------+-----------------+---------------------------------------------------------+--------------------------------------------------------------------------------------------+

.. _vpc_mirror_22__en-us_topic_0000002015687352_table42954412446:

.. table:: **Table 5** Inbound rules of the mirror filter

   +-----------+----------+----------+--------+-------+-----------------------------------------+-------------------+-------------------------------------------+-------------------------+
   | Direction | Priority | Protocol | Action | Type  | Source                                  | Source Port Range | Destination                               | Destination Port Range  |
   +===========+==========+==========+========+=======+=========================================+===================+===========================================+=========================+
   | Inbound   | 1        | TCP      | Accept | IPv4  | The private IP address of **ECS-test**: | All               | The private IP address of **ECS-source**: | Port of **ECS-source**: |
   |           |          |          |        |       |                                         |                   |                                           |                         |
   |           |          |          |        |       | 192.168.0.161/32                        |                   | 192.168.0.230/32                          | 1234-1234               |
   +-----------+----------+----------+--------+-------+-----------------------------------------+-------------------+-------------------------------------------+-------------------------+

Procedure
---------

:ref:`Figure 2 <vpc_mirror_22__en-us_topic_0000002015687352_en-us_topic_0285680794_en-us_topic_0000001154868962_fig10285152624918>` shows the procedure required to mirror inbound TCP traffic to a single network interface.

.. _vpc_mirror_22__en-us_topic_0000002015687352_en-us_topic_0285680794_en-us_topic_0000001154868962_fig10285152624918:

.. figure:: /_static/images/en-us_image_0000002581268344.png
   :alt: **Figure 2** Mirroring inbound TCP traffic

   **Figure 2** Mirroring inbound TCP traffic

Step 1: Create Cloud Resources
------------------------------

#. Create a VPC with a subnet.

   For details, see :ref:`Creating a VPC with a Subnet <en-us_topic_0013935842>`.

#. Create three ECSs.

   For details, see `Creating an ECS <https://docs.otc.t-systems.com/elastic-cloud-server/umn/getting_started/creating_an_ecs/index.html#en-us-topic-0021831611>`__.

#. Assign an EIP.

   For details, see :ref:`Assigning an EIP <en-us_topic_0013748738>`.

Step 2: Create a Mirror Filter and a Mirror Session
---------------------------------------------------

#. Create a mirror filter.

   For details, see :ref:`Creating a Mirror Filter <vpc_mirror_04>`.

#. Create a mirror session, and associate the mirror filter, mirror source, and mirror target with this mirror session.

   For details, see :ref:`Creating a Mirror Session <vpc_mirror_12>`.

Step 3: Install Netcat (nc) to Simulate Traffic
-----------------------------------------------

The nc utility reads and writes data across network connections using TCP or UDP. It is usually used to test ports for accessibility. You need to install nc on both **ECS-source** and **ECS-test**.

#. Install nc on **ECS-source**.

   a. .. _vpc_mirror_22__en-us_topic_0000002015687352_en-us_topic_0285680794_li3716337101011:

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

   d. .. _vpc_mirror_22__en-us_topic_0000002015687352_li9477162552613:

      Unbind the EIP from **ECS-source** after nc is installed.

#. Repeat :ref:`1.a <vpc_mirror_22__en-us_topic_0000002015687352_en-us_topic_0285680794_li3716337101011>` to :ref:`1.d <vpc_mirror_22__en-us_topic_0000002015687352_li9477162552613>` on **ECS-test**.
#. Release the EIP.

Step 3: Check Whether the Mirror Session Works
----------------------------------------------

#. Establish a TCP connection between **ECS-source** and **ECS-test**.

   Send TCP packets from **ECS-test** to **ECS-source** and check whether **ECS-source** can receive the packets.

   a. Run the following command on **ECS-source** to listen on port 1234:

      **nc -l** *<listening-port-of-mirror-source-ECS-source>*

      Example command:

      **nc -l 1234**

      If the command output is empty, the port is opened for listening.

   b. Run the following command on **ECS-test** to establish a TCP connection between **ECS-source** and **ECS-test**:

      **nc** *<private-IP-address-of-mirror-source-ECS-source> <listening-port-of-mirror-source-ECS-source>*

      Example command:

      **nc 192.168.0.230 1234**

      The command output is empty. Enter any information (for example, **hello**) on **ECS-test** and press **Enter** to check whether the TCP connection is successfully established.

      .. code-block:: console

         [root@ecs-test ~]# nc 192.168.0.230 1234
         hello

   c. Check whether **ECS-source** can receive information from **ECS-test**.

      If information similar to the following is displayed, the information can be received and the TCP connection is successfully established.

      .. code-block:: console

         [root@ecs-source ~]# nc -l 1234
         hello

#. Check whether the inbound packet on **ECS-source** can be mirrored to **ECS-target**.

   When **ECS-test** sends a TCP packet to **ECS-source**, run **tcpdump** to check whether **ECS-target** can receive the packet. If **ECS-target** receives the packet, the mirror session works.

   a. Remotely log in to **ECS-target**.

   b. Run the following command on **ECS-target** to view its network interface name:

      **ifconfig**

      Information similar to the following is displayed. In this example, the network interface of the mirror target is **eth0**.

      .. code-block:: console

         [root@ecs-target ~]# ifconfig
         eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
                 inet 192.168.0.164  netmask 255.255.255.0  broadcast 192.168.0.255
                 inet6 fe80::f816:3eff:fe7e:d67a  prefixlen 64  scopeid 0x20<link>
                 ether fa:16:3e:7e:d6:7a  txqueuelen 1000  (Ethernet)
                 RX packets 29043  bytes 32268398 (30.7 MiB)
                 RX errors 0  dropped 0  overruns 0  frame 0
                 TX packets 13811  bytes 3961116 (3.7 MiB)
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

   d. Enter any information (for example, **12345**) on **ECS-test** and press **Enter** to send a TCP packet to **ECS-source**.

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-test ~]# nc 192.168.0.230 1234
         hello
         12345

   e. Check whether **ECS-source** can receive information from **ECS-test**.

      If information similar to the following is displayed, **ECS-source** can receive information from **ECS-test**:

      .. code-block:: console

         [root@ecs-source ~]# nc -l 1234
         hello
         12345

   f. Check whether **ECS-target** can receive the packet.

      Information similar to the following is displayed. You can view the packet containing **12345** sent by **ECS-test** after running **tcpdump**. **vni 1** is the identifier of the mirror session, indicating that **ECS-target** can receive the packet through the mirror session. The packet content has two parts. For details, see :ref:`Table 6 <vpc_mirror_22__en-us_topic_0000002015687352_table223316435223>`.

      .. code-block:: console

         [root@ecs-target ~]# tcpdump -i eth0 udp port 4789 -nne
         dropped privs to tcpdump
         tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
         listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
         19:12:25.839624 fa:16:3e:d1:6b:5d > fa:16:3e:7e:d6:7a, ethertype IPv4 (0x0800), length 122: 192.168.0.230.32838 > 192.168.0.164.4789: VXLAN, flags [I] (0x08), vni 1
         fa:16:3e:7e:d6:77 > fa:16:3e:7e:d6:bc, ethertype IPv4 (0x0800), length 72: 192.168.0.161.38944 > 192.168.0.230.1234: Flags [P.], seq 2063075043:2063075049, ack 1116663338, win 502, options [nop,nop,TS val 969673134 ecr 605179348], length 6

      .. _vpc_mirror_22__en-us_topic_0000002015687352_table223316435223:

      .. table:: **Table 6** Packet description

         +----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
         | Packet Example                                                                                                                                                                                                                                     | Packet Description                                                                                                                      |
         +====================================================================================================================================================================================================================================================+=========================================================================================================================================+
         | .. code-block::                                                                                                                                                                                                                                    | VXLAN packet encapsulated by Traffic Mirroring. Packet format:                                                                          |
         |                                                                                                                                                                                                                                                    |                                                                                                                                         |
         |    19:12:25.839624 fa:16:3e:d1:6b:5d > fa:16:3e:7e:d6:7a, ethertype IPv4 (0x0800), length 122: 192.168.0.230.32838 > 192.168.0.164.4789: VXLAN, flags [I] (0x08), vni 1                                                                            | <Timestamp><SMacAddr><DMacAddr><EthernetType><Length><Sip><Sport><Dip><Dport><VXLAN Flags><VNI>                                         |
         |                                                                                                                                                                                                                                                    |                                                                                                                                         |
         |                                                                                                                                                                                                                                                    | Fields in the encapsulated packet:                                                                                                      |
         |                                                                                                                                                                                                                                                    |                                                                                                                                         |
         |                                                                                                                                                                                                                                                    | -  Timestamp: Time when a packet is obtained. It is generated by tcpdump.                                                               |
         |                                                                                                                                                                                                                                                    | -  SMacAddr: MAC address of the source instance of VXLAN packets. In this example, it is the MAC address of the gateway instance.       |
         |                                                                                                                                                                                                                                                    | -  DMacAddr: MAC address of the target instance of VXLAN packets. In this example, it is the MAC address of the mirror target instance. |
         |                                                                                                                                                                                                                                                    | -  EthernetType: indicates the Ethernet type of a packet. 0x0800 indicates that the protocol is IPv4.                                   |
         |                                                                                                                                                                                                                                                    | -  Length: packet length                                                                                                                |
         |                                                                                                                                                                                                                                                    | -  Sip: Mirror source address                                                                                                           |
         |                                                                                                                                                                                                                                                    | -  Sport: Mirror source port                                                                                                            |
         |                                                                                                                                                                                                                                                    | -  Dip: Mirror target address                                                                                                           |
         |                                                                                                                                                                                                                                                    | -  Dport: Mirror target port, which is usually port 4789 that receives VXLAN packets                                                    |
         |                                                                                                                                                                                                                                                    | -  VXLAN Flags: The value is usually 0x08, indicating a VXLAN packet.                                                                   |
         |                                                                                                                                                                                                                                                    | -  VNI: VXLAN network identifier of a mirror session                                                                                    |
         +----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
         | .. code-block::                                                                                                                                                                                                                                    | Original packet                                                                                                                         |
         |                                                                                                                                                                                                                                                    |                                                                                                                                         |
         |    fa:16:3e:7e:d6:77 > fa:16:3e:7e:d6:bc, ethertype IPv4 (0x0800), length 72: 192.168.0.161.38944 > 192.168.0.230.1234: Flags [P.], seq 2063075043:2063075049, ack 1116663338, win 502, options [nop,nop,TS val 969673134 ecr 605179348], length 6 | The original packet field is general network knowledge and is not described in detail herein.                                           |
         +----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
