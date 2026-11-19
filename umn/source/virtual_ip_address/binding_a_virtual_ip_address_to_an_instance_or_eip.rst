:original_name: en-us_topic_0067802474.html

.. _en-us_topic_0067802474:

Binding a Virtual IP Address to an Instance or EIP
==================================================

Scenarios
---------

You can bind a virtual IP address to an instance or EIP.

-  Bind a virtual IP address to an instance. You can:

   -  Bind one or more virtual IP addresses to an instance.
   -  Bind a virtual IP address to multiple instances.

-  Bind a virtual IP address to an EIP to enable Internet communications.

Constraints
-----------

-  A virtual IP address can only be bound to one EIP.

Binding a Virtual IP Address to an EIP or ECS on the Console
------------------------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Subnets**.

   The subnet list page is displayed.

#. Click the name with a hyperlink of the subnet that the virtual IP address belongs to.

   The subnet details page is displayed.

#. Click the **IP Addresses** tab.

   -  To bind a virtual IP address to an EIP, locate the row that contains the virtual IP address and click **Bind to EIP** in the **Operation** column.
   -  To bind a virtual IP address to an ECS, locate the row that contains the virtual IP address and click **Bind to Server** in the **Operation** column.

#. Select the EIP or ECS to be bound.

   .. note::

      -  If an ECS has multiple network interfaces, bind the virtual IP address to the primary network interface.
      -  The network interface of an ECS can have multiple virtual IP addresses bound.

#. Click **OK**.

   .. important::

      After a virtual IP address is bound to the network interface of an ECS, you need to manually configure the virtual IP address on the ECS. For details, see :ref:`Configuring a Virtual IP Address for an ECS <en-us_topic_0067802474__section896472025412>`.

.. _en-us_topic_0067802474__section896472025412:

Configuring a Virtual IP Address for an ECS
-------------------------------------------

After you bind one or more virtual IP addresses to an ECS on the console, you must log in to the ECS to manually configure these virtual IP addresses.

The following OSs are used as examples here. For other OSs, see the help documentation on their official websites.

-  Linux: CentOS 8.2 64bit and Ubuntu 22.04 server 64bit
-  Windows: Windows Server

CentOS
------

The following uses CentOS 8.2 64bit as an example.

#. .. _en-us_topic_0067802474__li1096462055417:

   Obtain the network interface that the virtual IP address is to be bound and the connection of the network interface:

   **nmcli connection**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-centos ~]# nmcli connection
      NAME         UUID                                  TYPE      DEVICE
      System eth0  5fb06bd0-0bb0-7ffb-45f1-d6edd65f3e03  ethernet  eth0
      System eth1  9c92fad9-6ecb-3e6c-eb4d-8a47c6f50c04  ethernet  --
      System eth2  3a73717e-65ab-93e8-b518-24f5af32dc0d  ethernet  --
      System eth3  c5ca8081-6db2-4602-4b46-d771f4330a6d  ethernet  --
      System eth4  84d43311-57c8-8986-f205-9c78cd6ef5d2  ethernet  --

   The command output in this example is described as follows:

   -  **eth0** in the **DEVICE** column indicates the network interface that the virtual IP address is to be bound.
   -  **System eth0** in the **NAME** column indicates the connection of the network interface.

#. .. _en-us_topic_0067802474__li19964420105413:

   Add the virtual IP address for the connection:

   **nmcli connection modify "**\ *connection-name-of-the-network-interface*\ **"** **+ipv4.addresses** *virtual-IP-address*

   Configure the parameters as follows:

   -  *connection-name-of-the-network-interface*: The connection name of the network interface obtained in :ref:`1 <en-us_topic_0067802474__li1096462055417>`. In this example, the connection name is **System eth0**.
   -  *virtual-IP-address*: The virtual IP address to be added. If you add multiple virtual IP addresses at a time, separate every two with a comma (,).

   Example commands:

   -  Adding a single virtual IP address: **nmcli connection modify "System eth0" +ipv4.addresses 192.168.0.22**
   -  Adding multiple virtual IP addresses: **nmcli connection modify "System eth0" +ipv4.addresses 192.168.0.22,192.168.0.23**

#. .. _en-us_topic_0067802474__li196482065413:

   Make the configuration in :ref:`2 <en-us_topic_0067802474__li19964420105413>` take effect:

   **nmcli connection up "**\ *connection-name-of-the-network-interface*\ **"**

   Example command:

   **nmcli connection up "System eth0"**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-centos ~]# nmcli connection up "System eth0"
      Connection successfully activated (D-Bus active path: /org/freedesktop/NetworkManager/ActiveConnection/2)

#. Check whether the virtual IP address has been bound:

   **ip a**

   Information similar to the following is displayed. In the command output, virtual IP address **192.168.0.22** is bound to network interface **eth0**.

   .. code-block:: console

      [root@ecs-centos ~]# ip a
      1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
          link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
          inet 127.0.0.1/8 scope host lo
             valid_lft forever preferred_lft forever
          inet6 ::1/128 scope host
             valid_lft forever preferred_lft forever
      2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
          link/ether fa:16:3e:54:ac:fa brd ff:ff:ff:ff:ff:ff
          inet 192.168.0.22/32 scope global noprefixroute eth0
             valid_lft forever preferred_lft forever
          inet 192.168.0.78/24 brd 192.168.0.255 scope global dynamic noprefixroute eth0
             valid_lft 315359994sec preferred_lft 315359994sec
          inet6 fe80::f816:3eff:fe54:acfa/64 scope link
             valid_lft forever preferred_lft forever

   .. note::

      After the preceding configurations are complete, the configurations will not be lost after the ECS is restarted.

      To delete an added virtual IP address, perform the following steps:

      a. Delete the virtual IP address from the connection of the network interface:

         **nmcli connection modify "**\ *connection-name-of-the-network-interface*\ **"** **-ipv4.addresses** *virtual-IP-address*

         To delete multiple virtual IP addresses at a time, separate every two with a comma (,). Example commands are as follows:

         -  Deleting a single virtual IP address: **nmcli connection modify "System eth0" -ipv4.addresses 192.168.0.22**
         -  Deleting multiple virtual IP addresses: **nmcli connection modify "System eth0" -ipv4.addresses 192.168.0.22,192.168.0.23**

      b. Make the deletion take effect by referring to :ref:`3 <en-us_topic_0067802474__li196482065413>`.

Ubuntu
------

The following uses Ubuntu 22.04 server 64bit as an example. If the ECS runs **Ubuntu 22** or **Ubuntu 20**, perform the following operations:

#. Obtain and take a note of the network interface that the virtual IP address is to be bound:

   **ifconfig**

   Information similar to the following is displayed. In this example, the network interface with the virtual IP address bound is **eth0**.

   .. code-block::

      root@ecs-X-Ubuntu:~# ifconfig
      eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
              inet 172.16.0.210  netmask 255.255.255.0  broadcast 172.16.0.255
              inet6 fe80::f816:3eff:fe01:f1c3  prefixlen 64  scopeid 0x20<link>
              ether fa:16:3e:01:f1:c3  txqueuelen 1000  (Ethernet)
              RX packets 43915  bytes 63606486 (63.6 MB)
              RX errors 0  dropped 0  overruns 0  frame 0
              TX packets 3364  bytes 455617 (455.6 KB)
              TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
      ...

#. Switch to the **/etc/netplan** directory:

   **cd /etc/netplan**

#. .. _en-us_topic_0067802474__li11965920115418:

   Add a virtual IP address to the network interface.

   a. Open the configuration file **01-netcfg.yaml**:

      **vim 01-netcfg.yaml**

   b. Press **i** to enter the editing mode.

   c. In the network interface configuration area, add a virtual IP address.

      In this example, add a virtual IP address for **eth0**:

      **addresses:**

      **- 172.16.0.26/32**

      The file content is as follows:

      .. code-block::

         network:
             version: 2
             renderer: NetworkManager
             ethernets:
                 eth0:
                     dhcp4: true
                     addresses:
                     - 172.16.0.26/32
                 eth1:
                     dhcp4: true
                 eth2:
                     dhcp4: true
                 eth3:
                     dhcp4: true
                 eth4:
                     dhcp4: true

   d. Press **Esc**, enter **:wq!**, save the configuration, and exit.

#. .. _en-us_topic_0067802474__li17966162010544:

   Make the configuration in :ref:`3 <en-us_topic_0067802474__li11965920115418>` take effect:

   **netplan apply**

#. Check whether the virtual IP address has been bound:

   **ip a**

   Information similar to the following is displayed. In the command output, virtual IP address **172.16.0.26** is bound to network interface **eth0**.

   .. code-block::

      root@ecs-X-Ubuntu:/etc/netplan# ip a
      ...
      2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
          link/ether fa:16:3e:01:f1:c3 brd ff:ff:ff:ff:ff:ff
          altname enp0s3
          altname ens3
          inet 172.16.0.26/32 scope global noprefixroute eth0
             valid_lft forever preferred_lft forever
          inet 172.16.0.210/24 brd 172.16.0.255 scope global dynamic noprefixroute eth0
             valid_lft 107999971sec preferred_lft 107999971sec
          inet6 fe80::f816:3eff:fe01:f1c3/64 scope link
             valid_lft forever preferred_lft forever

   .. note::

      After the preceding configurations are complete, the configurations will not be lost after the ECS is restarted.

      To delete an added virtual IP address, perform the following steps:

      a. Open the configuration file **01-netcfg.yaml** and delete the virtual IP address of the corresponding network interface by referring to :ref:`3 <en-us_topic_0067802474__li11965920115418>`.
      b. Make the deletion take effect by referring to :ref:`4 <en-us_topic_0067802474__li17966162010544>`.

Windows Server
--------------

The following operations use Windows Server as an example.

#. In **Control Panel**, click **Network and Sharing Center**, and click the corresponding local connection.

#. On the displayed page, click **Properties**.

#. On the **Network** tab page, select **Internet Protocol Version 4 (TCP/IPv4)**.

#. Click **Properties**.

#. Select **Use the following IP address** and set **IP address** to the private IP address of the ECS, for example, 10.0.0.101.


   .. figure:: /_static/images/en-us_image_0000002555997613.png
      :alt: **Figure 1** Configuring a private IP address

      **Figure 1** Configuring a private IP address

#. Click **Advanced**.

#. On the **IP Settings** tab, click **Add** in the **IP addresses** area.

   Add the virtual IP address, for example, 10.0.0.154.


   .. figure:: /_static/images/en-us_image_0000002556117589.png
      :alt: **Figure 2** Configuring a virtual IP address

      **Figure 2** Configuring a virtual IP address

#. Click **OK**.

#. In the **Start** menu, open the Windows command line window and run the following command to check whether the virtual IP address has been configured:

   **ipconfig /all**

   In the command output, **IPv4 Address** is the virtual IP address 10.0.0.154, indicating that the virtual IP address of the ECS's network interface has been correctly configured.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865582673.png
