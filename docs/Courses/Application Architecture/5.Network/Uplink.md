In VMware, **uplink ports** are physical adapter ports that connect a virtual network to a physical network. These ports are linked to physical adapters when device drivers initialize them or when virtual switch teaming policies are reconfigured.
![[Uplink.png]]

An **uplink port group** or **dvuplink port group** is created as part of a distributed switch. It serves as a template for configuring the physical connections of hosts, along with failover and load-balancing policies. Each uplink port group can contain one or more uplinks, and you map the physical NICs (network interface cards) of hosts to these uplinks on the distributed switch. At the host level, each physical NIC is assigned to an uplink port with a specific ID.

Failover and load-balancing policies are applied to these uplinks, and the configurations automatically propagate to the host proxy switches (data plane). This ensures consistent failover and load-balancing settings across all physical NICs on the hosts connected to the distributed switch.

