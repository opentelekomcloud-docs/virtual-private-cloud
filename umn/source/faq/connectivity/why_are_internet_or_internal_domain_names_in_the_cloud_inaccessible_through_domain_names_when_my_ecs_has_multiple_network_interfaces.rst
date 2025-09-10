:original_name: vpc_faq_0060.html

.. _vpc_faq_0060:

Why Are Internet or Internal Domain Names in the Cloud Inaccessible Through Domain Names When My ECS Has Multiple Network Interfaces?
=====================================================================================================================================

When an ECS has more than one network interface, if different DNS server addresses are configured for the subnets used by the network interfaces, the ECS cannot access public websites or internal domain names in the cloud.

You can resolve this issue by configuring the same DNS server address for the subnets used by the same ECS. You can perform the following steps to modify DNS server addresses of subnets in a VPC:

#. Log in to the management console.

2. On the console homepage, under **Network**, click **Virtual Private Cloud**.
3. In the navigation pane on the left, choose **Virtual Private Cloud** > **Subnets**.
4. In the subnet list, locate the target subnet and click its name.
5. On the subnet details page, change the DNS server address of the subnet.
6. Click **OK**.
