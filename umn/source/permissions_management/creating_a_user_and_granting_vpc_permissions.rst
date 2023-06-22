:original_name: permission_0003.html

.. _permission_0003:

Creating a User and Granting VPC Permissions
============================================

This section describes how to use IAM to implement fine-grained permissions control for your VPC resources. With IAM, you can:

-  Create IAM users for employees based on your enterprise's organizational structure. Each IAM user will have their own security credentials for accessing VPC resources.
-  Grant only the permissions required for users to perform a specific task.
-  Entrust a cloud account or cloud service to perform efficient O&M on your VPC resources.

If your cloud account does not require individual IAM users, skip this section.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <permission_0003__fig1447123814172>`).

Prerequisites
-------------

Learn about the permissions (:ref:`Permissions <overview_permission>`) supported by VPC and choose policies or roles according to your requirements.

For permissions of other services, see .

Process Flow
------------

.. _permission_0003__fig1447123814172:

.. figure:: /_static/images/en-us_image_0171311823.png
   :alt: **Figure 1** Process for granting VPC permissions

   **Figure 1** Process for granting VPC permissions

#. .. _permission_0003__li8447183891715:

   `Create a user group and assign permissions to it <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0030.html>`__.

   Create a user group on the IAM console, and assign the **VPC ReadOnlyAccess** policy to the group.

#. `Create an IAM user and add it to the user group <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0031.html>`__.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <permission_0003__li8447183891715>`.

#. `Log in <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0032.html>`__ and verify permissions.

   Log in to the VPC console by using the user created in 2, and verify that the user only has read permissions for VPC.

   -  Choose **Service List** > **Virtual Private Cloud**. Then click **Create VPC** on the VPC console. If a message appears indicating that you have insufficient permissions to perform the operation, the **VPC ReadOnlyAccess** policy has already taken effect.
   -  Choose any other service in **Service List**. If a message appears indicating that you have insufficient permissions to access the service, the **VPC ReadOnlyAccess** policy has already taken effect.
