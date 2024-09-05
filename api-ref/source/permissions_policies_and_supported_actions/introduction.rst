:original_name: permission_0001.html

.. _permission_0001:

Introduction
============

By default, new IAM users do not have permissions assigned. You need to add them to one or more groups and attach policies or roles to these groups. The users then inherit permissions from the groups. This way, they can perform specified operations on cloud services based on the permissions.

An account has all the permissions required to call all APIs, but IAM users must be assigned the required permissions. The permissions required for calling an API are determined by the actions supported by the API. Only users who have been granted permissions allowing the actions can call the API successfully. For example, if an IAM user wants to query VPCs using an API, the user must have been granted permissions that allow the **vpc:vpcs:list** action.

Supported Actions
-----------------

VPC provides system-defined policies that can be directly used in IAM. You can also create custom policies to supplement system-defined policies for more refined access control. Operations supported by policies are specific to APIs. The following are common concepts related to policies:

-  Permissions: statements in a policy that allow or deny certain operations
-  APIs: REST APIs that can be called by a user who has been granted specific permissions
-  Actions: specific operations that are allowed or denied
-  IAM project/Enterprise project: A custom policy can be applied to IAM projects or enterprise projects or both. Policies that contain actions supporting both IAM and enterprise projects can be assigned to user groups and take effect in both IAM and Enterprise Management. Policies that only contain actions supporting IAM projects can be assigned to user groups and only take effect for IAM. Such policies will not take effect if they are assigned to user groups in Enterprise Management.

   .. note::

      Y: supported; x: not supported
