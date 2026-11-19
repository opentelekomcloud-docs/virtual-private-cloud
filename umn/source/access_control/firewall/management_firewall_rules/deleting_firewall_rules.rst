:original_name: vpc_acl_0007.html

.. _vpc_acl_0007:

Deleting Firewall Rules
=======================

Scenarios
---------

If you no longer need a firewall rule to control the inbound and outbound traffic of a subnet, you can delete the firewall rule.

Deleting rules may affect how and where traffic is directed. Proceed with caution.

To perform operations on a single firewall rule, see :ref:`Deleting a Firewall Rule <vpc_acl_0007__section25103352161542>`.

To perform operations on multiple firewall rules at a time:

-  If there are only a few rules to be deleted, you can select these rules in the firewall rule list on the console by referring to :ref:`Deleting Firewall Rules in Batches <vpc_acl_0007__section1634181814430>`.
-  If there are a large number of rules to be deleted, you can :ref:`export the rule list to a local Excel file <vpc_acl_0008>`, keep only the rules you want to delete, and import the file to the console. The system then selects the rules to be processed based on the imported file, improving processing efficiency. For details, see :ref:`Deleting Firewall Rules in Batches (Using an Excel File) <vpc_acl_0007__section1103205593210>`.

Notes and Constraints
---------------------

Default firewall rules cannot be modified or deleted.

A maximum of 50 firewall rules can be deleted at a time.

.. _vpc_acl_0007__section25103352161542:

Deleting a Firewall Rule
------------------------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The VPC list is displayed.

4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

5. Locate the target firewall and click its name to switch to the page showing details of that particular firewall.

6. On the **Inbound Rules** or **Outbound Rules** tab, locate the row that contains the target rule and click **Delete** in the **Operation** column.

7. Click **OK**.

.. _vpc_acl_0007__section1634181814430:

Deleting Firewall Rules in Batches
----------------------------------

#. Log in to the management console.

2. Click |image3| in the upper left corner and select the region and project.

3. In the upper left corner of the page, click |image4| to expand the service list and choose **Network** > **Virtual Private Cloud**.

   The VPC list is displayed.

4. In the navigation pane on the left, choose **Access Control** > **Firewalls**.

   The firewall list is displayed.

5. In the firewall list, locate the target firewall and click its name.

   The firewall summary page is displayed.

6. Click the **Inbound Rules** or **Outbound Rules** tab as required.

   The rule list is displayed.

7. In the firewall rule list, select multiple rules and click **Delete** in the upper left corner above the list.

   A confirmation dialog box is displayed.

8. Confirm the information and click **OK**.

.. _vpc_acl_0007__section1103205593210:

Deleting Firewall Rules in Batches (Using an Excel File)
--------------------------------------------------------

#. Log in to the management console.

2.  Click |image5| in the upper left corner and select the region and project.

3.  In the upper left corner of the page, click |image6| to expand the service list and choose **Network** > **Virtual Private Cloud**.

    The VPC list is displayed.

4.  In the navigation pane on the left, choose **Access Control** > **Firewalls**.

    The firewall list is displayed.

5.  In the firewall list, locate the target firewall and click its name.

    The firewall summary page is displayed.

6.  Click the **Inbound Rules** or **Outbound Rules** tab as required.

    The rule list is displayed.

7.  In the upper left corner above the rule list, click **Batch Select**.

    The **Batch Select** dialog box is displayed.

8.  Select either of the following methods:

    -  Method 1: Click **Download Template** to download the Excel file to your local PC and fill in the rules to be enabled or disabled in the file.
    -  Method 2: :ref:`Export the existing rules to a local Excel file <vpc_acl_0008>`, filter the target rules and keep them as they are, and save the file.

    After the Excel file is ready, take step :ref:`9 <vpc_acl_0007__li143617481478>`. The system then automatically selects the target rules based on the imported file.

9.  .. _vpc_acl_0007__li143617481478:

    In the **Batch Select** dialog box, click **Add**.

    The system starts to process and match the rules in the Excel file with the existing rules. The matching items of a rule include the type, action, protocol, source address, source port range, destination address, and destination port range.

    -  If a rule in the Excel file matches an existing rule, **Verified** is displayed in the **Result** column. Only the matched rules can be enabled or disabled.
    -  If a rule fails to be matched, the causes will be displayed in the **Result** column. The possible causes are as follows:

       -  There is no such rule in this firewall.
       -  Inconsistent rule direction. For example, you perform the operation on outbound rules on the **Inbound Rules** tab, or the other way around.
       -  Duplicate rules in the Excel file. The system automatically filters out the duplicate rules.

10. Confirm the rules and click **OK**.

    The rule list page is displayed and the target rules are selected automatically.

11. Click **Delete** above the rule list.

    A confirmation dialog box is displayed.

12. Confirm the information and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823162.png
.. |image3| image:: /_static/images/en-us_image_0141273034.png
.. |image4| image:: /_static/images/en-us_image_0000002778654525.png
.. |image5| image:: /_static/images/en-us_image_0141273034.png
.. |image6| image:: /_static/images/en-us_image_0000002778774389.png
