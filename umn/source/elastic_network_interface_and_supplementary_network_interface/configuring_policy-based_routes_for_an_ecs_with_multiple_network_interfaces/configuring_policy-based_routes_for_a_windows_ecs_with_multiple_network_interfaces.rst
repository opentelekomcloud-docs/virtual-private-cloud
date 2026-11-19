:original_name: vpc_nic_0017.html

.. _vpc_nic_0017:

Configuring Policy-based Routes for a Windows ECS with Multiple Network Interfaces
==================================================================================

Scenarios
---------

This section describes how to configure policy-based routes for a Windows Server 2012 64-bit ECS with two network interfaces.

-  IPv4: :ref:`Configuring IPv4 Policy-based Routes for a Windows ECS <vpc_nic_0017__en-us_topic_0000001251535881_section20907123285010>`
-  IPv6: :ref:`Configuring IPv6 Policy-based Routes for a Windows ECS <vpc_nic_0017__en-us_topic_0000001251535881_section5956333121217>`

For details about the background knowledge and networking of an ECS with two network interfaces, see :ref:`Overview <vpc_nic_0014>`.

.. _vpc_nic_0017__en-us_topic_0000001251535881_section20907123285010:

Configuring IPv4 Policy-based Routes for a Windows ECS
------------------------------------------------------

#. .. _vpc_nic_0017__en-us_topic_0000001251535881_li55021158174319:

   Collect the ECS network information required for configuring policy-based routes.

   For details, see :ref:`Collecting ECS Network Information <vpc_nic_0015>`.

   In this example, the network information of the ECS is shown in :ref:`Table 1 <vpc_nic_0017__en-us_topic_0000001251535881_table13529103181915>`.

   .. _vpc_nic_0017__en-us_topic_0000001251535881_table13529103181915:

   .. table:: **Table 1** Windows ECS using IPv4

      +-----------------------+-----------------------------+-----------------------------+
      | ECS                   | Primary Network Interface   | Extended Network Interface  |
      +=======================+=============================+=============================+
      | Source                | -  IP address: 10.0.0.59    | -  IP address: 10.0.1.104   |
      |                       | -  Subnet gateway: 10.0.0.1 | -  Subnet gateway: 10.0.1.1 |
      +-----------------------+-----------------------------+-----------------------------+
      | Destination           | IP address: 10.0.2.12       | N/A                         |
      +-----------------------+-----------------------------+-----------------------------+

#. Log in to the source ECS.

3. Check whether the source ECS can use its primary network interface to communicate with the destination ECS:

   **Before configuring policy-based routes, ensure that the source ECS can use its primary network interface to communicate with the destination ECS.**

   **ping -S** *<IP-address-of-the-primary-network-interface-on-the-source-ECS>* *<IP-address-of-the-destination-ECS>*

   In this example, run the following command:

   **ping -S 10.0.0.59 10.0.2.12**

   If information similar to the following is displayed, the source ECS can use its primary network interface to communicate with the destination ECS.

   |image1|

4. Configure a policy-based route for the extended network interface.

   **route add -p 0.0.0.0 mask 0.0.0.0** *<subnet-gateway-of-the-extended-network-interface>* **metric** *<route-priority>*

   Configure the parameters as follows:

   -  **0.0.0.0/0**: Default route. Do not change it.
   -  Subnet gateway of the extended network interface: Enter the IP address collected in :ref:`1 <vpc_nic_0017__en-us_topic_0000001251535881_li55021158174319>`.
   -  Route priority: Set its value to 261. The priority of the extended network interface must be lower than that of the primary network interface. A larger value indicates a lower priority.

   In this example, run the following command:

   **route add -p 0.0.0.0 mask 0.0.0.0 10.0.1.1 metric** **261**

   .. note::

      -  The primary network interface already has policy-based routes and you do not need to configure again.
      -  If the ECS has multiple extended network interfaces, configure policy-based routes for all extended network interfaces one by one.

5. Check whether the policy-based route is added.

   **route print**

   If information similar to the following is displayed, the policy-based route has been added. The route is a permanent route and will not be lost after the ECS is restarted.

   |image2|

6. Check whether the source and destination ECSs can communicate with each other.

   **ping -S** *<IP-address-of-the-primary-network-interface-on-the-source-ECS>* *<IP-address-of-the-destination-ECS>*

   **ping -S** *<IP-address-of-the-extended-network-interface-on-the-source-ECS>* *<IP-address-of-the-destination-ECS>*

   In this example, run the following commands:

   **ping -S 10.0.0.59 10.0.2.12**

   **ping -S 10.0.1.104 10.0.2.12**

   If information similar to the following is displayed, both the network interfaces of the source ECS can communicate with the destination ECS.

   |image3|

.. _vpc_nic_0017__en-us_topic_0000001251535881_section5956333121217:

Configuring IPv6 Policy-based Routes for a Windows ECS
------------------------------------------------------

#. Collect the ECS network information required for configuring policy-based routes.

   For details, see :ref:`Collecting ECS Network Information <vpc_nic_0015>`.

   In this example, the network information of the ECS is shown in :ref:`Table 2 <vpc_nic_0017__en-us_topic_0000001251535881_table118303388417>`.

   .. _vpc_nic_0017__en-us_topic_0000001251535881_table118303388417:

   .. table:: **Table 2** Windows ECS using IPv6

      +-------------+---------------------------------------------------+---------------------------------------------------+
      | ECS         | Primary Network Interface                         | Extended Network Interface                        |
      +=============+===================================================+===================================================+
      | Source      | IP address: 2407:c080:802:aba:6788:fb94:d71f:8deb | IP address: 2407:c080:802:be6:71c8:42e0:d44e:eeb4 |
      +-------------+---------------------------------------------------+---------------------------------------------------+
      | Destination | IP address: 2407:c080:802:be7:c2e6:d99c:b685:c6c8 | N/A                                               |
      +-------------+---------------------------------------------------+---------------------------------------------------+

#. Log in to the source ECS.

3. Run the following command to check whether the ECS has IPv6 enabled and has IPv6 addresses:

   **ipconfig**

   If information similar to the following is displayed, each network interface has an IPv6 address starting with 2407, which indicates that the ECS has been assigned IPv6 addresses.

   |image4|

   .. important::

      Perform this step for both the source and destination ECSs to ensure that the ECSs have IPv6 addresses. Otherwise, the ECSs cannot communicate with each other using IPv6 addresses.

4. Check whether the source and destination ECSs can communicate with each other.

   **ping -6 -S** *<IP-address-of-the-primary-network-interface-on-the-source-ECS>* *<IP-address-of-the-destination-ECS>*

   **ping -6 -S** *<IP-address-of-the-extended-network-interface-on-the-source-ECS>* *<IP-address-of-the-destination-ECS>*

   In this example, run the following commands:

   **ping -6 -S 2407:c080:802:aba:8999:5e61:e19:cf7e 2407:c080:802:be7:c2e6:d99c:b685:c6c8**

   **ping -6 -S 2407:c080:802:be6:ec23:ec4:c886:cc1 2407:c080:802:be7:c2e6:d99c:b685:c6c8**

   If information similar to the following is displayed, both the network interfaces of the source ECS can communicate with the destination ECS.

   |image5|

   .. important::

      ECSs in this example run Windows Server 2012 (64-bit). You do not need to configure policy-based routes for these ECSs because both the network interfaces of such an ECS can communicate with others using IPv6.

.. |image1| image:: /_static/images/en-us_image_0000002207227401.png
.. |image2| image:: /_static/images/en-us_image_0000002207353021.png
.. |image3| image:: /_static/images/en-us_image_0000002172106590.png
.. |image4| image:: /_static/images/en-us_image_0000002171946862.png
.. |image5| image:: /_static/images/en-us_image_0000002207227413.png
