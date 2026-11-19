:original_name: vpc_nic_0015.html

.. _vpc_nic_0015:

Collecting ECS Network Information
==================================

Scenarios
---------

Before configuring policy-based routes for an ECS with multiple network interfaces, you need to collect network information about the ECS.

-  :ref:`Table 1 <vpc_nic_0015__en-us_topic_0000001251730713_table02681556143>` lists the information to be collected for a Linux ECS using IPv4.

   .. _vpc_nic_0015__en-us_topic_0000001251730713_table02681556143:

   .. table:: **Table 1** Linux ECS using IPv4

      +-----------------+-----------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | ECS             | Primary Network Interface   | Extended Network Interface  | How to Obtain                                                                                                                 |
      +=================+=============================+=============================+===============================================================================================================================+
      | Source          | -  IP address: 10.0.0.115   | -  IP address: 10.0.1.183   | -  :ref:`Obtaining ECS Network Interface Addresses <vpc_nic_0015__en-us_topic_0000001251730713_section14494516152812>`        |
      |                 | -  Subnet: 10.0.0.0/24      | -  Subnet: 10.0.1.0/24      | -  :ref:`Obtaining Subnet CIDR Blocks and Gateway Addresses <vpc_nic_0015__en-us_topic_0000001251730713_section347012134286>` |
      |                 | -  Subnet gateway: 10.0.0.1 | -  Subnet gateway: 10.0.1.1 |                                                                                                                               |
      +-----------------+-----------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | Destination     | IP address: 10.0.2.12       | N/A                         |                                                                                                                               |
      +-----------------+-----------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------+

-  :ref:`Table 2 <vpc_nic_0015__en-us_topic_0000001251730713_table13529103181915>` lists the information to be collected for a Windows ECS using IPv4.

   .. _vpc_nic_0015__en-us_topic_0000001251730713_table13529103181915:

   .. table:: **Table 2** Windows ECS using IPv4

      +-----------------+-----------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | ECS             | Primary Network Interface   | Extended Network Interface  | How to Obtain                                                                                                                 |
      +=================+=============================+=============================+===============================================================================================================================+
      | Source          | -  IP address: 10.0.0.59    | -  IP address: 10.0.1.104   | -  :ref:`Obtaining ECS Network Interface Addresses <vpc_nic_0015__en-us_topic_0000001251730713_section14494516152812>`        |
      |                 | -  Subnet gateway: 10.0.0.1 | -  Subnet gateway: 10.0.1.1 | -  :ref:`Obtaining Subnet CIDR Blocks and Gateway Addresses <vpc_nic_0015__en-us_topic_0000001251730713_section347012134286>` |
      +-----------------+-----------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | Destination     | IP address: 10.0.2.12       | N/A                         |                                                                                                                               |
      +-----------------+-----------------------------+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------+

.. important::

   The above information is only for your reference.

.. _vpc_nic_0015__en-us_topic_0000001251730713_section14494516152812:

Obtaining ECS Network Interface Addresses
-----------------------------------------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click **Service List** and choose **Computing** > **Elastic Cloud Server**.

4. In the ECS list, click the target ECS name.

   The **Summary** tab page of the ECS is displayed.

5. In the **NICs** area, view the IP addresses of the primary and extended network interfaces.

.. _vpc_nic_0015__en-us_topic_0000001251730713_section347012134286:

Obtaining Subnet CIDR Blocks and Gateway Addresses
--------------------------------------------------

#. Log in to the management console.
#. Click |image2| in the upper left corner and select the desired region and project.
#. Click **Service List** and choose **Computing** > **Elastic Cloud Server**.

4. In the ECS list, click the target ECS name.

   The **Summary** tab page of the ECS is displayed.

5. In the **ECS Information** area, click the name of its VPC.

   The **Virtual Private Cloud** page is displayed.

6. Locate the target VPC and click the number in the **Subnets** column.

   The **Subnets** page is displayed.

7. In the subnet list, view the CIDR blocks of the subnets.

8. In the subnet list, click the subnet name.

   The **Summary** page is displayed.

9. Click the **IP Addresses** tab and view the gateway addresses of the subnet.

.. |image1| image:: /_static/images/en-us_image_0000002171946714.png
.. |image2| image:: /_static/images/en-us_image_0000002792274624.png
