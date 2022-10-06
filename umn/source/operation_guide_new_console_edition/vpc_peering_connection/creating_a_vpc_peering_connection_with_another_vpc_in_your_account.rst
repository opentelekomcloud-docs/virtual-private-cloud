:original_name: en-us_topic_0046655037.html

.. _en-us_topic_0046655037:

Creating a VPC Peering Connection with Another VPC in Your Account
==================================================================

Scenarios
---------

To create a VPC peering connection, first create a request to peer with another VPC. You can request a VPC peering connection with another VPC in your account, but the two VPCs must be in the same region. The system automatically accepts the request.

Prerequisites
-------------

Two VPCs in the same region have been created.

Creating a VPC Peering Connection
---------------------------------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. On the console homepage, under **Network**, click **Virtual Private Cloud**.

4. In the navigation pane on the left, click **VPC Peering**.

5. In the right pane displayed, click **Create VPC Peering Connection**.

6. Configure parameters as prompted. You must select **My account** for **Account**. :ref:`Table 1 <en-us_topic_0046655037__en-us_topic_0118498960_table1215761020244>` lists the parameters to be configured.


   .. figure:: /_static/images/en-us_image_0167839112.png
      :alt: **Figure 1** Create VPC Peering Connection


      **Figure 1** Create VPC Peering Connection

   .. _en-us_topic_0046655037__en-us_topic_0118498960_table1215761020244:

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                              | Example Value         |
      +=======================+==========================================================================================================================================================+=======================+
      | Name                  | The name of the VPC peering connection.                                                                                                                  | peering-001           |
      |                       |                                                                                                                                                          |                       |
      |                       | The name contains a maximum of 64 characters, which consist of letters, digits, hyphens (-), and underscores (_).                                        |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Local VPC             | The local VPC. You can select one from the drop-down list.                                                                                               | vpc_002               |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Local VPC CIDR Block  | The CIDR block for the local VPC.                                                                                                                        | 192.168.10.0/24       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Account               | The account to which the peer VPC belongs.                                                                                                               | My account            |
      |                       |                                                                                                                                                          |                       |
      |                       | -  **My account**: The VPC peering connection will be created between two VPCs, in the same region, in your account.                                     |                       |
      |                       | -  **Another account**: The VPC peering connection will be created between your VPC and a VPC in another account, in the same region.                    |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Peer Project          | The peer project name. The project name of the current project is used by default.                                                                       | aaa                   |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Peer VPC              | The peer VPC. You can select one from the drop-down list if the VPC peering connection is created between two VPCs in your own account.                  | vpc_fab1              |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Peer VPC CIDR Block   | The CIDR block for the peer VPC.                                                                                                                         | 192.168.2.0/24        |
      |                       |                                                                                                                                                          |                       |
      |                       | The local and peer VPCs cannot have matching or overlapping CIDR blocks. Otherwise, the routes added for the VPC peering connection may not take effect. |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7. Click **OK**.

Adding Routes for a VPC Peering Connection
------------------------------------------

If you request a VPC peering connection with another VPC in your own account, the system automatically accepts the request. To enable communication between the two VPCs, you need to add local and peer routes on the **Route Tables** page for the VPC peering connection.

#. On the console homepage, under **Network**, click **Virtual Private Cloud**.

#. In the navigation pane on the left, click **VPC Peering**.

#. Locate the VPC peering connection that you want to configure routes for in the connection list and click the connection name.

   The page showing the VPC peering connection details is displayed.

#. Add routes for the VPC peering connection to the route table of the local VPC:

   a. Click the **Local Routes** tab and then click the **Route Tables** hyperlink.

      The **Summary** tab of the default route table for the local VPC is displayed.

   b. Click the **Associated Subnets** tab to view the subnets associated with the default route table.

      -  If there is the subnet to be connected by the VPC peering connection,

         #. Click the **Summary** tab of the route table and click **Add Route** to add a route to the default route table.

            :ref:`Table 2 <en-us_topic_0046655037__en-us_topic_0118498960_table97163496270>` describes the route parameters.

      -  If the subnet to be connected by the VPC peering connection is not there,

         #. Return to the VPC list and switch to the subnet list of the VPC.

         #. Locate the row that contains the target subnet to be connected by the VPC peering connection, and click the route table name in the **Route Table** column.

            The **Summary** tab of the route table associated with the subnet is displayed.

         #. Click **Add Route** to add a route to the route table.

            :ref:`Table 2 <en-us_topic_0046655037__en-us_topic_0118498960_table97163496270>` describes the route parameters.

      .. _en-us_topic_0046655037__en-us_topic_0118498960_table97163496270:

      .. table:: **Table 2** Parameter description

         +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
         | Parameter             | Description                                                                                                                                                 | Example Value          |
         +=======================+=============================================================================================================================================================+========================+
         | Destination           | The peer VPC CIDR block, subnet CIDR block, or ECS IP address. For details, see :ref:`VPC Peering Connection Configuration Plans <en-us_topic_0046809840>`. | 192.168.0.0/16         |
         +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
         | Next Hop Type         | The next hop type. Select **VPC peering connection**.                                                                                                       | VPC peering connection |
         +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
         | Next Hop              | The next hop address. Select the name of the current VPC peering connection.                                                                                | peering-001            |
         +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
         | Description           | Supplementary information about the route. This parameter is optional.                                                                                      | -                      |
         |                       |                                                                                                                                                             |                        |
         |                       | The route description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                   |                        |
         +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+

5. Add routes for the VPC peering connection to the route table of the peer VPC:

   a. Click the **Peer Routes** tab and then click the **Route Tables** hyperlink.

      The **Summary** tab of the default route table for the peer VPC is displayed.

   b. Click the **Associated Subnets** tab to view the subnets associated with the default route table.

      -  If there is the subnet to be connected by the VPC peering connection,

         #. Click the **Summary** tab of the route table and click **Add Route** to add a route to the default route table.

            :ref:`Table 3 <en-us_topic_0046655037__en-us_topic_0118498960_table13697163914393>` describes the route parameters.

         #. Click **OK**.

      -  If the subnet to be connected by the VPC peering connection is not there,

         #. Return to the VPC list and switch to the subnet list of the VPC.

         #. Locate the row that contains the target subnet to be connected by the VPC peering connection, and click the route table name in the **Route Table** column.

            The **Summary** tab of the route table associated with the subnet is displayed.

         #. Click **Add Route** to add a route to the route table.

            :ref:`Table 3 <en-us_topic_0046655037__en-us_topic_0118498960_table13697163914393>` describes the route parameters.

         #. Click **OK**.

      .. _en-us_topic_0046655037__en-us_topic_0118498960_table13697163914393:

      .. table:: **Table 3** Parameter description

         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
         | Parameter             | Description                                                                                                                                                  | Example Value          |
         +=======================+==============================================================================================================================================================+========================+
         | Destination           | The local VPC CIDR block, subnet CIDR block, or ECS IP address. For details, see :ref:`VPC Peering Connection Configuration Plans <en-us_topic_0046809840>`. | 192.168.2.0/16         |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
         | Next Hop Type         | The next hop type. Select **VPC peering connection**.                                                                                                        | VPC peering connection |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
         | Next Hop              | The next hop address. Select the name of the current VPC peering connection.                                                                                 | peering-001            |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
         | Description           | Supplementary information about the route. This parameter is optional.                                                                                       | -                      |
         |                       |                                                                                                                                                              |                        |
         |                       | The route description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                    |                        |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+

After a VPC peering connection is created, the two VPCs can communicate with each other through private IP addresses. You can run the **ping** command to check whether the two VPCs can communicate with each other.

If two VPCs cannot communicate with each other, check the configuration by following the instructions provided in :ref:`Why Did Communication Fail Between VPCs That Were Connected by a VPC Peering Connection? <vpc_faq_0069>`

.. |image1| image:: /_static/images/en-us_image_0141273034.png
