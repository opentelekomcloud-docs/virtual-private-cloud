:original_name: bestpractice_0013.html

.. _bestpractice_0013:

Using IP Address Groups to Reduce the Number of Security Group Rules
====================================================================

Scenarios
---------

Finance and securities enterprises have high security requirements when planning cloud networks. Access to servers is often controlled based on IP addresses. To simplify security group rule configuration and provide refined security control, you can use IP address groups in case of the following scenarios:

-  A security group has more than 40 rules.
-  The direction, type, protocol, and port of security group rules are the same except the address.

Constraints
-----------

-  An IP address group can contain a maximum of 20 IP addresses or IP address ranges.

Prerequisites
-------------

You have created one or more security groups for access control.

Typical Case
------------

For example, you plan to configure the following rules for security group A.

========= ==== ======== ========== =========================
Direction Type Protocol Port Range Source/Destination
========= ==== ======== ========== =========================
Inbound   IPv4 TCP      22122      Source: 11.19.255.64/30
Inbound   IPv4 TCP      22122      Source: 113.31.128.252/30
Inbound   IPv4 TCP      22122      Source: 113.31.138.0/25
Inbound   IPv4 TCP      22122      Source: 183.232.25.208/28
========= ==== ======== ========== =========================

The four inbound rules have the same port, type, and protocol but different source IP addresses. In this case, you can use an IP address group to reconfigure the security group rules.

Procedure
---------

**Create an IP address group.**

#. Log in to the management console.
#. Click |image1| in the upper left corner and Under **Network**, click **Elastic Load Balancing**.
#. In the navigation pane on the left, choose **IP Address Groups**.
#. Click **Create IP Address Group**.
#. Set the parameters.

   -  **Name**: **ipGroup-A**

   -  **IP Address**:

      11.19.255.64/30
      113.31.128.252/30
      113.31.138.0/25
      183.232.25.208/28


      .. figure:: /_static/images/en-us_image_0000001124559441.png
         :alt: **Figure 1** Creating an IP address group

         **Figure 1** Creating an IP address group

#. Click **OK**.

**Configure a security group rule.**

8.  Click |image1| in the upper left corner and Under **Network**, click **Virtual Private Cloud**.
9.  In the navigation pane on the left, choose **Access Control** > **Security Groups**.
10.  Locate security group A and click **Manage Rule** in the **Operation** column.
11. Under **Inbound Rules**, click **Add Rule**.
12. Set the parameters.

    -  **Protocol & Port**: **TCP** and **22122**

    -  **Type**: **IPv4**

    -  **Source**: **ipGroup-A**


       .. figure:: /_static/images/en-us_image_0000001124559429.png
          :alt: **Figure 2** Configuring a security group rule

          **Figure 2** Configuring a security group rule

13. Click **OK**.

**Delete old security group rules.**

14. Delete four old security group rules after the configured security group rule takes effect.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
