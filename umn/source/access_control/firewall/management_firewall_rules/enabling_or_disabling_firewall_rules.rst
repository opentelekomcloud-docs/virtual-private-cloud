:original_name: vpc_acl_0006.html

.. _vpc_acl_0006:

Enabling or Disabling Firewall Rules
====================================

Scenarios
---------

After a firewall rule is added, it is in the **Enabled** status. You can enable or disable custom firewall rules as required.

-  Disabled custom firewall rules become invalid. If all custom rules are disabled, only the default rules apply, and all traffic to and from the associated subnets is denied. This may interrupt network traffic of associated subnets. Proceed with caution.
-  Enabled custom firewall rules are applied. Enabling custom rules may affect how and where traffic is directed. Proceed with caution.

To perform operations on a single firewall rule, see :ref:`Enabling or Disabling a Single Firewall Rule <vpc_acl_0006__section25103352161542>`.

To perform operations on multiple firewall rules at a time:

-  If there are only a few rules, you can select the rules to process from the firewall rule list on the console by referring to :ref:`Enabling or Disabling a Single Firewall Rule <vpc_acl_0006__section25103352161542>`.
-  If there are many rules, you can :ref:`export the rule list to a local Excel file <vpc_acl_0008>`, keep only the rules you want to enable or disable, and import the file to the console. The system identifies the rules to process based on the imported file, improving processing efficiency. For details, see :ref:`Enabling or Disabling Multiple Firewall Rules in Batches Using an Excel File <vpc_acl_0006__section1103205593210>`.

.. _vpc_acl_0006__section25103352161542:

Enabling or Disabling a Single Firewall Rule
--------------------------------------------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

5. Locate the target firewall and click its name to switch to the page showing details of that particular firewall.

6. On the **Inbound Rules** or **Outbound Rules** tab, locate the row that contains the target rule, and click **More** and then **Enable** or **Disable** in the **Operation** column.

7. Click **OK** in the displayed dialog box.

   The rule is enabled or disabled. The procedure for enabling or disabling an outbound rule is the same as that for enabling or disabling an inbound rule.

Enabling or Disabling Multiple Firewall Rules in Batches on the Console
-----------------------------------------------------------------------

#. Log in to the management console.

2. Click |image3| in the upper left corner and select the desired region and project.

3. Click |image4| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list page is displayed.

4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

5. Locate the target firewall and click its name to switch to the page showing details of that particular firewall.

6. Click the **Inbound Rules** or **Outbound Rules** tab as required.

   The firewall rule list is displayed.

7. In the firewall rule list, select multiple rules.

8. In the rule list, perform the following operations:

   -  Enabling a firewall rule:

      a. In the upper left corner above the firewall rule list, choose **More** > **Enable**.

         A confirmation dialog box is displayed.

      b. Confirm the information and click **OK**.

   -  Disabling a firewall rule:

      a. In the upper left corner above the firewall rule list, choose **More** > **Disable**.

         A confirmation dialog box is displayed.

      b. Confirm the information and click **OK**.

.. _vpc_acl_0006__section1103205593210:

Enabling or Disabling Multiple Firewall Rules in Batches Using an Excel File
----------------------------------------------------------------------------

#. Log in to the management console.

2.  Click |image5| in the upper left corner and select the desired region and project.

3.  Click |image6| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

    The VPC list page is displayed.

4.  In the navigation pane on the left, choose **Access Control** > **Firewalls**.

5.  Locate the target firewall and click its name to switch to the page showing details of that particular firewall.

6.  Click the **Inbound Rules** or **Outbound Rules** tab as required.

    The firewall rule list is displayed.

7.  In the upper left corner above the firewall rule list, click **Batch Select**.

    The **Batch Select** dialog box is displayed.

8.  Select either of the following methods:

    -  Method 1: Click **Download Template** to download the Excel file to your local PC and fill in the rules to be enabled or disabled in the file.
    -  Method 2: :ref:`Export the existing rules to a local Excel file <vpc_acl_0008>`, filter the target rules and keep them as they are, and save the file.

    After the Excel file is ready, go to the next step to import the Excel file. The system then automatically selects the target rules based on the imported file.

9.  In the **Batch Select** dialog box, click **Add**.

    The system starts to process and match the rules in the Excel file with the existing rules. The matching items of a rule include the type, action, protocol, source address, source port range, destination address, and destination port range.

    -  If a rule in the Excel file matches an existing rule, **Verified** is displayed in the **Result** column. Only the matched rules can be enabled or disabled.
    -  If a rule fails to be matched, the causes will be displayed in the **Result** column. The possible causes are as follows:

       -  There is no such rule in this firewall.
       -  Inconsistent rule direction. For example, you perform the operation on outbound rules on the **Inbound Rules** tab, or the other way around.
       -  Duplicate rules in the Excel file. The system automatically filters out the duplicate rules.

10. Confirm the rules and click **OK**.

    The rule list page is displayed and the target rules are selected automatically.

11. In the rule list, perform the following operations:

    -  Enabling a firewall rule:

       a. In the upper left corner above the firewall rule list, choose **More** > **Enable**.

          A confirmation dialog box is displayed.

       b. Confirm the information and click **OK**.

    -  Disabling a firewall rule:

       a. In the upper left corner above the firewall rule list, choose **More** > **Disable**.

          A confirmation dialog box is displayed.

       b. Confirm the information and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823738.png
.. |image3| image:: /_static/images/en-us_image_0000002633200908.png
.. |image4| image:: /_static/images/en-us_image_0000002633360806.png
.. |image5| image:: /_static/images/en-us_image_0000002663639985.png
.. |image6| image:: /_static/images/en-us_image_0000002663600039.png
