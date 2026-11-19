:original_name: vpc_subeni_0003.html

.. _vpc_subeni_0003:

Creating a Supplementary Network Interface
==========================================

Scenarios
---------

The number of elastic network interfaces that can be attached to each ECS is limited. If this limit cannot meet your requirements, you can use supplementary network interfaces.

Notes and Constraints
---------------------

-  Supplementary network interfaces and its elastic network interface must be in the same VPC but can belong to different subnets and security groups.
-  Before using a supplementary network interface, you need to create VLAN subinterfaces on the network interface of the instance and configure corresponding rules by referring to :ref:`Configuring a Supplementary Network Interface <vpc_subeni_0003__section0831323111013>`.


Creating a Supplementary Network Interface
------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Network Interfaces**.

#. In the upper right corner of the page, click **Create Supplementary Network Interface**.


   .. figure:: /_static/images/en-us_image_0000001818823022.png
      :alt: **Figure 1** Create Supplementary Network Interface

      **Figure 1** Create Supplementary Network Interface

#. Configure the parameters based on :ref:`Table 1 <vpc_subeni_0003__table145313414319>`.

   .. _vpc_subeni_0003__table145313414319:

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Parameter             | Description                                                                                                                                                                 | Example Value                   |
      +=======================+=============================================================================================================================================================================+=================================+
      | Network Interface     | Elastic network interface that the supplementary network interface to be attached to.                                                                                       | --(172.16.0.145)                |
      |                       |                                                                                                                                                                             |                                 |
      |                       | Select an elastic network interface from the drop-down list.                                                                                                                |                                 |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | VPC                   | VPC that the supplementary network interface belongs to. You do not need to set this parameter.                                                                             | vpc-A                           |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Subnet                | Select the subnet for the supplementary network interface.                                                                                                                  | subnet-A01                      |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Description           | (Optional) Enter the description of the supplementary network interface in the text box as required.                                                                        | ``-``                           |
      |                       |                                                                                                                                                                             |                                 |
      |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                         |                                 |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Quantity              | Number of supplementary network interfaces to be created. The value ranges from 1 to 20.                                                                                    | 1                               |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Private IP Address    | Whether to assign a private IPv4 address or IPv6 address to the supplementary network interface. There are two options:                                                     | Private IPv4 network            |
      |                       |                                                                                                                                                                             |                                 |
      |                       | -  **Private IPv4 network**: a private IPv4 address will be assigned. This option is selected by default and cannot be deselected.                                          |                                 |
      |                       |                                                                                                                                                                             |                                 |
      |                       | -  **IPv6 network (Public and private network traffic)**: a private IPv6 address will be assigned. Both private and public IPv6 networks are supported.                     |                                 |
      |                       |                                                                                                                                                                             |                                 |
      |                       |    IPv6 is shown only when IPv6 is enabled for the subnet of the supplementary network interface.                                                                           |                                 |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | IPv4 Address          | How a private IPv4 address will be assigned to the supplementary network interface. There are two options:                                                                  | Automatically assign IP address |
      |                       |                                                                                                                                                                             |                                 |
      |                       | -  **Automatically assign IP address**: The system assigns an IP address from the subnet you have selected.                                                                 |                                 |
      |                       |                                                                                                                                                                             |                                 |
      |                       | -  **Manually specify IP address**: You can specify an IP address.                                                                                                          |                                 |
      |                       |                                                                                                                                                                             |                                 |
      |                       |    If you select **Manually specify IP address**, enter a private IPv4 address.                                                                                             |                                 |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | IPv6 Address          | How a IPv6 address will be assigned to the supplementary network interface if **IPv6 network (Public and private network traffic)** is selected for **Private IP Address**. | Automatically assign IP address |
      |                       |                                                                                                                                                                             |                                 |
      |                       | There are two options:                                                                                                                                                      |                                 |
      |                       |                                                                                                                                                                             |                                 |
      |                       | -  **Automatically assign IP address**: The system assigns an IP address from the subnet you have selected.                                                                 |                                 |
      |                       |                                                                                                                                                                             |                                 |
      |                       | -  **Manually specify IP address**: You can specify an IP address.                                                                                                          |                                 |
      |                       |                                                                                                                                                                             |                                 |
      |                       |    If you select **Manually specify IP address**, enter a IPv6 address.                                                                                                     |                                 |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Security Group        | Security group that the supplementary network interface will be associated with.                                                                                            | sg-001                          |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+

#. Click **OK**.

   .. important::

      After a supplementary network interface is created, you need to create VLAN subinterfaces on the network interface of the instance and configure corresponding routes by referring to :ref:`Configuring a Supplementary Network Interface <vpc_subeni_0003__section0831323111013>`.

.. _vpc_subeni_0003__section0831323111013:

Configuring a Supplementary Network Interface
---------------------------------------------

After a supplementary network interface is created, you need to create a VLAN subinterface for the network interface of the instance and configure a private IP address and default routes for the supplementary network interface.

Before doing so, you need to obtain:

-  The information described in :ref:`Table 2 <vpc_subeni_0003__table16664333135616>` when you configure a supplementary network interface for a Linux ECS.

-  The information described in :ref:`Table 2 <vpc_subeni_0003__table16664333135616>` and :ref:`Table 3 <vpc_subeni_0003__table740019546479>` when you configure a supplementary network interface for a Windows ECS.

   .. _vpc_subeni_0003__table16664333135616:

   .. table:: **Table 2** Information about the supplementary network interface and subnet

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Item                              | How to Obtain                                                                                                                                          |
      +===================================+========================================================================================================================================================+
      | VLAN ID                           | #. In the supplementary network interface list, click the private IP address of the target supplementary network interface.                            |
      |                                   |                                                                                                                                                        |
      |                                   |    The **Summary** page is displayed.                                                                                                                  |
      |                                   |                                                                                                                                                        |
      |                                   | #. On the displayed page, check and record the following information:                                                                                  |
      |                                   |                                                                                                                                                        |
      |                                   |    VLAN ID                                                                                                                                             |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MAC address                       | #. In the supplementary network interface list, click the private IP address of the target supplementary network interface.                            |
      |                                   |                                                                                                                                                        |
      |                                   |    The **Summary** page is displayed.                                                                                                                  |
      |                                   |                                                                                                                                                        |
      |                                   | #. On the displayed page, check and record the following information:                                                                                  |
      |                                   |                                                                                                                                                        |
      |                                   |    MAC address                                                                                                                                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Private IP address                | #. In the supplementary network interface list, click the private IP address of the target supplementary network interface.                            |
      |                                   |                                                                                                                                                        |
      |                                   |    The **Summary** page is displayed.                                                                                                                  |
      |                                   |                                                                                                                                                        |
      |                                   | #. On the displayed page, check and record the following information:                                                                                  |
      |                                   |                                                                                                                                                        |
      |                                   |    Private IP address                                                                                                                                  |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Subnet mask                       | #. In the supplementary network interface list, locate the target supplementary network interface and click the subnet name in the **Network** column. |
      |                                   |                                                                                                                                                        |
      |                                   |    The **Summary** page of the subnet is displayed.                                                                                                    |
      |                                   |                                                                                                                                                        |
      |                                   | #. On the displayed page, check and record the following information:                                                                                  |
      |                                   |                                                                                                                                                        |
      |                                   |    Subnet mask: subnet mask of the IPv4 CIDR block. For example, if the IPv4 CIDR block is 192.168.0.0/24, the mask is 24.                             |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Gateway address                   | #. In the supplementary network interface list, locate the target supplementary network interface and click the subnet name in the **Network** column. |
      |                                   |                                                                                                                                                        |
      |                                   |    The **Summary** page of the subnet is displayed.                                                                                                    |
      |                                   |                                                                                                                                                        |
      |                                   | #. On the displayed page, check and record the following information:                                                                                  |
      |                                   |                                                                                                                                                        |
      |                                   |    Subnet gateway: In the **Gateway and DNS Information** area, check the gateway address.                                                             |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _vpc_subeni_0003__table740019546479:

   .. table:: **Table 3** Information about the network interface and subnet to which the supplementary network interface belongs

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Item                              | How to Obtain                                                                                                              |
      +===================================+============================================================================================================================+
      | MAC address                       | #. In the ECS list, click the name of the ECS with the network interface attached.                                         |
      |                                   |                                                                                                                            |
      |                                   |    The **Summary** page is displayed.                                                                                      |
      |                                   |                                                                                                                            |
      |                                   | #. Switch to the **Network Interface** tab and click |image3| to check and record the following information:               |
      |                                   |                                                                                                                            |
      |                                   |    MAC address                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Private IP address                | #. In the ECS list, click the name of the ECS with the network interface attached.                                         |
      |                                   |                                                                                                                            |
      |                                   |    The **Summary** page is displayed.                                                                                      |
      |                                   |                                                                                                                            |
      |                                   | #. Switch to the **Network Interface** tab and click |image4| to check and record the following information:               |
      |                                   |                                                                                                                            |
      |                                   |    Private IP address                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Subnet mask                       | #. In the network interface list, locate the target network interface and click the subnet name in the **Network** column. |
      |                                   |                                                                                                                            |
      |                                   |    The **Summary** page of the subnet is displayed.                                                                        |
      |                                   |                                                                                                                            |
      |                                   | #. On the displayed page, check and record the following information:                                                      |
      |                                   |                                                                                                                            |
      |                                   |    Subnet mask: subnet mask of the IPv4 CIDR block. For example, if the IPv4 CIDR block is 192.168.0.0/24, the mask is 24. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Gateway address                   | #. In the network interface list, locate the target network interface and click the subnet name in the **Network** column. |
      |                                   |                                                                                                                            |
      |                                   |    The **Summary** page of the subnet is displayed.                                                                        |
      |                                   |                                                                                                                            |
      |                                   | #. On the displayed page, check and record the following information:                                                      |
      |                                   |                                                                                                                            |
      |                                   |    Subnet gateway: In the **Gateway and DNS Information** area, check the gateway address.                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+

Configuring a Supplementary Network Interface for a Linux ECS
-------------------------------------------------------------

The following describes how to create a VLAN subinterface on the network interface of a Linux ECS. CentOS 7.8 is used as an example. In this example, the information about the supplementary network interface and subnet is as follows:

-  VLAN ID: 1937
-  MAC address: fa:16:3e:6d:c5:5a
-  Private IP address: 192.168.0.149
-  Subnet mask: 24
-  Subnet gateway address: 192.168.0.1

.. note::

   This example describes how to configure the supplementary network interface for the primary network interface of an ECS. If you want to do the same thing for the extended network interface of the ECS, follow the similar steps.

#. Log in to the ECS.

#. .. _vpc_subeni_0003__li14111010139:

   Run the following command to check and record the network interface name of the ECS:

   **ifconfig**

   Information similar to the following is displayed. In this example, the network interface name is **eth0**.

   .. code-block:: console

      [root@ecs-subeni-linux ~]# ifconfig
      eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
              inet 192.168.0.125  netmask 255.255.255.0  broadcast 192.168.0.255
              inet6 fe80::f816:3eff:fe6d:c542  prefixlen 64  scopeid 0x20<link>
              ether fa:16:3e:6d:c5:42  txqueuelen 1000  (Ethernet)
              RX packets 78131  bytes 111604802 (106.4 MiB)
              RX errors 0  dropped 0  overruns 0  frame 0
              TX packets 8686  bytes 1422159 (1.3 MiB)
              TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
      ...

#. .. _vpc_subeni_0003__li17301841161514:

   Run the following command to create a VLAN subinterface on the network interface:

   **ip link add link** *<network-interface-name>* **name** *<VLAN-sub-interface-name>* **type vlan id** *<VLAN-ID-of-the-supplementary-network-interface>*

   Variables in the preceding command are as follows:

   -  *network-interface-name*: the network interface name queried in :ref:`2 <vpc_subeni_0003__li14111010139>`. In this example, the name is **eth0**.
   -  *VLAN-subinterface-name*: Name the subinterface in the format of *<network-interface-name>*\ **.**\ *<VLAN-ID-of-the-supplementary-network-interface>*. In this example, the VLAN subinterface name is **eth0.1937**.
   -  *VLAN-ID-of-the-supplementary-network-interface*: In this example, the ID is **1937**.

   Example command:

   **ip link add link eth0 name eth0.1937 type vlan id 1937**

#. Run the following command to create a namespace:

   **ip netns add** *<namespace-name>*

   *namespace-name*: Name it in the format of **ns**\ *<supplementary-network-interface-VLAN-ID>*. In this example, the name is **ns1937**.

   Example command:

   **ip netns add ns1937**

#. Run the following command to add the VLAN subinterface to the namespace:

   **ip link set** *<VLAN-sub-interface-name>* **netns** *<namespace-name>*

   Example command:

   **ip link set eth0.1937 netns ns1937**

#. Run the following command to change the MAC address of the VLAN subinterface to that of the supplementary network interface:

   **ip netns exec** *<namespace-name>* **ifconfig** *<VLAN-sub-interface-name>* **hw ether** *<MAC-address-of-the-supplementary-network-interface>*

   Example command:

   **ip netns exec ns1937 ifconfig eth0.1937 hw ether fa:16:3e:6d:c5:5a**

#. Run the following command to enable the VLAN subinterface:

   **ip netns exec** *<namespace-name>* **ifconfig** *<VLAN-sub-interface-name>* **up**

   Example command:

   **ip netns exec ns1937 ifconfig eth0.1937 up**

#. Run the following command to configure a private IP address for the VLAN subinterface:

   **ip netns exec** *<namespace-name>* **ip addr add** *<private-IP-address>* **dev** *<VLAN-sub-interface-name>*

   *private-IP-address*: private IP address of the supplementary network interface/subnet mask. In this example, the value is **192.168.0.149/24**.

   Example command:

   **ip netns exec ns1937 ip addr add 192.168.0.149/24 dev eth0.1937**

#. .. _vpc_subeni_0003__li2735105892714:

   Run the following command to configure the default route for the VLAN subinterface

   **ip netns exec** *<namespace-name>* **ip route add default via** *<gateway-address-of-the-subnet-where-the-supplementary-network-interface-is-created>*

   Example command:

   **ip netns exec ns1937 ip route add default via 192.168.0.1**

#. .. _vpc_subeni_0003__li615191883116:

   Check whether the supplementary network interface has worked.

   a. Run the following command to verify the connectivity between network interface and the test ECS:

      **ping** *<private-IP-address-of-the-test-ECS>*

      Plan the same VPC and security group for the test ECS and the ECS with network interface **eth0** attached, so that the two ECSs can communicate with each other by default.

      Example command:

      **ping 192.168.0.133**

      If information similar to the following is displayed, the two ECSs can communicate with each other. If the communication is normal, proceed with :ref:`10.b <vpc_subeni_0003__li26161740173611>`.

      .. code-block:: console

         [root@ecs-subeni-linux ~]# ping 192.168.0.133
         PING 192.168.0.133 (192.168.0.133) 56(84) bytes of data.
         64 bytes from 192.168.0.133: icmp_seq=1 ttl=64 time=0.302 ms
         64 bytes from 192.168.0.133: icmp_seq=2 ttl=64 time=0.262 ms
         ...
         --- 192.168.0.133 ping statistics ---
         2 packets transmitted, 2 received, 0% packet loss, time 999ms
         rtt min/avg/max/mdev = 0.262/0.282/0.302/0.020 ms

   b. .. _vpc_subeni_0003__li26161740173611:

      Run the following command to verify the connectivity between the supplementary network interface and the test ECS:

      **ip netns exec** *<namespace-name>* **ping** *<private-IP-address-of-the-test-ECS>*

      Plan the same VPC and security group for the test ECS and the ECS with the supplementary network interface attached, so that the two ECSs can communicate with each other by default.

      Example command:

      **ip netns exec ns1937 ping 192.168.0.133**

      If information similar to the following is displayed, the two ECSs can communicate with each other. This means the supplementary network interface has worked.

      .. code-block:: console

         [root@ecs-subeni-linux ~]# ip netns exec ns1937 ping 192.168.0.133
         PING 192.168.0.133 (192.168.0.133) 56(84) bytes of data.
         64 bytes from 192.168.0.133: icmp_seq=1 ttl=64 time=0.420 ms
         64 bytes from 192.168.0.133: icmp_seq=2 ttl=64 time=0.233 ms
         ...
         --- 192.168.0.133 ping statistics ---
         2 packets transmitted, 2 received, 0% packet loss, time 999ms
         rtt min/avg/max/mdev = 0.233/0.326/0.420/0.095 ms

   .. important::

      -  The route configured above is a temporary route that is applied once configured, and will be lost after ECS restarts. To avoid network disruptions, take step :ref:`11 <vpc_subeni_0003__li18679924114013>` to configure permanent routes instead.
      -  If the ECS needs to access a public domain name through the supplementary network interface, you need to take step :ref:`11 <vpc_subeni_0003__li18679924114013>` to configure DNS for that supplementary network interface and then restart the ECS.

11. .. _vpc_subeni_0003__li18679924114013:

    Configure a permanent route and DNS for the supplementary network interface. The configuration will work after the ECS is restarted.

    a. Configure a permanent route for the supplementary network interface.

       #. Run the following command to open the **/etc/rc.local** file:

          **vi /etc/rc.local**

       #. Press **i** to enter editing mode.

       #. Add the following content to the end of the file.

          The parameters and values must be the same as those in steps :ref:`3 <vpc_subeni_0003__li17301841161514>` to :ref:`9 <vpc_subeni_0003__li2735105892714>`.

          .. code-block::

             ip link add link eth0 name eth0.1937 type vlan id 1937
             ip netns add ns1937
             ip link set eth0.1937 netns ns1937
             ip netns exec ns1937 ifconfig eth0.1937 hw ether fa:16:3e:6d:c5:5a
             ip netns exec ns1937 ifconfig eth0.1937 up
             ip netns exec ns1937 ip addr add 192.168.0.149/24 dev eth0.1937
             ip netns exec ns1937 ip route add default via 192.168.0.1

       #. Press **Esc** to exit and enter **:wq!** to save the configuration.

       #. .. _vpc_subeni_0003__li450595617442:

          Run the following command to assign execute permissions to the **/etc/rc.local** file:

          **chmod +x /etc/rc.local**

          .. note::

             If your operating system is Red Hat or EulerOS, run the following command after you perform :ref:`11.a.v <vpc_subeni_0003__li450595617442>`:

             **chmod +x /etc/rc.d/rc.local**

    b. (Optional) Configure DNS for the supplementary network interface if the ECS needs to access the public domain name through the supplementary network interface.

       If DNS resolution is not required, take step :ref:`11.c <vpc_subeni_0003__li1288045695220>` to restart the ECS.

       #. Run the following command to go to the **/etc/sysconfig/network-scripts/** directory that stores the network interface configuration file:

          **cd /etc/sysconfig/network-scripts/**

       #. Run the following command to modify the network interface configuration file:

          **vi ifcfg-**\ *<network-interface-name>*

          *network-interface-name*: the name queried in :ref:`2 <vpc_subeni_0003__li14111010139>`. In this example, the name is **vi ifcfg-eth0**.

       #. Press **i** to enter the editing mode.

       #. Add the following content to the end of the file.

          **114.114.114.114** is the public recursive DNS address.

          .. code-block::

             DNS1=114.114.114.114

       #. Press **Esc** to exit and enter **:wq!** to save the configuration.

    c. .. _vpc_subeni_0003__li1288045695220:

       Run the following command to restart the ECS:

       **reboot**

    d. Check whether the permanent route has worked by referring to :ref:`10 <vpc_subeni_0003__li615191883116>`.

    e. (Optional) If DNS is configured, check whether the DNS configuration has worked.

       #. Bind an EIP to the supplementary network interface by referring to :ref:`Binding or Unbinding a Supplementary Network Interface to or from an EIP <vpc_subeni_0004>`.

       #. Run the following command to check whether the supplementary network interface can access the public domain name:

          **ip netns exec** *<namespace-name>* **ping** *<public-domain-name>*

12. (Optional) Remotely log in to the ECS using the private IP address of the supplementary network interface.

    a. Add an inbound rule to allow traffic over SSH port 22 to the security group associated with the supplementary network interface.

       For details, see :ref:`Adding a Security Group Rule <en-us_topic_0030969470>`.

       .. table:: **Table 4** A security group rule that allows traffic over SSH port 22

          +-----------+------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
          | Direction | Type | Protocol & Port | Source                                                                                                                                                          |
          +===========+======+=================+=================================================================================================================================================================+
          | Inbound   | IPv4 | TCP: 22         | Set the IP address based on service requirements. For example, to remotely log in to the ECS from a local PC, set the source to the IP address of the local PC. |
          +-----------+------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

    b. Run the following command to check whether port 22 in the namespace is listened on:

       **ip netns exec** *<namespace-name>* **netstat -antp \| grep 22**

       Example command:

       **ip netns exec ns1937 netstat -antp \| grep 22**

       -  If the command output is empty, port 22 in the namespace is not listened on. Go to :ref:`12.c <vpc_subeni_0003__li189011359152210>`.

       -  If information similar to the following is displayed, port 22 is listened on. No further action is required.

          .. code-block:: console

             [root@ecs-subeni-linux ~]# ip netns exec ns1937 netstat -antp | grep 22
             tcp        0      0 0.0.0.0:22        0.0.0.0:*        LISTEN      2797/sshd
             tcp6       0      0 :::22            :::*             LISTEN      2979/sshd

    c. .. _vpc_subeni_0003__li189011359152210:

       Run the following command to start the SSH service and enable listening port 22:

       **ip netns exec** *<namespace-name>* **/sbin/sshd**

       Example command:

       **ip netns exec ns1937 /sbin/sshd**

    d. Run the following command to check whether port 22 in the namespace is listened on:

       **ip netns exec** *<namespace-name>* **netstat -antp \| grep 22**

       Example command:

       **ip netns exec ns1937 netstat -antp \| grep 22**

       If information similar to the following is displayed, port 22 is listened on:

       .. code-block:: console

          [root@ecs-subeni-linux ~]# ip netns exec ns1937 netstat -antp | grep 22
          tcp        0      0 0.0.0.0:22        0.0.0.0:*        LISTEN      2797/sshd
          tcp6       0      0 :::22            :::*             LISTEN      2979/sshd

13. (Optional) Allow traffic over HTTP port 80 of the supplementary network interface if the ECS needs to provide the web service through the supplementary network interface.

    a. Add an inbound rule to allow traffic over HTTP port 80 to the security group associated with the supplementary network interface.

       For details, see :ref:`Adding a Security Group Rule <en-us_topic_0030969470>`.

       .. table:: **Table 5** A security group rule that allows traffic over HTTP port 80

          +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------+
          | Direction       | Type            | Protocol & Port | Source                                                                            |
          +=================+=================+=================+===================================================================================+
          | Inbound         | IPv4            | TCP: 80         | 0.0.0.0/0                                                                         |
          |                 |                 |                 |                                                                                   |
          |                 |                 |                 | Allows any IP address to access the supplementary network interface over port 80. |
          +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------+

    b. Run the following command to check whether port 80 in the namespace is listened on:

       **ip netns exec** *<namespace-name>* **netstat -antp \| grep 80**

       Example command:

       **ip netns exec ns1937 netstat -antp \| grep 80**

       -  If the command output is empty, port 80 in the namespace is not listened on. In this case, enable port 80 for the web service.

       -  If information similar to the following is displayed, port 80 is listened on. No further operation is required.

          .. code-block:: console

             [root@ecs-subeni-linux ~]# ip netns exec ns1937 netstat -antp | grep 80
             tcp6       0      0 :::80            :::*             LISTEN      ...

Configuring a Supplementary Network Interface for a Windows ECS
---------------------------------------------------------------

The following describes how to create a VLAN subinterface on the network interface of a Windows ECS. Windows Server 2019 Standard 64bit is used as an example. In this example, the information about the supplementary network interface, primary network interface, and subnet is as follows:

-  Supplementary network interface

   -  VLAN ID: 2242
   -  MAC address: fa:16:3e:6d:c5:db
   -  Private IP address: 192.168.0.22
   -  Subnet mask: 24 (255.255.255.0)
   -  Subnet gateway address: 192.168.0.1

-  Network interface

   -  MAC address: fa:16:3e:6d:c5:d5
   -  Private IP address: 192.168.0.16
   -  Subnet mask: 24 (255.255.255.0)
   -  Subnet gateway address: 192.168.0.1

   .. note::

      This example describes how to configure the supplementary network interface for the primary network interface of an ECS. If you want to do the same thing for the extended network interface of the ECS, follow the similar steps.

#. Log in to the ECS.

#. Enter **Windows PowerShell** in the search box in the lower left corner of the desktop and press **Enter**.

#. On the displayed window, run the following command to query the Ethernet adapter information of the network interface:

   **ipconfig**

   Information similar to the following is displayed. In this example, the Ethernet adapter name is **tap7888b905-ee**.

   |image5|

#. Create a bond group.

   a. .. _vpc_subeni_0003__li1515713256509:

      Run the following command to create a bond group for the custom VLAN:

      **New-NetLbfoTeam -Name** *<bond-group-name>* **-TeamMembers "**\ *<Ethernet-adapter-name-of-the-network-interface>*\ **" -TeamingMode SwitchIndependent -LoadBalancingAlgorithm IPAddresses -Confirm:$false**

      Variables in the preceding command are as follows:

      -  *bond-group-name*: the bond group name of the custom VLAN. In this example, the bond group name is **Team1**.
      -  *Ethernet-adapter-name-of-the-network-interface*: information queried in :ref:`3 <vpc_subeni_0003__li17301841161514>`. In this example, the name is **tap7888b905-ee**.

      Example command:

      **New-NetLbfoTeam -Name Team1 -TeamMembers "tap7888b905-ee" -TeamingMode SwitchIndependent -LoadBalancingAlgorithm IPAddresses -Confirm:$false**

      Information similar to the following is displayed:

      |image6|

   b. Run the following commands to query the bond group you have created:

      **Get-NetLbfoTeamMember**

      Information similar to the following is displayed:

      |image7|

      **Get-NetAdapter**

      Information similar to the following is displayed:

      |image8|

#. Configure a custom VLAN network.

   a. .. _vpc_subeni_0003__li3371142095513:

      Run the following command to create a VLAN subinterface:

      **Add-NetLbfoTeamNIC -Team "**\ *<bond-group-name>*\ **" -VlanID** *<VLAN-ID-of-the-supplementary-network-interface>* **-Confirm:$false**

      Example command:

      **Add-NetLbfoTeamNIC -Team "Team1" -VlanID 2242 -Confirm:$false**

      Information similar to the following is displayed:

      |image9|

   b. Run the following command to open the **Network Connections** page:

      **ncpa.cpl**

      On the displayed page, **Team1** is the bond group created in :ref:`4.a <vpc_subeni_0003__li1515713256509>`, and **Team1 - VLAN 2242** is the VLAN sub-interface created in :ref:`5.a <vpc_subeni_0003__li3371142095513>`.

      |image10|

#. Configure the network for the network interface.

   a. On the **Network Connections** page, double-click **Team1**.

      The **Team1 Status** page is displayed.

      |image11|

   b. On the **Team1 Status** page, click **Properties**.

      The **Team1 Properties** page is displayed.

      |image12|

   c. On the **Team1 Properties** page, click **Configure...**.

      The **Microsoft Network Adapter Multiplexor Driver Properties** page is displayed.

      |image13|

   d. On the **Microsoft Network Adapter Multiplexor Driver Properties** page, choose the **Advanced** tab, click **MAC Address**, enter the MAC address of the network interface, and click **OK**.

      When entering the MAC address, remove the colons (:) and use the uppercase letters. For example, if the MAC address of the network interface is **fa:16:3e:6d:c5:d5**, enter **FA163E6DC5D5**.

      |image14|

   e. Return to the **Team1 Properties** page, double-click **Internet Protocol Version 4 (TCP/IPv4)**.

      The **Internet Protocol Version 4 (TCP/IPv4) Properties** page is displayed.

      |image15|

      |image16|

   f. On the **Internet Protocol Version 4 (TCP/IPv4) Properties** page, configure the network information of the network interface and click **OK**.

      -  Select **Use the following IP address:**.
      -  **IP address**: Enter the private IP address of the network interface. In this example, the private IP address is **192.168.0.16**.
      -  **Subnet mask**: Enter the mask of the subnet where the network interface is created. In this example, the mask is **255.255.255.0**.
      -  **Default gateway**: Enter the gateway of the subnet where the network interface is created. In this example, the gateway is **192.168.0.1**.

      |image17|

   g. On the **Team1 Properties** page, click **OK** to save the settings.

      |image18|

   h. Return to the **Team1 Status** page and click **Details...**.

      On the **Network Connection Details** page, check whether the following information is correctly configured:

      -  **Physical Address**: MAC address of the network interface.
      -  **IPv4 Address**: the private IP address of the network interface.
      -  **IPv4 Subnet Mask**: the mask of the subnet where the network interface is created.
      -  **IPv4 Default Gateway**: the gateway of the subnet where the network interface is created.

      |image19|

      |image20|

   i. Check the settings and click **Close**.

      The **Network Connections** page is displayed.

      |image21|

#. Configure the network for the supplementary network interface.

   a. On the **Network Connections** page, double-click **Team1 - VLAN 2242**.

      The **Team1 - VLAN 2242 Status** page is displayed.

      |image22|

   b. On the **Team1 - VLAN 2242 Status** page, click **Properties**.

      The **Team1 - VLAN 2242 Properties** page is displayed.

      |image23|

   c. On the **Team1 - VLAN 2242 Properties** page, click **Configure...**.

      The **Microsoft Network Adapter Multiplexor Driver #2 Properties** page is displayed.

      |image24|

   d. On the **Microsoft Network Adapter Multiplexor Driver #2 Properties** page, choose the **Advanced** tab, click **MAC Address**, enter the MAC address of the supplementary network interface, and click **OK**.

      When entering the MAC address, remove the colons (:) and use the uppercase letters. For example, if the MAC address of the supplementary network interface is **fa:16:3e:6d:c5:db**, enter **FA163E6DC5DB**.

      |image25|

   e. Return to the **Team1 - VLAN 2242 Properties** page, double-click **Internet Protocol Version 4 (TCP/IPv4)**.

      The **Internet Protocol Version 4 (TCP/IPv4) Properties** page is displayed.

      |image26|

      |image27|

   f. On the **Internet Protocol Version 4 (TCP/IPv4) Properties** page, configure the network information of the supplementary network interface and click **OK**.

      -  Select **Use the following IP address:**.
      -  **IP address**: Enter the private IP address of the supplementary network interface. In this example, the private IP address is **192.168.0.22**.
      -  **Subnet mask**: Enter the mask of the subnet where the supplementary network interface is created. In this example, the mask is **255.255.255.0**.
      -  **Default gateway**: Enter the gateway of the subnet where the supplementary network interface is created. In this example, the gateway is **192.168.0.1**.

      |image28|

      If the following warning is displayed, click **Yes** to close the dialog box.

      |image29|

   g. On the **Team1 - VLAN 2242 Properties** page, click **OK** to save the settings.

      |image30|

   h. Return to the **Team1 - VLAN 2242 Status** page and click **Details...**.

      On the **Network Connection Details** page, check whether the following information is correctly configured:

      -  **Physical Address**: MAC address of the supplementary network interface.
      -  **IPv4 Address**: the private IP address of the supplementary network interface.
      -  **IPv4 Subnet Mask**: the mask of the subnet where the supplementary network interface is created.
      -  **IPv4 Default Gateway**: the gateway of the subnet where the supplementary network interface is created.

      |image31|

      |image32|

   i. Check the settings and click **Close**.

#. On the Windows PowerShell CLI page, check whether the network interface and supplementary network interface are connected to the test ECS.

   a. Run the following command to verify the connectivity between network interface and the test ECS:

      **Ping** *<private-IP-address-of-the-test-ECS>* **-S** *<private-IP-address-of-the-network-interface>*

      Plan the same VPC and security group for the test ECS and the ECS with network interface **eth0** attached, so that the two ECSs can communicate with each other by default.

      Example command:

      **Ping 192.168.0.133 -S 192.168.0.16**

      If information similar to the following is displayed, the two ECSs can communicate with each other.

      |image33|

   b. Run the following command to verify the connectivity between the supplementary network interface and the test ECS:

      **Ping** *<private-IP-address-of-the-test-ECS>* **-S** *<private-IP-address-of-the-supplementary-network-interface>*

      Plan the same VPC and security group for the test ECS and the ECS with the supplementary network interface attached, so that the two ECSs can communicate with each other by default.

      Example command:

      **Ping 192.168.0.133 -S 192.168.0.22**

      If information similar to the following is displayed, the two ECSs can communicate with each other.

      |image34|

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823018.png
.. |image3| image:: /_static/images/en-us_image_0000002171013500.png
.. |image4| image:: /_static/images/en-us_image_0000002219534885.png
.. |image5| image:: /_static/images/en-us_image_0000002171181112.png
.. |image6| image:: /_static/images/en-us_image_0000002206461969.png
.. |image7| image:: /_static/images/en-us_image_0000002171021384.png
.. |image8| image:: /_static/images/en-us_image_0000002206347557.png
.. |image9| image:: /_static/images/en-us_image_0000002171181120.png
.. |image10| image:: /_static/images/en-us_image_0000002206461977.png
.. |image11| image:: /_static/images/en-us_image_0000002171021388.png
.. |image12| image:: /_static/images/en-us_image_0000002206347561.png
.. |image13| image:: /_static/images/en-us_image_0000002171181124.png
.. |image14| image:: /_static/images/en-us_image_0000002206461989.png
.. |image15| image:: /_static/images/en-us_image_0000002171021396.png
.. |image16| image:: /_static/images/en-us_image_0000002206347565.png
.. |image17| image:: /_static/images/en-us_image_0000002171181128.png
.. |image18| image:: /_static/images/en-us_image_0000002206461993.png
.. |image19| image:: /_static/images/en-us_image_0000002171021400.png
.. |image20| image:: /_static/images/en-us_image_0000002206347569.png
.. |image21| image:: /_static/images/en-us_image_0000002171181136.png
.. |image22| image:: /_static/images/en-us_image_0000002206461997.png
.. |image23| image:: /_static/images/en-us_image_0000002171021404.png
.. |image24| image:: /_static/images/en-us_image_0000002206347577.png
.. |image25| image:: /_static/images/en-us_image_0000002171181144.png
.. |image26| image:: /_static/images/en-us_image_0000002206462001.png
.. |image27| image:: /_static/images/en-us_image_0000002171021408.png
.. |image28| image:: /_static/images/en-us_image_0000002206347581.png
.. |image29| image:: /_static/images/en-us_image_0000002171181148.png
.. |image30| image:: /_static/images/en-us_image_0000002206462009.png
.. |image31| image:: /_static/images/en-us_image_0000002171021416.png
.. |image32| image:: /_static/images/en-us_image_0000002206347585.png
.. |image33| image:: /_static/images/en-us_image_0000002171181152.png
.. |image34| image:: /_static/images/en-us_image_0000002206462013.png
