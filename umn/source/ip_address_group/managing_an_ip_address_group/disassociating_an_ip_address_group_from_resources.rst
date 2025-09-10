:original_name: vpc_IPAddressGroup_0006.html

.. _vpc_IPAddressGroup_0006:

Disassociating an IP Address Group from Resources
=================================================

Scenarios
---------

This section describes how to disassociate an IP address group from a resource.

An IP address group can be associated with security groups.

Notes and Constraints
---------------------

Disassociating an IP address group from resources will make the rules of the resources invalid, and this action cannot be undone.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **IP Address Groups**.

   The IP address group list is displayed.

5. In the IP address group list, locate the row that contains the IP address group and click the resource hyperlink in the **Associated Resources** column.

   The **Associated Resources** page is displayed.

6. In the **Associated Resources** list, click the hyperlink of the corresponding resource name.

   The resource summary page is displayed. You can refer to :ref:`Table 1 <vpc_ipaddressgroup_0006__table106971359413>` to disassociate the IP address group from resources.

   .. _vpc_ipaddressgroup_0006__table106971359413:

   .. table:: **Table 1** Disassociating an IP address group from resources

      +-----------------------+----------------------------------------------------------------------------------+--------------------------------------------------------------------+
      | Resource              | Description                                                                      | Reference                                                          |
      +=======================+==================================================================================+====================================================================+
      | Security group        | Modify or delete inbound or outbound rules associated with the IP address group. | -  :ref:`Modifying a Security Group Rule <vpc_securitygroup_0005>` |
      |                       |                                                                                  |                                                                    |
      |                       |                                                                                  |    -  Inbound rule: Change the value of **Source**.                |
      |                       |                                                                                  |    -  Outbound rule: Change the value of **Destination**.          |
      |                       |                                                                                  |                                                                    |
      |                       |                                                                                  | -  :ref:`Deleting a Security Group Rule <vpc_securitygroup_0006>`  |
      +-----------------------+----------------------------------------------------------------------------------+--------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823746.png
