:original_name: overview_permission.html

.. _overview_permission:

Permissions
===========

If you need to assign different permissions to personnel in your enterprise to access your VPCs, IAM is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you to securely access your cloud resources.

With IAM, you can create IAM users, and assign permissions to control their access to specific resources. For example, if you want some software developers in your enterprise to use VPCs but do not want them to delete VPCs or perform any other high-risk operations, you can grant permissions to use VPCs but not permissions to delete them.

If your cloud account does not require IAM for permissions management, you can skip this section.

IAM is a free service. You only pay for the resources in your account. For more information, see `IAM Service Overview <https://docs.otc.t-systems.com/identity-access-management/umn/service_overview/what_is_iam.html#iam-01-0026>`__.

VPC Permissions
---------------

New IAM users do not have any permissions assigned by default. You need to first add them to one or more groups and attach policies or roles to these groups. The users then inherit permissions from the groups and can perform specified operations on cloud services based on the permissions they have been assigned.

VPC is a project-level service deployed for specific regions. When you set **Scope** to **Region-specific projects** and select the specified projects in the specified regions, the users only have permissions for VPCs in the selected projects. If you set **Scope** to **All resources**, users have permissions for VPCs in all region-specific projects. When accessing VPCs, the users need to switch to the authorized region.

You can grant permissions by using roles and policies.

-  Roles: A coarse-grained authorization strategy provided by IAM to assign permissions based on users' job responsibilities. Only a limited number of service-level roles are available for authorization. When you grant permissions using roles, you also need to attach dependent roles. Roles are not ideal for fine-grained authorization and least privilege access.
-  Policies: A fine-grained authorization strategy that defines permissions required to perform operations on specific cloud resources under certain conditions. This type of authorization is more flexible and is ideal for least privilege access. For example, you can grant VPC users only the permissions for managing a certain type of resources. A majority of fine-grained policies contain permissions for specific APIs, and permissions are defined using API actions. For the API actions supported by VPC, see `Permissions Policies and Supported Actions <https://docs.otc.t-systems.com/virtual-private-cloud/api-ref/permissions_policies_and_supported_actions/index.html>`__.

:ref:`Table 1 <overview_permission__table43611845113413>` lists all the system-defined permissions for VPC.

.. _overview_permission__table43611845113413:

.. table:: **Table 1** System-defined permissions for VPC

   +--------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Policy Name        | Description                                                                                                             | Policy Type           | Dependencies                                                                                                                 |
   +====================+=========================================================================================================================+=======================+==============================================================================================================================+
   | VPC FullAccess     | Full permissions for VPC                                                                                                | System-defined policy | To use the VPC flow log function, users must also have the **LTS ReadOnlyAccess** permission.                                |
   +--------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
   | VPC ReadOnlyAccess | Read-only permissions on VPC.                                                                                           | System-defined policy | None                                                                                                                         |
   +--------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
   | VPC Administrator  | Most permissions on VPC, excluding creating, modifying, deleting, and viewing security groups and security group rules. | System-defined role   | **Tenant Guest** and **Server Administrator** policies, which must be attached in the same project as **VPC Administrator**. |
   |                    |                                                                                                                         |                       |                                                                                                                              |
   |                    | To be granted this permission, users must also have the **Tenant Guest** and **Server Administrator** permission.       |                       |                                                                                                                              |
   +--------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+

:ref:`Table 2 <overview_permission__table73311721105916>` lists the common operations supported by system-defined permissions for VPC.

.. _overview_permission__table73311721105916:

.. table:: **Table 2** Common operations supported by system-defined permissions

   +--------------------------------------------+--------------------+-------------------+----------------+
   | Operation                                  | VPC ReadOnlyAccess | VPC Administrator | VPC FullAccess |
   +============================================+====================+===================+================+
   | Creating a VPC                             | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Modifying a VPC                            | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Deleting a VPC                             | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Viewing VPC information                    | Y                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Creating a subnet                          | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Viewing subnet information                 | Y                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Modifying a subnet                         | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Deleting a subnet                          | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Creating a security group                  | x                  | x                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Viewing security group information         | Y                  | x                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Modifying a security group                 | x                  | x                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Deleting a security group                  | x                  | x                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Adding a security group rule               | x                  | x                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Viewing a security group rule              | Y                  | x                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Modifying a security group rule            | x                  | x                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Deleting a security group rule             | x                  | x                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Creating a firewall                        | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Viewing a firewall                         | Y                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Modifying a firewall                       | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Deleting a firewall                        | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Adding a firewall rule                     | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Modifying a firewall rule                  | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Deleting a firewall rule                   | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Creating a VPC peering connection          | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Modifying a VPC peering connection         | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Deleting a VPC peering connection          | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Querying a VPC peering connection          | Y                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Accepting a VPC peering connection request | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Rejecting a VPC peering connection request | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Creating a route table                     | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Deleting a route table                     | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Modifying a route table                    | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Associating a route table with a subnet    | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Adding a route                             | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Modifying a route                          | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Deleting a route                           | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Creating a VPC flow log                    | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Viewing a VPC flow log                     | Y                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Enabling or disabling a VPC flow log       | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+
   | Deleting a VPC flow log                    | x                  | Y                 | Y              |
   +--------------------------------------------+--------------------+-------------------+----------------+

Helpful Links
-------------

-  `What Is IAM? <https://docs.otc.t-systems.com/identity-access-management/umn/service_overview/what_is_iam.html#iam-01-0026>`__
-  :ref:`Creating a User and Granting VPC Permissions <permission_0003>`
-  `Permissions Policies and Supported Actions <https://docs.otc.t-systems.com/virtual-private-cloud/api-ref/permissions_policies_and_supported_actions/index.html>`__
