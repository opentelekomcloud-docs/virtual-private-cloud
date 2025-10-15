:original_name: vpc_qs_0022.html

.. _vpc_qs_0022:

Overview
========

If your ECSs need to access the Internet (for example, the ECSs functioning as the service nodes for deploying a website), you can follow the procedure shown in :ref:`Figure 1 <vpc_qs_0022__fe457c1ec47c84d6fa3b87210d5b284eb>` to bind EIPs to the ECSs.

.. _vpc_qs_0022__fe457c1ec47c84d6fa3b87210d5b284eb:

.. figure:: /_static/images/en-us_image_0000001818823006.png
   :alt: **Figure 1** Configuring the network

   **Figure 1** Configuring the network

:ref:`Table 1 <vpc_qs_0022__t5143cea7d59f4c31b1c56ab35e86f71f>` describes the different tasks in the procedure for configuring the network.

.. _vpc_qs_0022__t5143cea7d59f4c31b1c56ab35e86f71f:

.. table:: **Table 1** Configuration process description

   +--------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Task                                 | Description                                                                                                                                                                                                                                                                                 |
   +======================================+=============================================================================================================================================================================================================================================================================================+
   | Create a VPC.                        | This task is mandatory.                                                                                                                                                                                                                                                                     |
   |                                      |                                                                                                                                                                                                                                                                                             |
   |                                      | A created VPC comes with a default subnet you specified.                                                                                                                                                                                                                                    |
   |                                      |                                                                                                                                                                                                                                                                                             |
   |                                      | After the VPC is created, you can create other required network resources in the VPC based on your service requirements.                                                                                                                                                                    |
   +--------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Create another subnet for the VPC.   | This task is optional.                                                                                                                                                                                                                                                                      |
   |                                      |                                                                                                                                                                                                                                                                                             |
   |                                      | If the default subnet cannot meet your requirements, you can create one.                                                                                                                                                                                                                    |
   |                                      |                                                                                                                                                                                                                                                                                             |
   |                                      | The new subnet is used to assign IP addresses to network interfaces attached to the ECS.                                                                                                                                                                                                    |
   +--------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Assign an EIP and bind it to an ECS. | This task is mandatory.                                                                                                                                                                                                                                                                     |
   |                                      |                                                                                                                                                                                                                                                                                             |
   |                                      | You can assign an EIP and bind it to an ECS for Internet access.                                                                                                                                                                                                                            |
   +--------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Create a security group.             | This task is mandatory.                                                                                                                                                                                                                                                                     |
   |                                      |                                                                                                                                                                                                                                                                                             |
   |                                      | You can create a security group and add ECSs in the VPC to the security group to improve ECS access security. After a security group is created, it has default rules, which allow all outgoing data packets. ECSs in a security group can access each other without the need to add rules. |
   +--------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Add a security group rule.           | This task is optional.                                                                                                                                                                                                                                                                      |
   |                                      |                                                                                                                                                                                                                                                                                             |
   |                                      | If the default rule does not meet your service requirements, you can add security group rules.                                                                                                                                                                                              |
   +--------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
