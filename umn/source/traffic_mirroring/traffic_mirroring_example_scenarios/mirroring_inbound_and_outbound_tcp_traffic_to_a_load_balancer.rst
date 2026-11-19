:original_name: vpc_mirror_25.html

.. _vpc_mirror_25:

Mirroring Inbound and Outbound TCP Traffic to a Load Balancer
=============================================================

Solution Architecture
---------------------

To mirror inbound and outbound TCP traffic between a mirror source (network interface) and a given instance to a mirror target (load balancer), you can refer to the configurations in this section. In :ref:`Figure 1 <vpc_mirror_25__en-us_topic_0000002070193194_fig124891925379>`, to mirror the TCP traffic between **ECS-source** and **ECS-test** running in VPC **VPC-A** to load balancer **ELB-A**, one mirror session is needed. In this example, mirror session **mirror-session-01** is created. You can configure it as follows:

-  Set the mirror source to **network-interface-s** on **ECS-source**. The inbound and outbound TCP traffic on this network interface will be mirrored.
-  Set the mirror target to **ELB-A**. The inbound and outbound TCP traffic on **network-interface-s** will be mirrored to **ELB-A**. **ELB-A** will distribute the mirrored traffic across backend servers **ECS-target-01** and **ECS-target-02** based on the routing rules.
-  Create a mirror filter (**mirror-filter-01**) and add the following rules:

   -  Outbound rule: accepts TCP traffic from **ECS-source** to **ECS-test**.
   -  Inbound rule: accepts TCP traffic from **ECS-test** to **ECS-source**.

.. _vpc_mirror_25__en-us_topic_0000002070193194_fig124891925379:

.. figure:: /_static/images/en-us_image_0000002611828105.png
   :alt: **Figure 1** Mirroring inbound and outbound TCP traffic to a load balancer

   **Figure 1** Mirroring inbound and outbound TCP traffic to a load balancer

Notes and Constraints
---------------------

See :ref:`Notes and Constraints <vpc_mirror_02__en-us_topic_0000001651378981_section1412134042913>`.

Resource Planning
-----------------

In this example, the VPC, subnet, EIP, load balancer, and ECSs must be in the same region but can be in different AZs.

.. note::

   The following resource details are only for your reference. You can modify them if needed.

.. table:: **Table 1** Resource details for mirroring inbound and outbound TCP traffic to a load balancer

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Resource              | Quantity              | Description                                                                                                                                                                                                                                                                                                                                                       |
   +=======================+=======================+===================================================================================================================================================================================================================================================================================================================================================================+
   | VPC and subnet        | VPC: 1                | -  **Name**: Set it as needed. In this example, **VPC-A** is used.                                                                                                                                                                                                                                                                                                |
   |                       |                       | -  **VPC IPv4 CIDR Block**: Set it as needed. In this example, **192.168.0.0/16** is used.                                                                                                                                                                                                                                                                        |
   |                       | Subnet: 1             | -  **Subnet Name**: Set it as needed. In this example, **Subnet-A01** is used.                                                                                                                                                                                                                                                                                    |
   |                       |                       | -  **Subnet IPv4 CIDR Block**: Set it as needed. In this example, **192.168.0.0/24** is used.                                                                                                                                                                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ECS                   | 4                     | Configure the ECSs as follows:                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **ECS Name**: Set it as needed. In this example, the ECSs are named **ECS-source**, **ECS-target-01**, **ECS-target-02**, and **ECS-test**.                                                                                                                                                                                                                    |
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
   |                       |                       | -  **Security Group**: In this example, the four ECSs are associated with the same security group (**Sg-X**). Ensure that all rules in :ref:`Table 2 <vpc_mirror_25__en-us_topic_0000002052878369_en-us_topic_0285680794_table102261597217>` are added.                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |    If the ECSs are associated with different security groups, you also need to add additional rules.                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |    -  If **ECS-test** is associated with **Sg-X** but **ECS-source** is associated with **Sg-A**, add the rules in :ref:`Table 3 <vpc_mirror_25__en-us_topic_0000002070193194_en-us_topic_0285680794_table164981355467>` to **Sg-A** and **Sg-X** to allow traffic between **ECS-test** and **ECS-source**.                                                       |
   |                       |                       |    -  If **ECS-source** is associated with **Sg-A** and **ECS-target-01** is associated with **Sg-B**, add the rule in :ref:`Table 4 <vpc_mirror_25__en-us_topic_0000002070193194_table686503122416>` to **Sg-B** to allow UDP packets encapsulated by the mirror source to access the mirror target over port 4789. The same applies to **ECS-target-02**.       |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **EIP**: Select **Not required**.                                                                                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  Private IP address: In this example, use **192.168.0.230** for **ECS-source**, **192.168.0.6** for **ECS-target-01**, **192.168.0.12** for **ECS-target-02**, and **192.168.0.161** for **ECS-test**.                                                                                                                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EIP                   | 1                     | -  **Billing Mode**: Set it as needed. In this example, **Pay-per-use** is used.                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **EIP Name**: Set it as needed. In this example, **EIP-A** is used.                                                                                                                                                                                                                                                                                            |
   |                       |                       | -  EIP: The EIP is randomly assigned. In this example, **124.**\ *X.X*\ **.187** is used.                                                                                                                                                                                                                                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Load balancer         | 1                     | -  Target type: Only dedicated load balancers can be used as mirror targets.                                                                                                                                                                                                                                                                                      |
   |                       |                       | -  **Name**: Set it as needed. In this example, **ELB-A** is used.                                                                                                                                                                                                                                                                                                |
   |                       |                       | -  **Specifications**: Select **Network load balancing (TCP/UDP/TLS)** to forward UDP packets. Specifications vary by region. If TLS is not supported in your region, select **Network load balancing (TCP/UDP)**.                                                                                                                                                |
   |                       |                       | -  **Network Type**: The encapsulated mirrored packet uses the IPv4 UDP protocol. Select **Private IPv4 network** in this example.                                                                                                                                                                                                                                |
   |                       |                       | -  **VPC**: Set it as needed. In this example, select **VPC-A**.                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **Frontend Subnet**: Set it as needed. In this example, select **Subnet-A01**.                                                                                                                                                                                                                                                                                 |
   |                       |                       | -  IPv4 address: Set it as needed. In this example, select **Automatically assign IP address**.                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **Backend Subnet**: Set it as needed. In this example, select **Subnet of the load balancer**.                                                                                                                                                                                                                                                                 |
   |                       |                       | -  **IP as a Backend**: Disable it.                                                                                                                                                                                                                                                                                                                               |
   |                       |                       | -  **EIP**: Set it as needed. In this example, select **Not required**.                                                                                                                                                                                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Listener              | 1                     | -  Configure the listener as follows:                                                                                                                                                                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |    -  **Name**: Set it as needed. In this example, name it **listener-A**.                                                                                                                                                                                                                                                                                        |
   |                       |                       |    -  **Frontend Protocol**: Select **UDP** to forward encapsulated UDP packets.                                                                                                                                                                                                                                                                                  |
   |                       |                       |    -  **Frontend Port**: Enter **4789**, the fixed port used by the mirror target to receive traffic.                                                                                                                                                                                                                                                             |
   |                       |                       |    -  **Access Control**: Select **All IP addresses** for this example. If you select **Whitelist**, ensure that the mirror source IP address is in the whitelist.                                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  Configure the routing policy as follows:                                                                                                                                                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |    -  **Forwarding Mode**: Set it as needed. In this example, select **Load balancing**.                                                                                                                                                                                                                                                                          |
   |                       |                       |    -  **Backend Server Group Type**: Set it as needed. In this example, select **Hybrid**.                                                                                                                                                                                                                                                                        |
   |                       |                       |    -  **Backend Server Group Name**: Set it as needed. In this example, name it **serve_group-A**.                                                                                                                                                                                                                                                                |
   |                       |                       |    -  **Backend Protocol**: Select **UDP** to process encapsulated UDP packets.                                                                                                                                                                                                                                                                                   |
   |                       |                       |    -  **Forward to Same Port**: Set it as needed. In this example, disable it.                                                                                                                                                                                                                                                                                    |
   |                       |                       |    -  **Load Balancing Algorithm**: Set it as needed. In this example, select **Weighted round robin**.                                                                                                                                                                                                                                                           |
   |                       |                       |    -  **Sticky Session**: Set it as needed. In this example, disable it.                                                                                                                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  Add backend servers as follows:                                                                                                                                                                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |    -  On the **Backend Server** tab, select **ECS-target-01** and **ECS-target-02** for this example.                                                                                                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |       Set **Backend Port** to **4789** and **Weight** to **1**.                                                                                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |    -  **Health Check**: Disable it for this example. If port 4789 is not listened on and the health check option is enabled, the health check result will be unhealthy, preventing ELB from forwarding traffic to backend servers.                                                                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mirror filter         | 1                     | -  **Name**: Set it as needed. In this example, **mirror-filter-01** is used.                                                                                                                                                                                                                                                                                     |
   |                       |                       | -  Inbound rule: Add an inbound rule to accept TCP traffic from **ECS-test** to **ECS-source**.                                                                                                                                                                                                                                                                   |
   |                       |                       | -  Outbound rule: Add an outbound rule to accept TCP traffic from **ECS-source** to **ECS-test**.                                                                                                                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | For details about the rules, see :ref:`Table 5 <vpc_mirror_25__en-us_topic_0000002070193194_table42954412446>`.                                                                                                                                                                                                                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mirror session        | 1                     | -  **Basic Information**                                                                                                                                                                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |    -  **Name**: Set it as needed. In this example, **mirror-session-01** is used.                                                                                                                                                                                                                                                                                 |
   |                       |                       |    -  **Priority**: Set it as needed. In this example, **1** is used.                                                                                                                                                                                                                                                                                             |
   |                       |                       |    -  **VNI**: Set it as needed. In this example, **1** is used.                                                                                                                                                                                                                                                                                                  |
   |                       |                       |    -  **Packet Length**: Set it as needed. In this example, **96** is used.                                                                                                                                                                                                                                                                                       |
   |                       |                       |    -  **Mirror Session**: Enable it to mirror the traffic from the mirror source.                                                                                                                                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       | -  **Associate Mirror Filter**: Set it as needed. In this example, **mirror-filter-01** is used.                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **Associate Mirror Sources**: Set it as needed. In this example, the private IP address (192.168.0.230) of the network interface on **ECS-source** is used.                                                                                                                                                                                                    |
   |                       |                       | -  **Associate Mirror Target**                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |    -  **Type**: **Load balancer**                                                                                                                                                                                                                                                                                                                                 |
   |                       |                       |    -  Network interface: Set it as needed. In this example, the private IP address (192.168.0.147) of the network interface of **ELB-A** is used.                                                                                                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_mirror_25__en-us_topic_0000002052878369_en-us_topic_0285680794_table102261597217:

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

.. _vpc_mirror_25__en-us_topic_0000002070193194_en-us_topic_0285680794_table164981355467:

.. table:: **Table 3** Rules of security groups **Sg-A** and **Sg-X** (allowing traffic between ECSs)

   +----------------+-----------+---------+---------+-----------------+------------------------------------------------------------+------------------------------------------------------------------------+
   | Security Group | Direction | Action  | Type    | Protocol & Port | Source                                                     | Description                                                            |
   +================+===========+=========+=========+=================+============================================================+========================================================================+
   | Sg-A           | Inbound   | Allow   | IPv4    | TCP: 1234       | The security group that **ECS-test** is associated with:   | Allows TCP packets from **ECS-test** to **ECS-source** over port 1234. |
   |                |           |         |         |                 |                                                            |                                                                        |
   |                |           |         |         |                 | **Sg-X**                                                   |                                                                        |
   +----------------+-----------+---------+---------+-----------------+------------------------------------------------------------+------------------------------------------------------------------------+
   | Sg-X           | Inbound   | Allow   | IPv4    | TCP: All ports  | The security group that **ECS-source** is associated with: | Allows TCP packets from **ECS-source** to **ECS-test** over all ports. |
   |                |           |         |         |                 |                                                            |                                                                        |
   |                |           |         |         |                 | **Sg-A**                                                   |                                                                        |
   +----------------+-----------+---------+---------+-----------------+------------------------------------------------------------+------------------------------------------------------------------------+

.. _vpc_mirror_25__en-us_topic_0000002070193194_table686503122416:

.. table:: **Table 4** Security group **Sg-B** rule

   +-----------+-----------+-----------+-----------------+---------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Direction | Action    | Type      | Protocol & Port | Source                                                  | Description                                                                                   |
   +===========+===========+===========+=================+=========================================================+===============================================================================================+
   | Inbound   | Allow     | IPv4      | UDP: 4789       | The private IP address of mirror source **ECS-source**: | Allows UDP packets encapsulated by **ECS-source** to access **ECS-target-01** over port 4789. |
   |           |           |           |                 |                                                         |                                                                                               |
   |           |           |           |                 | 192.168.0.230/32                                        |                                                                                               |
   +-----------+-----------+-----------+-----------------+---------------------------------------------------------+-----------------------------------------------------------------------------------------------+

.. _vpc_mirror_25__en-us_topic_0000002070193194_table42954412446:

.. table:: **Table 5** Inbound and outbound rules of the mirror filter

   +-----------+----------+----------+--------+-------+-------------------------------------------+-------------------------+-------------------------------------------+-------------------------+
   | Direction | Priority | Protocol | Action | Type  | Source                                    | Source Port Range       | Destination                               | Destination Port Range  |
   +===========+==========+==========+========+=======+===========================================+=========================+===========================================+=========================+
   | Inbound   | 1        | TCP      | Accept | IPv4  | The private IP address of **ECS-test**:   | All                     | The private IP address of **ECS-source**: | Port of **ECS-source**: |
   |           |          |          |        |       |                                           |                         |                                           |                         |
   |           |          |          |        |       | 192.168.0.161/32                          |                         | 192.168.0.230/32                          | 1234-1234               |
   +-----------+----------+----------+--------+-------+-------------------------------------------+-------------------------+-------------------------------------------+-------------------------+
   | Outbound  | 1        | TCP      | Accept | IPv4  | The private IP address of **ECS-source**: | Port of **ECS-source**: | The private IP address of **ECS-test**:   | All                     |
   |           |          |          |        |       |                                           |                         |                                           |                         |
   |           |          |          |        |       | 192.168.0.230/32                          | 1234-1234               | 192.168.0.161/32                          |                         |
   +-----------+----------+----------+--------+-------+-------------------------------------------+-------------------------+-------------------------------------------+-------------------------+

Procedure
---------

:ref:`Figure 2 <vpc_mirror_25__en-us_topic_0000002070193194_fig142558410317>` shows the procedure required to mirror the inbound and outbound TCP traffic between a mirror source (network interface) and a given instance to a mirror target (load balancer).

.. _vpc_mirror_25__en-us_topic_0000002070193194_fig142558410317:

.. figure:: /_static/images/en-us_image_0000002581268352.png
   :alt: **Figure 2** Mirroring inbound and outbound TCP traffic to a load balancer

   **Figure 2** Mirroring inbound and outbound TCP traffic to a load balancer

Step 1: Create Cloud Resources
------------------------------

#. Create a VPC with a subnet.

   For details, see :ref:`Creating a VPC with a Subnet <en-us_topic_0013935842>`.

#. Create four ECSs.

   For details, see `Creating an ECS <https://docs.otc.t-systems.com/elastic-cloud-server/umn/getting_started/creating_an_ecs/index.html#en-us-topic-0021831611>`__.

#. Assign an EIP.

   For details, see :ref:`Assigning an EIP <en-us_topic_0013748738>`.

Step 2: Create a Load Balancer
------------------------------

#. Create a dedicated load balancer.

   For details, see `Creating a Dedicated Load Balancer <https://docs.otc.t-systems.com/elastic-load-balancing/umn/load_balancer/creating_a_dedicated_load_balancer.html#creating-a-dedicated-load-balancer>`__.

#. Add a UDP listener to the load balancer and add backend servers.

   For details, see `Adding a UDP Listener <https://docs.otc.t-systems.com/elastic-load-balancing/umn/listener/adding_a_udp_listener.html#elb-ug-jt-0007>`__.

Step 3: Create a Mirror Filter and a Mirror Session
---------------------------------------------------

#. Create a mirror filter.

   For details, see :ref:`Creating a Mirror Filter <vpc_mirror_04>`.

#. Create a mirror session, and associate the mirror filter, mirror source, and mirror target with this mirror session.

   For details, see :ref:`Creating a Mirror Session <vpc_mirror_12>`.

Step 4: Install Netcat (nc) to Simulate Traffic
-----------------------------------------------

The nc utility reads and writes data across network connections using TCP or UDP. It is usually used to test ports for accessibility. You need to install nc on both **ECS-source** and **ECS-test**.

#. Install nc on **ECS-source**.

   a. .. _vpc_mirror_25__en-us_topic_0000002070193194_en-us_topic_0000002015687352_en-us_topic_0285680794_li3716337101011:

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

   d. .. _vpc_mirror_25__en-us_topic_0000002070193194_en-us_topic_0000002015687352_li9477162552613:

      Unbind the EIP from **ECS-source** after nc is installed.

#. Repeat :ref:`1.a <vpc_mirror_25__en-us_topic_0000002070193194_en-us_topic_0000002015687352_en-us_topic_0285680794_li3716337101011>` to :ref:`1.d <vpc_mirror_25__en-us_topic_0000002070193194_en-us_topic_0000002015687352_li9477162552613>` on **ECS-test**.
#. Release the EIP.

Step 5: Check Whether the Mirror Session Works
----------------------------------------------

#. Establish a TCP connection between **ECS-source** and **ECS-test**.

   Use **ECS-source** to send TCP packets to **ECS-test** and check whether **ECS-test** can receive the packets.

   a. Run the following command on **ECS-source** to listen on port 1234:

      **nc -l** *<listening-port-of-mirror-source-ECS-source>*

      Example command:

      **nc -l 1234**

      If the command output is empty, the port is opened for listening.

   b. Run the following command on **ECS-test** to establish a TCP connection between **ECS-source** and **ECS-test**:

      **nc** *<private-IP-address-of-mirror-source-ECS-source> <listening-port-of-mirror-source-ECS-source>*

      Example command:

      **nc 192.168.0.230 1234**

      If the command output is empty, the TCP connection has been established.

   c. Enter any information (for example, **hello**) on **ECS-source** and press **Enter** to check whether requests can be sent over the TCP connection.

      .. code-block:: console

         [root@ecs-source ~]# nc -l 1234
         hello

   d. Check whether **ECS-test** can receive information from **ECS-source**.

      If information similar to the following is displayed, the information can be received and the TCP connection is successfully established.

      .. code-block:: console

         [root@ecs-test ~]# nc 192.168.0.230 1234
         hello

2. Check whether the outbound TCP packet from **ECS-source** to **ECS-test** can be mirrored to backend servers **ECS-target-01** and **ECS-target-02** of **ELB-A**.

   When **ECS-source** sends a TCP packet to **ECS-test**, run **tcpdump** to check whether **ECS-target-01** and **ECS-target-02** can receive the packet. If they do, the mirror session accepts the outbound TCP traffic.

   a. Remotely log in to **ECS-target-01**.

   b. Run the following command on **ECS-target-01** to view its network interface name:

      **ifconfig**

      Information similar to the following is displayed. In this example, the network interface of **ECS-target-01** is **eth0**.

      .. code-block:: console

         [root@ecs-target-01 ~]# ifconfig
         eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
                 inet 192.168.0.6  netmask 255.255.255.0  broadcast 192.168.0.255
                 inet6 fe80::f816:3eff:fe7e:d6dc  prefixlen 64  scopeid 0x20<link>
                 ether fa:16:3e:7e:d6:dc  txqueuelen 1000  (Ethernet)
                 RX packets 87498  bytes 114570302 (109.2 MiB)
                 RX errors 0  dropped 0  overruns 0  frame 0
                 TX packets 18337  bytes 6613541 (6.3 MiB)
                 TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
         ...

   c. Run the following command on **ECS-target-01** to check whether it can receive packets:

      **tcpdump -i** *<network-interface-name-of-the-mirror-target>* **udp port 4789 -nne**

      Example command:

      **tcpdump -i eth0 udp port 4789 -nne**

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-target-01 ~]# tcpdump -i eth0 udp port 4789 -nne
         dropped privs to tcpdump
         tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
         listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes

   d. Remotely log in to **ECS-target-02**.

   e. Run the following command on **ECS-target-02** to view its network interface name:

      **ifconfig**

      Information similar to the following is displayed. In this example, the network interface of **ECS-target-02** is **eth0**.

      .. code-block:: console

         [root@ecs-target-02 ~]# ifconfig
         eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
                 inet 192.168.0.12  netmask 255.255.255.0  broadcast 192.168.0.255
                 inet6 fe80::f816:3eff:fe7e:d6e2  prefixlen 64  scopeid 0x20<link>
                 ether fa:16:3e:7e:d6:e2  txqueuelen 1000  (Ethernet)
                 RX packets 87009  bytes 114283412 (108.9 MiB)
                 RX errors 0  dropped 0  overruns 0  frame 0
                 TX packets 17015  bytes 6492086 (6.1 MiB)
                 TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
         ...

   f. Run the following command on **ECS-target-02** to check whether it can receive packets:

      **tcpdump -i** *<network-interface-name-of-the-mirror-target>* **udp port 4789 -nne**

      Example command:

      **tcpdump -i eth0 udp port 4789 -nne**

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-target-02 ~]# tcpdump -i eth0 udp port 4789 -nne
         dropped privs to tcpdump
         tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
         listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes

   g. Enter any information (for example, **source to test**) on **ECS-source** and press **Enter** to send a TCP packet to **ECS-test**.

      Information similar to the following is displayed:

      .. code-block:: console

         [root@source ~]# nc -l 1234
         hello
         source to test

   h. Check whether **ECS-test** can receive "source to test" from **ECS-source**.

      If information similar to the following is displayed, **ECS-test** can receive "source to test" from **ECS-source**.

      .. code-block:: console

         [root@ecs-test ~]# nc 192.168.0.230 1234
         hello
         source to test

   i. Check whether **ECS-target-01** and **ECS-target-02** can receive the packet.

      -  **ECS-target-01**

         If the information similar to the following is displayed, the packet containing "source to test" (time: **19:09:21.273376**) from **ECS-source** is not sent to **ECS-test** after running **tcpdump**. This means the accept rule works. **vni 1** is the identifier of **mirror-session-01**, indicating that **ECS-target-01** can receive the packet through this mirror session. The packet content has two parts: a VXLAN packet encapsulated by traffic mirroring and the original packet. For details, see :ref:`Table 6 <vpc_mirror_22__en-us_topic_0000002015687352_table223316435223>`.

         .. code-block:: console

            [root@ecs-target-01 ~]# tcpdump -i eth0 udp port 4789 -nne
            dropped privs to tcpdump
            tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
            listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
            19:09:21.273376 fa:16:3e:d1:6b:5d > fa:16:3e:7e:d6:dc, ethertype IPv4 (0x0800), length 131: 192.168.0.230.32816 > 192.168.0.6.4789: VXLAN, flags [I] (0x08), vni 1
            fa:16:3e:7e:d6:bc > fa:16:3e:7e:d6:77, ethertype IPv4 (0x0800), length 81: 192.168.0.230.1234 > 192.168.0.161.57032: Flags [P.], seq 4181467553:4181467568, ack 3509843935, win 510, options [nop,nop,TS val 476501697 ecr 998055381], length 15

      -  **ECS-target-02**

         Information similar to the following is displayed. You can view the response packet (time: **19:09:21.273429**) from **ECS-test** to **ECS-source** after running **tcpdump**.

         .. code-block:: console

            [root@ecs-target-02 ~]# tcpdump -i eth0 udp port 4789 -nne
            dropped privs to tcpdump
            tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
            listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
            19:09:21.273429 fa:16:3e:d1:6b:5d > fa:16:3e:7e:d6:e2, ethertype IPv4 (0x0800), length 116: 192.168.0.230.32805 > 192.168.0.12.4789: VXLAN, flags [I] (0x08), vni 1
            fa:16:3e:7e:d6:77 > fa:16:3e:7e:d6:bc, ethertype IPv4 (0x0800), length 66: 192.168.0.161.57032 > 192.168.0.230.1234: Flags [.], ack 4181467568, win 502, options [nop,nop,TS val 998154498 ecr 476501697], length 0

3. Check whether the inbound TCP packets from **ECS-test** to **ECS-source** can be mirrored to backend servers **ECS-target-01** and **ECS-target-02** of **ELB-A**.

   When **ECS-test** sends a TCP packet to **ECS-source**, use tcpdump to check whether **ECS-target-01** and **ECS-target-02** can receive the packet. If they do, the mirror session accepts the inbound TCP traffic.

   a. Enter any information (for example, **test to source**) on **ECS-test** and press **Enter** to send a TCP packet to **ECS-source**.

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-test ~]# nc 192.168.0.230 1234
         hello
         source to test
         test to source

   b. Check whether **ECS-source** can receive "test to source" from **ECS-test**.

      If information similar to the following is displayed, **ECS-source** can receive "test to source" from **ECS-test**.

      .. code-block:: console

         [root@ecs-source ~]# nc -l 1234
         hello
         source to test
         test to source

   c. Check whether **ECS-target-01** and **ECS-target-02** can receive the packet.

      -  **ECS-target-01**

         Information similar to the following is displayed. You can view the packet containing "test to source" (time: **19:10:04.772581**) from **ECS-test** to **ECS-source** after running **tcpdump**. This means the accept rule works. **vni 1** is the identifier of **mirror-session-01**, indicating that **ECS-target-01** can receive the packet through this mirror session. The packet content has two parts: a VXLAN packet encapsulated by traffic mirroring and the original packet. For details, see :ref:`Table 6 <vpc_mirror_22__en-us_topic_0000002015687352_table223316435223>`.

         .. code-block:: console

            [root@ecs-target-01 ~]# tcpdump -i eth0 udp port 4789 -nne
            dropped privs to tcpdump
            tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
            listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
            19:09:21.273376 fa:16:3e:d1:6b:5d > fa:16:3e:7e:d6:dc, ethertype IPv4 (0x0800), length 131: 192.168.0.230.32816 > 192.168.0.6.4789: VXLAN, flags [I] (0x08), vni 1
            fa:16:3e:7e:d6:bc > fa:16:3e:7e:d6:77, ethertype IPv4 (0x0800), length 81: 192.168.0.230.1234 > 192.168.0.161.57032: Flags [P.], seq 4181467553:4181467568, ack 3509843935, win 510, options [nop,nop,TS val 476501697 ecr 998055381], length 15
            19:10:04.772581 fa:16:3e:d1:6b:5d > fa:16:3e:7e:d6:dc, ethertype IPv4 (0x0800), length 131: 192.168.0.230.32805 > 192.168.0.6.4789: VXLAN, flags [I] (0x08), vni 1
            fa:16:3e:7e:d6:77 > fa:16:3e:7e:d6:bc, ethertype IPv4 (0x0800), length 81: 192.168.0.161.57032 > 192.168.0.230.1234: Flags [P.], seq 1:16, ack 15, win 502, options [nop,nop,TS val 998197997 ecr 476501697], length 15

      -  **ECS-target-02**

         Information similar to the following is displayed. You can view the response packet (time: **19:10:04.772601**) from **ECS-test** to **ECS-source** after running **tcpdump**.

         .. code-block:: console

            [root@ecs-target-02 ~]# tcpdump -i eth0 udp port 4789 -nne
            dropped privs to tcpdump
            tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
            listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
            19:09:21.273429 fa:16:3e:d1:6b:5d > fa:16:3e:7e:d6:e2, ethertype IPv4 (0x0800), length 116: 192.168.0.230.32805 > 192.168.0.12.4789: VXLAN, flags [I] (0x08), vni 1
            fa:16:3e:7e:d6:77 > fa:16:3e:7e:d6:bc, ethertype IPv4 (0x0800), length 66: 192.168.0.161.57032 > 192.168.0.230.1234: Flags [.], ack 4181467568, win 502, options [nop,nop,TS val 998154498 ecr 476501697], length 0
            19:10:04.772601 fa:16:3e:d1:6b:5d > fa:16:3e:7e:d6:e2, ethertype IPv4 (0x0800), length 116: 192.168.0.230.32816 > 192.168.0.12.4789: VXLAN, flags [I] (0x08), vni 1
            fa:16:3e:7e:d6:bc > fa:16:3e:7e:d6:77, ethertype IPv4 (0x0800), length 66: 192.168.0.230.1234 > 192.168.0.161.57032: Flags [.], ack 15, win 510, options [nop,nop,TS val 476545196 ecr 998197997], length 0
