:original_name: vpc_peering02_0003.html

.. _vpc_peering02_0003:

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

6. Configure parameters as prompted. You must select **My account** for **Account**. :ref:`Table 1 <vpc_peering02_0003__en-us_topic_0118498960_table1215761020244>` lists the parameters to be configured.


   .. figure:: /_static/images/en-us_image_0167839112.png
      :alt: **Figure 1** Create VPC Peering Connection

      **Figure 1** Create VPC Peering Connection

   .. _vpc_peering02_0003__en-us_topic_0118498960_table1215761020244:

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

Adding Routes for the VPC Peering Connection
--------------------------------------------

If you request a VPC peering connection with another VPC in your own account, the system automatically accepts the request. To enable communication between the two VPCs, you need to add local and peer routes for the VPC peering connection.

#. On the console homepage, under **Network**, click **Virtual Private Cloud**.

#. In the navigation pane on the left, click **VPC Peering**.

#. Locate the target VPC peering connection in the connection list.


   .. figure:: /_static/images/en-us_image_0226820452.png
      :alt: **Figure 2** VPC peering connection list

      **Figure 2** VPC peering connection list

#. Click the name of the VPC peering connection to switch to the page showing details about the connection.

#. In the displayed **Local Routes** area, click **Add Local Route**. In the displayed dialog box, add a local route. :ref:`Table 2 <vpc_peering02_0003__en-us_topic_0118498960_table1626072032518>` lists the parameters to be configured.


   .. figure:: /_static/images/en-us_image_0226820455.png
      :alt: **Figure 3** Add Local Route

      **Figure 3** Add Local Route

   .. _vpc_peering02_0003__en-us_topic_0118498960_table1626072032518:

   .. table:: **Table 2** Route parameter description

      +-------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Parameter   | Description                                                                                                 | Example Value                        |
      +=============+=============================================================================================================+======================================+
      | Destination | Specifies the destination address. Set it to the peer VPC or subnet CIDR block.                             | 192.168.2.0/24                       |
      +-------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Next Hop    | Specifies the next hop address. The default value is the VPC peering connection ID. Keep the default value. | d1a7863b-9d5e-4d27-8eaf-ab14d2a9148b |
      +-------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------+

#. Click **OK** to switch to the page showing the VPC peering connection details.

#. On the displayed page, click the **Peer Routes** tab.

#. In the displayed **Peer Routes** area, click **Add Peer Route** and add a route.

#. Click **OK**.

After a VPC peering connection is created, the two VPCs can communicate with each other through private IP addresses. You can run the **ping** command to check whether the two VPCs can communicate with each other.

If two VPCs cannot communicate with each other, check the configuration by following the instructions provided in :ref:`Why Did Communication Fail Between VPCs That Were Connected by a VPC Peering Connection? <vpc_faq_0069>`

.. |image1| image:: /_static/images/en-us_image_0141273034.png
