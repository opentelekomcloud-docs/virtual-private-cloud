:original_name: permission_0003.html

.. _permission_0003:

Creating a User and Granting VPC Permissions
============================================

This section describes how to use IAM to implement fine-grained permissions control for your VPC resources. With IAM, you can:

-  Create IAM users for employees based on your enterprise's organizational structure. Each IAM user will have their own security credentials for accessing VPC resources.
-  Grant users only the permissions required to perform a given task based on their job responsibilities.
-  Entrust a cloud account or cloud service to perform efficient O&M on your VPC resources.

If your cloud account meets your permissions requirements, you can skip this section.

:ref:`Figure 1 <permission_0003__fig1447123814172>` shows the process flow for granting permissions.

Prerequisites
-------------

Learn about the permissions (see :ref:`Permissions <overview_permission>`) supported by VPC and choose policies or roles according to your requirements.

To grant permissions for other services, learn about all `permissions <https://docs.otc.t-systems.com/permissions/index.html>`__ supported by IAM.

Process Flow
------------

.. _permission_0003__fig1447123814172:

.. figure:: /_static/images/en-us_image_0171311823.png
   :alt: **Figure 1** Process for granting VPC permissions

   **Figure 1** Process for granting VPC permissions

#. On the IAM console, `create a user group and assign permissions to it <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0030.html>`__ (**VPC ReadOnlyAccess** as an example).

#. `Create an IAM user and add it to the created user group <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0031.html>`__.

#. `Log in as the IAM user <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0032.html>`__ and verify permissions.

   In the authorized region, perform the following operations:

   -  Choose **Service List** > **Virtual Private Cloud**. Then click **Create VPC** on the VPC console. If a message appears indicating that you have insufficient permissions to perform the operation, the **VPCReadOnlyAccess** policy is in effect.
   -  Choose another service from **Service List**. If a message appears indicating that you have insufficient permissions to access the service, the **VPCReadOnlyAccess** policy is in effect.
