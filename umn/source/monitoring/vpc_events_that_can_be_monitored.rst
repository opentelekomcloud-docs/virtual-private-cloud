:original_name: vpc010018.html

.. _vpc010018:

VPC Events That Can Be Monitored
================================

Description
-----------

On Cloud Eye, you can use event monitoring for data collection, query, and alarm reporting. You can create alarm rules for both system events and custom events. When specific events occur, Cloud Eye generates alarms for you.

Namespace
---------

SYS.VPC


VPC Events That Can Be Monitored
--------------------------------

.. table:: **Table 1** VPC events

   +-----------------------+-----------+--------------------+-----------------+----------------+
   | Event Source          | Namespace | Event Name         | Event ID        | Event Severity |
   +=======================+===========+====================+=================+================+
   | Virtual Private Cloud | SYS.VPC   | VPC deleted        | deleteVpc       | Major          |
   +-----------------------+-----------+--------------------+-----------------+----------------+
   |                       |           | VPC modified       | modifyVpc       | Minor          |
   +-----------------------+-----------+--------------------+-----------------+----------------+
   |                       |           | Subnet deleted     | deleteSubnet    | Minor          |
   +-----------------------+-----------+--------------------+-----------------+----------------+
   |                       |           | Subnet modified    | modifySubnet    | Minor          |
   +-----------------------+-----------+--------------------+-----------------+----------------+
   |                       |           | Bandwidth modified | modifyBandwidth | Minor          |
   +-----------------------+-----------+--------------------+-----------------+----------------+
   |                       |           | VPN deleted        | deleteVpn       | Major          |
   +-----------------------+-----------+--------------------+-----------------+----------------+
   |                       |           | VPN modified       | modifyVpn       | Minor          |
   +-----------------------+-----------+--------------------+-----------------+----------------+
