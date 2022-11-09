:original_name: en-us_topic_0046655038.html

.. _en-us_topic_0046655038:

Creating a VPC Peering Connection with a VPC in Another Account
===============================================================

Scenarios
---------

The VPC service also allows you to create a VPC peering connection with a VPC in another account. The two VPCs must be in the same region. If you request a VPC peering connection with a VPC in another account in the same region, the owner of the peer account must accept the request to activate the connection.

Creating a VPC Peering Connection
---------------------------------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. On the console homepage, under **Network**, click **Virtual Private Cloud**.

4. In the navigation pane on the left, click **VPC Peering**.

5. In the right pane displayed, click **Create VPC Peering Connection**.

6. Configure parameters as prompted. You must select **Another account** for **Account**.


   .. figure:: /_static/images/en-us_image_0167840073.png
      :alt: **Figure 1** Create VPC Peering Connection

      **Figure 1** Create VPC Peering Connection

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Parameter             | Description                                                                                                                                                           | Example Value                        |
      +=======================+=======================================================================================================================================================================+======================================+
      | Name                  | The name of the VPC peering connection.                                                                                                                               | peering-001                          |
      |                       |                                                                                                                                                                       |                                      |
      |                       | The name contains a maximum of 64 characters, which consist of letters, digits, hyphens (-), and underscores (_).                                                     |                                      |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Local VPC             | The local VPC. You can select one from the drop-down list.                                                                                                            | vpc_002                              |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Account               | The account to which the VPC to peer with belongs.                                                                                                                    | Another account                      |
      |                       |                                                                                                                                                                       |                                      |
      |                       | -  **My account**: The VPC peering connection will be created between two VPCs, in the same region, in your account.                                                  |                                      |
      |                       | -  **Another account**: The VPC peering connection will be created between your VPC and a VPC in another account, in the same region.                                 |                                      |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Peer Project ID       | This parameter is available only when **Another account** is selected.                                                                                                | N/A                                  |
      |                       |                                                                                                                                                                       |                                      |
      |                       | For details about how to obtain the peer project ID, see :ref:`Obtaining the Peer Project ID <en-us_topic_0046655038__en-us_topic_0118498933_section41291933224121>`. |                                      |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Peer VPC ID           | This parameter is available only when **Another account** is selected.                                                                                                | 65d062b3-40fa-4204-8181-3538f527d2ab |
      |                       |                                                                                                                                                                       |                                      |
      |                       | For details about how to obtain the peer VPC ID, see :ref:`Obtaining the Peer VPC ID <en-us_topic_0046655038__en-us_topic_0118498933_section19734314164713>`.         |                                      |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+

7. Click **OK**.

Accepting a VPC Peering Connection Request
------------------------------------------

To request a VPC peering connection with a VPC in another account, the owner of the peer account must accept the request to activate the connection.

#. The owner of the peer account logs in to the management console.

#. On the console homepage, under **Network**, click **Virtual Private Cloud**.

#. In the navigation pane on the left, click **VPC Peering**.

#. In the VPC peering connection list, locate the row that contains the target VPC peering connection and click **Accept Request** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0162391155.png
      :alt: **Figure 2** VPC peering connection list

      **Figure 2** VPC peering connection list

#. Click **Yes** in the displayed dialog box.

Refusing a VPC Peering Connection
---------------------------------

The owner of the peer account can reject any VPC peering connection request that they receive. If a VPC peering connection request is rejected, the connection will not be established. You must delete the rejected VPC peering connection request before creating a VPC peering connection between the same VPCs as those in the rejected request.

#. The owner of the peer account logs in to the management console.
#. On the console homepage, under **Network**, click **Virtual Private Cloud**.
#. In the navigation pane on the left, click **VPC Peering**.
#. In the VPC peering connection list, locate the row that contains the target VPC peering connection and click **Reject Request** in the **Operation** column.
#. Click **Yes** in the displayed dialog box.

Adding Routes for a VPC Peering Connection
------------------------------------------

If you request a VPC peering connection with a VPC in another account, the owner of the peer account must accept the request. To enable communication between the two VPCs, the owners of both the local and peer accounts need to add routes on the **Route Tables** page for the VPC peering connection. The owner of the local account can add only the local route because the owner does not have the required permission to perform operations on the peer VPC. The owner of the peer account must add the peer route. The procedure for adding a local route and a peer route is the same.

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

            :ref:`Table 2 <en-us_topic_0046655038__en-us_topic_0118498933_table97163496270>` describes the route parameters.

      -  If the subnet to be connected by the VPC peering connection is not there,

         #. Return to the VPC list and switch to the subnet list of the VPC.

         #. Locate the row that contains the target subnet to be connected by the VPC peering connection, and click the route table name in the **Route Table** column.

            The **Summary** tab of the route table associated with the subnet is displayed.

         #. Click **Add Route** to add a route to the route table.

            :ref:`Table 2 <en-us_topic_0046655038__en-us_topic_0118498933_table97163496270>` describes the route parameters.

      .. _en-us_topic_0046655038__en-us_topic_0118498933_table97163496270:

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
         | Description           | Supplementary information about the route. This parameter is optional.                                                                                      | ``-``                  |
         |                       |                                                                                                                                                             |                        |
         |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                         |                        |
         +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+

#. Add routes for the VPC peering connection to the route table of the peer VPC:

   a. Click the **Peer Routes** tab and then click the **Route Tables** hyperlink.

      The **Summary** tab of the default route table for the peer VPC is displayed.

   b. Click the **Associated Subnets** tab to view the subnets associated with the default route table.

      -  If there is the subnet to be connected by the VPC peering connection,

         #. Click the **Summary** tab of the route table and click **Add Route** to add a route to the default route table.

            :ref:`Table 3 <en-us_topic_0046655038__en-us_topic_0118498933_table13697163914393>` describes the route parameters.

         #. Click **OK**.

      -  If the subnet to be connected by the VPC peering connection is not there,

         #. Return to the VPC list and switch to the subnet list of the VPC.

         #. Locate the row that contains the target subnet to be connected by the VPC peering connection, and click the route table name in the **Route Table** column.

            The **Summary** tab of the route table associated with the subnet is displayed.

         #. Click **Add Route** to add a route to the route table.

            :ref:`Table 3 <en-us_topic_0046655038__en-us_topic_0118498933_table13697163914393>` describes the route parameters.

         #. Click **OK**.

      .. _en-us_topic_0046655038__en-us_topic_0118498933_table13697163914393:

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
         | Description           | Supplementary information about the route. This parameter is optional.                                                                                       | ``-``                  |
         |                       |                                                                                                                                                              |                        |
         |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                          |                        |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+

After a VPC peering connection is created, the two VPCs can communicate with each other through private IP addresses. You can run the **ping** command to check whether the two VPCs can communicate with each other.

If two VPCs cannot communicate with each other, check the configuration by following the instructions provided in :ref:`Why Did Communication Fail Between VPCs That Were Connected by a VPC Peering Connection? <vpc_faq_0069>`

.. _en-us_topic_0046655038__en-us_topic_0118498933_section41291933224121:

Obtaining the Peer Project ID
-----------------------------

#. The owner of the peer account logs in to the management console.
#. Select **My Credentials** from the username drop-down list.
#. On the **Projects** tab, obtain the required project ID.

.. _en-us_topic_0046655038__en-us_topic_0118498933_section19734314164713:

Obtaining the Peer VPC ID
-------------------------

#. The owner of the peer account logs in to the management console.
#. On the console homepage, under **Network**, click **Virtual Private Cloud**.
#. In the navigation pane on the left, click **Virtual Private Cloud**.
#. Click the target VPC name and view VPC ID on the VPC details page.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
