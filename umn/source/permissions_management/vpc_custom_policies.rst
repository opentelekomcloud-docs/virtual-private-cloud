:original_name: permission_0004.html

.. _permission_0004:

VPC Custom Policies
===================

Custom policies can be created to supplement the system-defined policies of VPC. For the actions supported for custom policies, see `Permissions Policies and Supported Actions <https://docs.otc.t-systems.com/virtual-private-cloud/api-ref/permissions_policies_and_supported_actions/index.html>`__.

You can create custom policies in either of the following ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.
-  JSON: Edit JSON policies from scratch or based on an existing policy.

For operation details, see `Creating a Custom Policy <https://docs.otc.t-systems.com/usermanual/iam/en-us_topic_0274187246.html>`__. The following section contains examples of common VPC custom policies.

Example Custom Policies
-----------------------

-  Example 1: Allowing users to create and view VPCs

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "
                           vpc:vpcs:create
                           vpc:svpcs:list
                       "
                  ]
              }
          ]
      }

-  Example 2: Denying VPC deletion

   A deny policy must be used in conjunction with other policies to take effect. If the permissions assigned to a user contain both Allow and Deny actions, the Deny actions take precedence over the Allow actions.

   The following method can be used if you need to assign permissions of the **VPC FullAccess** policy to a user but also forbid the user from deleting VPCs. Create a custom policy for denying VPC deletion, and assign both policies to the group the user belongs to. Then the user can perform all operations on VPC except deleting VPCs. The following is an example deny policy:

   .. code-block::

      {
            "Version": "1.1",
            "Statement": [
                  {
                "Effect": "Deny",
                        "Action": [
                              "vpc:vpcs:delete"
                        ]
                  }
            ]
      }

-  Example 3: Defining permissions for multiple services in a policy

   A custom policy can contain the actions of multiple services that are of the global or project-level type. The following is an example policy containing actions of multiple services:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Action": [
                      "vpc:vpcs:create",
                      "vpc:vpcs:update"
                  ],
                  "Effect": "Allow"
              },
              {
                  "Action": [
                      "ecs:servers:delete"
                  ],
                  "Effect": "Allow"
              }
          ]
      }
