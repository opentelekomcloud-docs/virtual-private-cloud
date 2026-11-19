:original_name: acl_0002.html

.. _acl_0002:

Firewall Configuration Examples
===============================

You can use firewalls to control the traffic in and out of subnets. When both security groups and firewalls are configured, traffic matches firewall rules first and then security group rules. You can add security group rules as required and use firewalls as an additional layer of protection for your subnets. Here are some examples on how firewalls can be used.

-  :ref:`Denying External Access to Instances in a Subnet over a Specific Port <acl_0002__section11312173319432>`
-  :ref:`Denying Access from a Specific IP Address <acl_0002__section1431022694618>`
-  :ref:`Allowing External Access to Instances in a Subnet over Specific Ports <acl_0002__section61291659102216>`

Notes
-----

Note the following before configuring rules:

-  Each firewall has default rules, as shown in :ref:`Table 1 <acl_0002__table206881417172215>`. If a firewall has no custom rules, the default inbound and outbound rules are applied, denying all traffic from entering or leaving a subnet.

   .. _acl_0002__table206881417172215:

   .. table:: **Table 1** Default firewall rules

      +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+
      | Direction | Rule Number | Action | Protocol | Source    | Source Port Range | Destination | Destination Port Range |
      +===========+=============+========+==========+===========+===================+=============+========================+
      | Inbound   | \*          | Deny   | All      | 0.0.0.0/0 | All               | 0.0.0.0/0   | All                    |
      +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+
      | Outbound  | \*          | Deny   | All      | 0.0.0.0/0 | All               | 0.0.0.0/0   | All                    |
      +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+

-  You do not need to add rules to allow response traffic to requests. This is because firewalls are stateful and allow the responses to enter or leave the subnet without being controlled by rules.

For more information about how firewall rules work, see :ref:`How Firewall Rules Work <acl_0001__section1952742625114>`.

.. _acl_0002__section11312173319432:

Denying External Access to Instances in a Subnet over a Specific Port
---------------------------------------------------------------------

If you want to block TCP port 445 to protect instances against WannaCry ransomware attacks, you can associate a firewall with the subnet and add inbound rules described in :ref:`Table 2 <acl_0002__table553618145582>` to protect the instances in 10.0.0.0/24.

#. The default firewall rule denies any traffic to the subnet. You need to add custom rule 02 to allow inbound traffic.
#. Add custom rule 01 to deny all inbound traffic to instances in the subnet over TCP port 445. Insert the deny rule above the allow rule to let the deny rule be applied first. For details, see :ref:`Adding a Firewall Rule <en-us_topic_0051746702>`.

.. _acl_0002__table553618145582:

.. table:: **Table 2** Denying external access to instances in a subnet over a specific port

   +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+----------------+
   | Direction | Rule Number | Action | Protocol | Source    | Source Port Range | Destination | Destination Port Range | Description    |
   +===========+=============+========+==========+===========+===================+=============+========================+================+
   | Inbound   | 1           | Deny   | TCP      | 0.0.0.0/0 | All               | 10.0.0.0/24 | 445                    | Custom rule 01 |
   +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+----------------+
   | Inbound   | 2           | Allow  | All      | 0.0.0.0/0 | All               | 10.0.0.0/24 | All                    | Custom rule 02 |
   +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+----------------+
   | Inbound   | \*          | Deny   | All      | 0.0.0.0/0 | All               | 0.0.0.0/0   | All                    | Default rule   |
   +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+----------------+

.. _acl_0002__section1431022694618:

Denying Access from a Specific IP Address
-----------------------------------------

You can associate a firewall with a subnet and add inbound rules as described in :ref:`Table 3 <acl_0002__table2084994619493>` to deny the access from abnormal IP addresses, for example, 10.1.1.12/32, to protect the instances in 10.5.0.0/24.

#. The default firewall rule denies any traffic to the subnet. You need to add custom rule 02 to allow inbound traffic.
#. Add custom rule 01 to deny traffic from 10.1.1.12/32 to the subnet. Insert the deny rule above the allow rule to let the deny rule be applied first. For details, see :ref:`Adding a Firewall Rule <en-us_topic_0051746702>`.

.. _acl_0002__table2084994619493:

.. table:: **Table 3** Denying access from a specific IP address

   +-----------+-------------+--------+----------+--------------+-------------------+-------------+------------------------+----------------+
   | Direction | Rule Number | Action | Protocol | Source       | Source Port Range | Destination | Destination Port Range | Description    |
   +===========+=============+========+==========+==============+===================+=============+========================+================+
   | Inbound   | 1           | Deny   | TCP      | 10.1.1.12/32 | All               | 10.5.0.0/24 | All                    | Custom rule 01 |
   +-----------+-------------+--------+----------+--------------+-------------------+-------------+------------------------+----------------+
   | Inbound   | 2           | Allow  | All      | 0.0.0.0/0    | All               | 10.5.0.0/24 | All                    | Custom rule 02 |
   +-----------+-------------+--------+----------+--------------+-------------------+-------------+------------------------+----------------+
   | Inbound   | \*          | Deny   | All      | 0.0.0.0/0    | All               | 0.0.0.0/0   | All                    | Default rule   |
   +-----------+-------------+--------+----------+--------------+-------------------+-------------+------------------------+----------------+

.. _acl_0002__section61291659102216:

Allowing External Access to Instances in a Subnet over Specific Ports
---------------------------------------------------------------------

If you deploy web servers in a subnet and want these servers to be accessible from external networks, you need to add firewall and security group rules to allow traffic over port 80 (HTTP) and port 443 (HTTPS).

#. Add firewall rules listed in :ref:`Table 4 <acl_0002__table389311581341>`.

   -  Add custom rule A01 to allow any IP addresses to access the instances in the subnet over port 80 (HTTP).
   -  Add custom rule A02 to allow any IP addresses to access the instances in the subnet over port 443 (HTTPS).

   **10.8.0.0/24 is the CIDR block of the subnet to be protected. If the destination of a rule is set to this CIDR block, all instances in the subnet can be protected.**

   .. _acl_0002__table389311581341:

   .. table:: **Table 4** Firewall rules for allowing access to instances in a subnet over specific ports

      +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+----------------+
      | Direction | Rule Number | Action | Protocol | Source    | Source Port Range | Destination | Destination Port Range | Description    |
      +===========+=============+========+==========+===========+===================+=============+========================+================+
      | Inbound   | 1           | Allow  | TCP      | 0.0.0.0/0 | All               | 10.8.0.0/24 | 80                     | Custom rule 01 |
      +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+----------------+
      | Inbound   | 2           | Allow  | TCP      | 0.0.0.0/0 | All               | 10.8.0.0/24 | 443                    | Custom rule 02 |
      +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+----------------+
      | Inbound   | \*          | Deny   | All      | 0.0.0.0/0 | All               | 0.0.0.0/0   | All                    | Default rule   |
      +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+----------------+
      | Outbound  | \*          | Deny   | All      | 0.0.0.0/0 | All               | 0.0.0.0/0   | All                    | Default rule   |
      +-----------+-------------+--------+----------+-----------+-------------------+-------------+------------------------+----------------+

#. Add the rules listed in :ref:`Table 5 <acl_0002__table347342171117>` to all the security groups associated with the instances.

   -  Add inbound rule 01 to allow any IP addresses to access the instances over port 80 (HTTP).

   -  Add inbound rule 02 to allow any IP addresses to access the instances over port 443 (HTTPS).

   -  Add outbound rule 03 to allow any traffic to leave the security group.

      A firewall adds an additional layer of security. Even if the security group rules allow more traffic than that actually required, the firewall rules allow only access over HTTP port 80 and HTTPS port 443 and deny other inbound traffic.

   .. _acl_0002__table347342171117:

   .. table:: **Table 5** Security group rules for allowing access to instances in a subnet over specific ports

      +-----------+-------------+------+-----------------+-----------------------+-------------+
      | Direction | Rule Number | Type | Protocol & Port | Source or Destination | Description |
      +===========+=============+======+=================+=======================+=============+
      | Inbound   | 1           | IPv4 | TCP: 80         | IP address: 0.0.0.0/0 | Rule 01     |
      +-----------+-------------+------+-----------------+-----------------------+-------------+
      | Inbound   | 1           | IPv4 | TCP: 443        | IP address: 0.0.0.0/0 | Rule 02     |
      +-----------+-------------+------+-----------------+-----------------------+-------------+
      | Outbound  | 1           | IPv4 | All             | IP address: 0.0.0.0/0 | Rule 03     |
      +-----------+-------------+------+-----------------+-----------------------+-------------+
