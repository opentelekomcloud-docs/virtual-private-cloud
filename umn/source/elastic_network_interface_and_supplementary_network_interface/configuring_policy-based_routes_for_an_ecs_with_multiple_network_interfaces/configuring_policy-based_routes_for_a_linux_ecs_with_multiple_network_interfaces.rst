:original_name: vpc_nic_0016.html

.. _vpc_nic_0016:

Configuring Policy-based Routes for a Linux ECS with Multiple Network Interfaces
================================================================================

Scenarios
---------

This section describes how to configure policy-based routes for a CentOS 8.0 64-bit ECS with two network interfaces.

-  IPv4: :ref:`Configuring IPv4 Policy-based Routes for a CentOS ECS <vpc_nic_0016__en-us_topic_0000001206815912_section20907123285010>`
-  IPv6: :ref:`Configuring IPv6 Policy-based Routes for a CentOS ECS <vpc_nic_0016__en-us_topic_0000001206815912_section1573810163614>`

For details about the background knowledge and networking of an ECS with two network interfaces, see :ref:`Overview <vpc_nic_0014>`.

.. _vpc_nic_0016__en-us_topic_0000001206815912_section20907123285010:

Configuring IPv4 Policy-based Routes for a CentOS ECS
-----------------------------------------------------

#. .. _vpc_nic_0016__en-us_topic_0000001206815912_li2073125515581:

   Collect the ECS network interface information required for configuring policy-based routes.

   For details, see :ref:`Collecting ECS Network Information <vpc_nic_0015>`.

   In this example, the network information of the ECS is shown in :ref:`Table 1 <vpc_nic_0016__en-us_topic_0000001206815912_table02681556143>`.

   .. _vpc_nic_0016__en-us_topic_0000001206815912_table02681556143:

   .. table:: **Table 1** CentOS ECS using IPv4

      +-----------------------+-----------------------------+-----------------------------+
      | ECS                   | Primary Network Interface   | Extended Network Interface  |
      +=======================+=============================+=============================+
      | Source                | -  IP address: 10.0.0.115   | -  IP address: 10.0.1.183   |
      |                       | -  Subnet: 10.0.0.0/24      | -  Subnet: 10.0.1.0/24      |
      |                       | -  Subnet gateway: 10.0.0.1 | -  Subnet gateway: 10.0.1.1 |
      +-----------------------+-----------------------------+-----------------------------+
      | Destination           | IP address: 10.0.2.12       | N/A                         |
      +-----------------------+-----------------------------+-----------------------------+

#. Log in to the source ECS.

#. Check whether the source ECS can use its primary network interface to communicate with the destination ECS:

   **Before configuring policy-based routes, ensure that the source ECS can use its primary network interface to communicate with the destination ECS.**

   **ping -I** *<IP-address-of-the-primary-network-interface-on-the-source-ECS>* *<IP-address-of-the-destination-ECS>*

   In this example, run the following command:

   **ping -I 10.0.0.115 10.0.2.12**

   If information similar to the following is displayed, the source ECS can use its primary network interface to communicate with the destination ECS.

   .. code-block:: console

      [root@ecs-resource ~]# ping -I 10.0.0.115 10.0.2.12
      PING 10.0.2.12 (10.0.2.12) from 10.0.0.115 : 56(84) bytes of data.
      64 bytes from 10.0.2.12: icmp_seq=1 ttl=64 time=0.775 ms
      64 bytes from 10.0.2.12: icmp_seq=2 ttl=64 time=0.268 ms
      64 bytes from 10.0.2.12: icmp_seq=3 ttl=64 time=0.220 ms
      64 bytes from 10.0.2.12: icmp_seq=4 ttl=64 time=0.167 ms
      ^C
      --- 10.0.2.12 ping statistics ---

#. .. _vpc_nic_0016__en-us_topic_0000001206815912_li330410351570:

   Query the network interface names of the source ECS:

   **ifconfig**

   Search for the network interface names based on IP addresses.

   -  The primary network interface address is 10.0.0.115, and its name is eth0.
   -  The extended network interface address is 10.0.1.183, and its name is eth1.

   .. code-block:: console

      [root@ecs-resource ~]# ifconfig
      eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
              inet 10.0.0.115  netmask 255.255.255.0  broadcast 10.0.0.255
              inet6 fe80::f816:3eff:fe92:6e0e  prefixlen 64  scopeid 0x20<link>
              ether fa:16:3e:92:6e:0e  txqueuelen 1000  (Ethernet)
              RX packets 432288  bytes 135762012 (129.4 MiB)
              RX errors 0  dropped 0  overruns 0  frame 1655
              TX packets 423744  bytes 106716932 (101.7 MiB)
              TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

      eth1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
              inet 10.0.1.183  netmask 255.255.255.0  broadcast 10.0.1.255
              inet6 fe80::f816:3eff:febf:5818  prefixlen 64  scopeid 0x20<link>
              ether fa:16:3e:bf:58:18  txqueuelen 1000  (Ethernet)
              RX packets 9028  bytes 536972 (524.3 KiB)
              RX errors 0  dropped 0  overruns 0  frame 1915
              TX packets 6290  bytes 272473 (266.0 KiB)
              TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

#. Configure temporary routes for the source ECS.

   .. important::

      Temporary routes are applied immediately but are lost after ECS restarts. To avoid network disruptions, perform :ref:`6 <vpc_nic_0016__en-us_topic_0000001206815912_li15279203551015>` to configure permanent routes instead.

   a. .. _vpc_nic_0016__en-us_topic_0000001206815912_li111457351491:

      Configure policy-based routes for both the primary and extended network interfaces.

      -  Primary network interface

         **ip route add default via** *<subnet-gateway>* **dev** *<network-interface-name>* **table** *<route-table-name>*

         **ip route add** *<subnet-CIDR-block>* **dev** *<network-interface-name>* **table** *<route-table-name>*

         **ip rule add from** *<network-interface-address>* **table** *<route-table-name>*

      -  Extended network interface

         **ip route add default via** *<subnet-gateway>* **dev** *<network-interface-name>* **table** *<route-table-name>*

         **ip route add** *<subnet-CIDR-block>* **dev** *<network-interface-name>* **table** *<route-table-name>*

         **ip rule add from** *<network-interface-address>* **table** *<route-table-name>*

      Configure the parameters as follows:

      -  Network interface name: Enter the name obtained in :ref:`4 <vpc_nic_0016__en-us_topic_0000001206815912_li330410351570>`.
      -  Route table name: Name the route table with a number.
      -  Other network information: Enter the IP addresses collected in :ref:`1 <vpc_nic_0016__en-us_topic_0000001206815912_li2073125515581>`.

      In this example, run the following commands:

      -  Primary network interface

         **ip route add default via 10.0.0.1 dev eth0 table 10**

         **ip route add 10.0.0.0/24 dev eth0 table 10**

         **ip rule add from 10.0.0.115 table 10**

      -  Extended network interface

         **ip route add default via 10.0.1.1 dev eth1 table 20**

         **ip route add 10.0.1.0/24 dev eth1 table 20**

         **ip rule add from 10.0.1.183 table 20**

      .. note::

         If the ECS has multiple network interfaces, configure policy-based routes for all network interfaces one by one.

   b. .. _vpc_nic_0016__en-us_topic_0000001206815912_li71457351897:

      Check whether the policy-based routes are added.

      **ip rule**

      **ip route show table** *<route-table-name-of-the-primary-network-interface>*

      **ip route show table** *<route-table-name-of-the-extended-network-interface>*

      The route table name is the one configured in :ref:`5.a <vpc_nic_0016__en-us_topic_0000001206815912_li111457351491>`.

      In this example, run the following commands:

      **ip rule**

      **ip route show table 10**

      **ip route show table 20**

      If information similar to the following is displayed, the policy-based routes have been added.

      .. code-block:: console

         [root@ecs-resource ~]# ip rule
         0:      from all lookup local
         32764:  from 10.0.1.183 lookup 20
         32765:  from 10.0.0.115 lookup 10
         32766:  from all lookup main
         32767:  from all lookup default
         [root@ecs-resource ~]# ip route show table 10
         default via 10.0.0.1 dev eth0
         10.0.0.0/24 dev eth0 scope link
         [root@ecs-resource ~]# ip route show table 20
         default via 10.0.1.1 dev eth1
         10.0.1.0/24 dev eth1 scope link

   c. .. _vpc_nic_0016__en-us_topic_0000001206815912_li15146835598:

      Check whether the source and destination ECSs can communicate with each other.

      **ping -I** *<IP-address-of-the-primary-network-interface-on-the-source-ECS>* *<IP-address-of-the-destination-ECS>*

      **ping -I** *<IP-address-of-the-extended-network-interface-on-the-source-ECS>* *<IP-address-of-the-destination-ECS>*

      In this example, run the following commands:

      **ping -I 10.0.0.115 10.0.2.12**

      **ping -I 10.0.1.183 10.0.2.12**

      If information similar to the following is displayed, both the network interfaces of the source ECS can communicate with the destination ECS.

      .. code-block:: console

         [root@ecs-resource ~]# ping -I 10.0.0.115 10.0.2.12
         PING 10.0.2.12 (10.0.2.12) from 10.0.0.115 : 56(84) bytes of data.
         64 bytes from 10.0.2.12: icmp_seq=1 ttl=64 time=0.775 ms
         64 bytes from 10.0.2.12: icmp_seq=2 ttl=64 time=0.268 ms
         64 bytes from 10.0.2.12: icmp_seq=3 ttl=64 time=0.220 ms
         64 bytes from 10.0.2.12: icmp_seq=4 ttl=64 time=0.167 ms
         ^C
         --- 10.0.2.12 ping statistics ---
         4 packets transmitted, 4 received, 0% packet loss, time 102ms
         rtt min/avg/max/mdev = 0.167/0.357/0.775/0.244 ms
         [root@ecs-resource ~]# ping -I 10.0.1.183 10.0.2.12
         PING 10.0.2.12 (10.0.2.12) from 10.0.1.183 : 56(84) bytes of data.
         64 bytes from 10.0.2.12: icmp_seq=1 ttl=64 time=2.84 ms
         64 bytes from 10.0.2.12: icmp_seq=2 ttl=64 time=0.258 ms
         64 bytes from 10.0.2.12: icmp_seq=3 ttl=64 time=0.234 ms
         64 bytes from 10.0.2.12: icmp_seq=4 ttl=64 time=0.153 ms
         ^C
         --- 10.0.2.12 ping statistics ---
         4 packets transmitted, 4 received, 0% packet loss, time 92ms
         rtt min/avg/max/mdev = 0.153/0.871/2.840/1.137 ms

#. .. _vpc_nic_0016__en-us_topic_0000001206815912_li15279203551015:

   Configure permanent routes for the source ECS.

   a. Run the following command to open the **/etc/rc.local** file:

      **vi /etc/rc.local**

   b. Press **i** to enter the editing mode.

   c. Add the following content to the end of the file:

      .. code-block::

         # check eth0
         for ((x=0; x<10; x++)); do
           if (ip addr show eth0 | grep -w 10.0.0.115 >/dev/null 2>&1); then
             break
           fi
           sleep 1
         done

         # Add v4 routes for eth0
         ip route flush table 10
         ip route add default via 10.0.0.1 dev eth0 table 10
         ip route add 10.0.0.0/24 dev eth0 table 10
         ip rule add from 10.0.0.115 table 10

         # check eth1
         for ((x=0; x<10; x++)); do
           if (ip addr show eth1 | grep -w 10.0.1.183 >/dev/null 2>&1); then
             break
           fi
           sleep 1
         done

         # Add v4 routes for eth1
         ip route flush table 20
         ip route add default via 10.0.1.1 dev eth1 table 20
         ip route add 10.0.1.0/24 dev eth1 table 20
         ip rule add from 10.0.1.183 table 20
         # Add v4 routes for cloud-init
         ip rule add to 169.254.169.254 table main

      The parameters are as follows:

      -  **check eth0**: Check for the presence of the IP address 10.0.0.115 on primary network interface eth0 every second up to 10 times.
      -  **Add v4 routes for eth0**: Add policy-based routes for the primary network interface. Set the value to be the same as that configured in :ref:`5.a <vpc_nic_0016__en-us_topic_0000001206815912_li111457351491>`.
      -  **check eth1**: Check for the presence of the IP address 10.0.1.183 on extended network interface eth1 every second up to 10 times.
      -  **Add v4 routes for eth1**: Add policy-based routes for the extended network interface. Set the value to be the same as that configured in :ref:`5.a <vpc_nic_0016__en-us_topic_0000001206815912_li111457351491>`.
      -  **Add v4 routes for cloud-init**: Set the Cloud-Init address to the same value as that in this example.

   d. Press **ESC** to exit and enter **:wq!** to save the configuration.

   e. .. _vpc_nic_0016__en-us_topic_0000001206815912_li9468953173010:

      Run the following command to add execute permissions to the **/etc/rc.local** file:

      **chmod +x /etc/rc.local**

      .. note::

         If your operating system is Red Hat or EulerOS, run the following command after you perform :ref:`6.e <vpc_nic_0016__en-us_topic_0000001206815912_li9468953173010>`:

         **chmod +x /etc/rc.d/rc.local**

   f. Run the following command to restart the ECS:

      **reboot**

      .. important::

         Policy-based routes added to the **/etc/rc.local** file take effect only after the ECS is restarted. Ensure that workloads on the ECS will not be affected before restarting the ECS.

   g. Repeat :ref:`5.b <vpc_nic_0016__en-us_topic_0000001206815912_li71457351897>` to :ref:`5.c <vpc_nic_0016__en-us_topic_0000001206815912_li15146835598>` to check whether the policy-based routes are added and whether the source ECS and the destination ECS can communicate with each other.

.. _vpc_nic_0016__en-us_topic_0000001206815912_section1573810163614:

Configuring IPv6 Policy-based Routes for a CentOS ECS
-----------------------------------------------------

#. .. _vpc_nic_0016__en-us_topic_0000001206815912_li55021158174319:

   Collect the ECS network interface information required for configuring policy-based routes.

   For details, see :ref:`Collecting ECS Network Information <vpc_nic_0015>`.

   .. table:: **Table 2** CentOS ECS using IPv6

      +-----------------------+----------------------------------------------------------+----------------------------------------------------------+
      | ECS                   | Primary Network Interface                                | Extended Network Interface                               |
      +=======================+==========================================================+==========================================================+
      | Source                | -  IPv4 address: 10.0.0.102                              | -  IPv4 address: 10.0.1.191                              |
      |                       | -  IPv6 address: 2407:c080:1200:1dd8:859c:e5d5:8b3d:a2d9 | -  IPv6 address: 2407:c080:1200:1a9c:7cc0:63b5:8e65:4dd8 |
      |                       | -  IPv6 subnet: 2407:c080:1200:1dd8::/64                 | -  IPv6 subnet: 2407:c080:1200:1a9c::/64                 |
      |                       | -  IPv6 subnet gateway: 2407:c080:1200:1dd8::1           | -  IPv6 subnet gateway: 2407:c080:1200:1a9c::1           |
      +-----------------------+----------------------------------------------------------+----------------------------------------------------------+
      | Destination           | -  IPv4 address: 10.0.2.3                                | N/A                                                      |
      |                       | -  IPv6 address: 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044 |                                                          |
      +-----------------------+----------------------------------------------------------+----------------------------------------------------------+

#. Log in to the source ECS.

#. Check whether the ECSs have IPv6 enabled and have IPv6 addresses.

   .. important::

      Perform this step for both the source and destination ECSs to ensure that the ECSs have IPv6 addresses. Otherwise, the ECSs cannot communicate with each other using IPv6 addresses.

      ECSs in this example run CentOS 8.0 (64-bit). For details about how to obtain IPv6 addresses for ECSs running other OSs, see the "Linux (Automatically Enabling Dynamic Assignment of IPv6 Addresses)" part in section "Dynamically Assigning IPv6 Addresses" in the *Elastic Cloud Server User Guide*.

   a. .. _vpc_nic_0016__en-us_topic_0000001206815912_li69657203218:

      Run the following command to check whether the ECS has IPv6 addresses:

      **ip addr**

      In the following command output, eth0 and eth1 are the network interfaces of the ECS. Each network interface has one **inet6** entry starting with **fe80**. This indicates that the ECS has IPv6 enabled but has not been assigned IPv6 addresses. In this case, perform :ref:`3.b <vpc_nic_0016__en-us_topic_0000001206815912_li199652253212>` to :ref:`3.g <vpc_nic_0016__en-us_topic_0000001206815912_li169673213324>` to assign IPv6 addresses.

      .. code-block:: console

         [root@ecs-resource ~]# ip addr
         ...
         2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
             link/ether fa:16:3e:22:22:88 brd ff:ff:ff:ff:ff:ff
             inet 10.0.0.102/24 brd 10.0.0.255 scope global dynamic noprefixroute eth0
                valid_lft 107943256sec preferred_lft 107943256sec
             inet6 fe80::f816:3eff:fe22:2288/64 scope link
                valid_lft forever preferred_lft forever
         3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
             link/ether fa:16:3e:22:23:e1 brd ff:ff:ff:ff:ff:ff
             inet 10.0.1.191/24 brd 10.0.1.255 scope global dynamic noprefixroute eth1
                valid_lft 107943256sec preferred_lft 107943256sec
             inet6 fe80::f816:3eff:fe22:23e1/64 scope link
                valid_lft forever preferred_lft forever

   b. .. _vpc_nic_0016__en-us_topic_0000001206815912_li199652253212:

      Query the network interface names of the source ECS:

      **ifconfig**

      Search for the network interface names based on IP addresses.

      -  The primary network interface address is 10.0.0.102, and its name is eth0.
      -  The extended network interface address is 10.0.1.191, and its name is eth1.

      .. code-block:: console

         [root@ecs-resource ~]# ifconfig
         eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
                 inet 10.0.0.102  netmask 255.255.255.0  broadcast 10.0.0.255
                 inet6 fe80::f816:3eff:fe22:2288  prefixlen 64  scopeid 0x20<link>
                 ether fa:16:3e:22:22:88  txqueuelen 1000  (Ethernet)
                 RX packets 135116  bytes 132321802 (126.1 MiB)
                 RX errors 0  dropped 0  overruns 0  frame 0
                 TX packets 60963  bytes 23201005 (22.1 MiB)
                 TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

         eth1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
                 inet 10.0.1.191  netmask 255.255.255.0  broadcast 10.0.1.255
                 inet6 fe80::f816:3eff:fe22:23e1  prefixlen 64  scopeid 0x20<link>
                 ether fa:16:3e:22:23:e1  txqueuelen 1000  (Ethernet)
                 RX packets 885  bytes 97676 (95.3 KiB)
                 RX errors 0  dropped 0  overruns 0  frame 0
                 TX packets 47  bytes 4478 (4.3 KiB)
                 TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

   c. Configure the **ifcfg** file of the primary network interface.

      #. Run the following command to open the **ifcfg** file of the primary network interface:

         **vi /etc/sysconfig/network-scripts/ifcfg-**\ *Primary network interface name*

         The name of the primary network interface is obtained in :ref:`3.b <vpc_nic_0016__en-us_topic_0000001206815912_li199652253212>`.

         In this example, run the following command:

         **vi /etc/sysconfig/network-scripts/ifcfg-eth0**

      #. Press **i** to enter the editing mode.

      #. Add the following content to the end of the file:

         .. code-block::

            IPV6INIT="yes"
            DHCPV6C="yes"

      #. Press **ESC** to exit and enter **:wq!** to save the configuration.

   d. Configure the **ifcfg** file of the extended network interface.

      #. Run the following command to open the **ifcfg** file of the extended network interface:

         **vi /etc/sysconfig/network-scripts/ifcfg-**\ *Extended network interface name*

         The name of the extended network interface is obtained in :ref:`3.b <vpc_nic_0016__en-us_topic_0000001206815912_li199652253212>`.

         In this example, run the following command:

         **vi /etc/sysconfig/network-scripts/ifcfg-eth1**

      #. Press **i** to enter the editing mode.

      #. Add the following content to the end of the file:

         .. code-block::

            IPV6INIT="yes"
            DHCPV6C="yes"

      #. Press **ESC** to exit and enter **:wq!** to save the configuration.

   e. Edit the **/etc/sysconfig/network** file.

      #. Run the following command to open the **/etc/sysconfig/network** file:

         **vi /etc/sysconfig/network**

      #. Press **i** to enter the editing mode.

      #. Add the following content to the end of the file:

         .. code-block::

            NETWORKING_IPV6="yes"

      #. Press **ESC** to exit and enter **:wq!** to save the configuration.

   f. Run the following command to restart the network service for the configuration to take effect:

      **systemctl restart NetworkManager**

   g. .. _vpc_nic_0016__en-us_topic_0000001206815912_li169673213324:

      Run the following command to check whether the ECS has IPv6 addresses:

      **ip addr**

      In the following command output, each network interface has an additional **inet6** entry starting with **2407**, followed by an entry starting with **fe80**. This indicates that the ECS has been assigned IPv6 addresses.

      .. code-block:: console

         [root@ecs-resource ~]# ip addr
         ...
         2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
             link/ether fa:16:3e:22:22:88 brd ff:ff:ff:ff:ff:ff
             inet 10.0.0.102/24 brd 10.0.0.255 scope global dynamic noprefixroute eth0
                valid_lft 107999994sec preferred_lft 107999994sec
             inet6 2407:c080:1200:1dd8:859c:e5d5:8b3d:a2d9/128 scope global dynamic noprefixroute
                valid_lft 7195sec preferred_lft 7195sec
             inet6 fe80::f816:3eff:fe22:2288/64 scope link noprefixroute
                valid_lft forever preferred_lft forever
         3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
             link/ether fa:16:3e:22:23:e1 brd ff:ff:ff:ff:ff:ff
             inet 10.0.1.191/24 brd 10.0.1.255 scope global dynamic noprefixroute eth1
                valid_lft 107999994sec preferred_lft 107999994sec
             inet6 2407:c080:1200:1a9c:7cc0:63b5:8e65:4dd8/128 scope global dynamic noprefixroute
                valid_lft 7198sec preferred_lft 7198sec
             inet6 fe80::f816:3eff:fe22:23e1/64 scope link noprefixroute
                valid_lft forever preferred_lft forever

   h. Log in to the destination ECS and assign an IPv6 address by performing operations from :ref:`3.a <vpc_nic_0016__en-us_topic_0000001206815912_li69657203218>` to :ref:`3.g <vpc_nic_0016__en-us_topic_0000001206815912_li169673213324>`.

#. Log in to the source ECS and check whether it can use its primary network interface to communicate with the destination ECS:

   **Before configuring policy-based routes, ensure that the source ECS can use its primary network interface to communicate with the destination ECS.**

   **ping6 -I** *<IP-address-of-the-primary-network-interface-on-the-source-ECS>* *<IP-address-of-the-destination-ECS>*

   In this example, run the following command:

   **ping6 -I 2407:c080:1200:1dd8:859c:e5d5:8b3d:a2d9 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044**

   If information similar to the following is displayed, the source ECS can use its primary network interface to communicate with the destination ECS.

   .. code-block:: console

      [root@ecs-resource ~]# ping6 -I 2407:c080:1200:1dd8:859c:e5d5:8b3d:a2d9 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044
      PING 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044(2407:c080:1200:1dd9:16a7:fe7a:8f71:7044) from 2407:c080:1200:1dd8:859c:e5d5:8b3d:a2d9 : 56 data bytes
      64 bytes from 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044: icmp_seq=1 ttl=64 time=0.635 ms
      64 bytes from 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044: icmp_seq=2 ttl=64 time=0.320 ms
      64 bytes from 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044: icmp_seq=3 ttl=64 time=0.287 ms
      64 bytes from 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044: icmp_seq=4 ttl=64 time=0.193 ms
      ^C
      --- 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044 ping statistics ---
      4 packets transmitted, 4 received, 0% packet loss, time 3074ms
      rtt min/avg/max/mdev = 0.193/0.358/0.635/0.167 ms

#. Log in to the source ECS and configure temporary routes for the ECS.

   .. important::

      Temporary routes are applied immediately but are lost after ECS restarts. To avoid network disruptions, perform :ref:`6 <vpc_nic_0016__en-us_topic_0000001206815912_li2516135483514>` to configure permanent routes instead.

   a. .. _vpc_nic_0016__en-us_topic_0000001206815912_li723364423517:

      Configure policy-based routes for both the primary and extended network interfaces.

      -  Primary network interface

         **ip -6 route add default via** *<subnet-gateway>* **dev** *<network-interface-name>* **table** *<route-table-name>*

         **ip -6 route add** *<subnet-CIDR-block>* **dev** *<network-interface-name>* **table** *<route-table-name>*

         **ip -6 rule add from** *<network-interface-address>* **table** *<route-table-name>*

      -  Extended network interface

         **ip -6 route add default via** *<subnet-gateway>* **dev** *<network-interface-name>* **table** *<route-table-name>*

         **ip -6 route add** *<subnet-CIDR-block>* **dev** *<network-interface-name>* **table** *<route-table-name>*

         **ip -6 rule add from** *<network-interface-address>* **table** *<route-table-name>*

      Configure the parameters as follows:

      -  Network interface name: Enter the name obtained in :ref:`3.b <vpc_nic_0016__en-us_topic_0000001206815912_li199652253212>`.
      -  Route table name: Name the route table with a number.
      -  Other network information: Enter the IP addresses collected in :ref:`1 <vpc_nic_0016__en-us_topic_0000001206815912_li55021158174319>`.

      In this example, run the following commands:

      -  Primary network interface

         **ip -6 route add default via 2407:c080:1200:1dd8::1 dev eth0 table 10**

         **ip -6 route add 2407:c080:1200:1dd8::/64 dev eth0 table 10**

         **ip -6 rule add from 2407:c080:1200:1dd8:859c:e5d5:8b3d:a2d9 table 10**

      -  Extended network interface

         **ip -6 route add default via 2407:c080:1200:1a9c::1 dev eth1 table 20**

         **ip -6 route add 2407:c080:1200:1a9c::/64 dev eth1 table 20**

         **ip -6 rule add from 2407:c080:1200:1a9c:7cc0:63b5:8e65:4dd8 table 20**

      .. note::

         If the ECS has multiple network interfaces, configure policy-based routes for all network interfaces one by one.

   b. .. _vpc_nic_0016__en-us_topic_0000001206815912_li3234144414354:

      Check whether the policy-based routes are added.

      **ip -6 rule**

      **ip -6 route show table** *<route-table-name-of-the-primary-network-interface>*

      **ip -6 route show table** *<route-table-name-of-the-extended-network-interface>*

      The route table name is the one configured in :ref:`5.a <vpc_nic_0016__en-us_topic_0000001206815912_li723364423517>`.

      In this example, run the following commands:

      **ip -6 rule**

      **ip -6 route show table 10**

      **ip -6 route show table 20**

      If information similar to the following is displayed, the policy-based routes have been added.

      .. code-block:: console

         [root@ecs-resource ~]# ip -6 rule
         0:      from all lookup local
         32764:  from 2407:c080:1200:1a9c:7cc0:63b5:8e65:4dd8 lookup 20
         32765:  from 2407:c080:1200:1dd8:859c:e5d5:8b3d:a2d9 lookup 10
         32766:  from all lookup main
         [root@ecs-resource ~]# ip -6 route show table 10
         2407:c080:1200:1dd8::/64 dev eth0 metric 1024 pref medium
         default via 2407:c080:1200:1dd8::1 dev eth0 metric 1024 pref medium
         [root@ecs-resource ~]# ip -6 route show table 20
         2407:c080:1200:1a9c::/64 dev eth1 metric 1024 pref medium
         default via 2407:c080:1200:1a9c::1 dev eth1 metric 1024 pref medium

   c. .. _vpc_nic_0016__en-us_topic_0000001206815912_li1523514414353:

      Check whether the source and destination ECSs can communicate with each other.

      **ping -6 -I** *<IP-address-of-the-primary-network-interface-on-the-source-ECS>* *<IP-address-of-the-destination-ECS>*

      **ping -6 -I** *<IP-address-of-the-extended-network-interface-on-the-source-ECS>* *<IP-address-of-the-destination-ECS>*

      In this example, run the following commands:

      **ping -6 -I 2407:c080:1200:1dd8:859c:e5d5:8b3d:a2d9 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044**

      **ping -6 -I 2407:c080:1200:1a9c:7cc0:63b5:8e65:4dd8 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044**

      If information similar to the following is displayed, both the network interfaces of the source ECS can communicate with the destination ECS.

      .. code-block:: console

         [root@ecs-resource ~]# ping -6 -I 2407:c080:1200:1dd8:859c:e5d5:8b3d:a2d9 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044
         PING 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044(2407:c080:1200:1dd9:16a7:fe7a:8f71:7044) from 2407:c080:1200:1dd8:859c:e5d5:8b3d:a2d9 : 56 data bytes
         64 bytes from 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044: icmp_seq=1 ttl=64 time=0.770 ms
         64 bytes from 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044: icmp_seq=2 ttl=64 time=0.295 ms
         64 bytes from 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044: icmp_seq=3 ttl=64 time=0.245 ms
         ^C
         --- 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044 ping statistics ---
         3 packets transmitted, 3 received, 0% packet loss, time 2080ms
         rtt min/avg/max/mdev = 0.245/0.436/0.770/0.237 ms
         [root@ecs-resource ~]# ping -6 -I 2407:c080:1200:1a9c:7cc0:63b5:8e65:4dd8 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044
         PING 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044(2407:c080:1200:1dd9:16a7:fe7a:8f71:7044) from 2407:c080:1200:1a9c:7cc0:63b5:8e65:4dd8 : 56 data bytes
         64 bytes from 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044: icmp_seq=1 ttl=64 time=0.922 ms
         64 bytes from 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044: icmp_seq=2 ttl=64 time=0.307 ms
         64 bytes from 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044: icmp_seq=3 ttl=64 time=0.174 ms
         ^C
         --- 2407:c080:1200:1dd9:16a7:fe7a:8f71:7044 ping statistics ---
         3 packets transmitted, 3 received, 0% packet loss, time 2059ms
         rtt min/avg/max/mdev = 0.174/0.467/0.922/0.326 ms

#. .. _vpc_nic_0016__en-us_topic_0000001206815912_li2516135483514:

   Configure permanent routes for the source ECS.

   a. Run the following command to open the **/etc/rc.local** file:

      **vi /etc/rc.local**

   b. Press **i** to enter the editing mode.

   c. Add the following content to the end of the file:

      .. code-block::

         # check eth0
         for ((x=0; x<10; x++)); do
           if (ip addr show eth0 | grep -w 2407:c080:1200:1dd8:859c:e5d5:8b3d:a2d9 >/dev/null 2>&1); then
             break
           fi
           sleep 1
         done

         # Add v6 routes for eth0
         ip -6 route flush table 10
         ip -6 route add default via 2407:c080:1200:1dd8::1 dev eth0 table 10
         ip -6 route add 2407:c080:1200:1dd8::/64 dev eth0 table 10
         ip -6 rule add from 2407:c080:1200:1dd8:859c:e5d5:8b3d:a2d9 table 10

         # check eth1
         for ((x=0; x<10; x++)); do
           if (ip addr show eth1 | grep -w 2407:c080:1200:1a9c:7cc0:63b5:8e65:4dd8 >/dev/null 2>&1); then
             break
           fi
           sleep 1
         done

         # Add v6 routes for eth1
         ip -6 route flush table 20
         ip -6 route add default via 2407:c080:1200:1a9c::1 dev eth1 table 20
         ip -6 route add 2407:c080:1200:1a9c::/64 dev eth1 table 20
         ip -6 rule add from 2407:c080:1200:1a9c:7cc0:63b5:8e65:4dd8 table 20

      The parameters are as follows:

      -  **check eth0**: Check whether primary network interface eth0 has obtained an IPv6 address (2407:c080:1200:1dd8:859c:e5d5:8b3d:a2d9) every second up to 10 times.
      -  **Add v6 routes for eth0**: Add policy-based routes for the primary network interface. Set the value to be the same as that configured in :ref:`5.a <vpc_nic_0016__en-us_topic_0000001206815912_li723364423517>`.
      -  **check eth1**: Check whether extended network interface eth1 has obtained an IPv6 address (2407:c080:1200:1a9c:7cc0:63b5:8e65:4dd8) every second up to 10 times.
      -  **Add v6 routes for eth1**: Add policy-based routes for the extended network interface. Set the value to be the same as that configured in :ref:`5.a <vpc_nic_0016__en-us_topic_0000001206815912_li723364423517>`.

   d. Press **ESC** to exit and enter **:wq!** to save the configuration.

   e. .. _vpc_nic_0016__en-us_topic_0000001206815912_li1751725414355:

      Run the following command to assign execute permissions to the **/etc/rc.local** file:

      **chmod +x /etc/rc.local**

      .. note::

         If your operating system is Red Hat or EulerOS, run the following command after you perform :ref:`6.e <vpc_nic_0016__en-us_topic_0000001206815912_li1751725414355>`:

         **chmod +x /etc/rc.d/rc.local**

   f. Run the following command to restart the ECS:

      **reboot**

      .. important::

         Policy-based routes added to the **/etc/rc.local** file take effect only after the ECS is restarted. Ensure that workloads on the ECS will not be affected before restarting the ECS.

   g. Repeat :ref:`5.b <vpc_nic_0016__en-us_topic_0000001206815912_li3234144414354>` to :ref:`5.c <vpc_nic_0016__en-us_topic_0000001206815912_li1523514414353>` to check whether the policy-based routes are added and whether the source ECS and the destination ECS can communicate with each other.
