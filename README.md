LACP EtherChannel and VLAN Trunking Lab

Overview

This project demonstrates the configuration and verification of an LACP EtherChannel between two Cisco switches. Two physical links were bundled into a single logical Port-Channel to provide link redundancy and increased available bandwidth.

Objectives

Configure an EtherChannel using LACP.

Bundle two physical switch links into Port-Channel 1.

Configure the connection to carry VLAN traffic using 802.1Q trunking.

Verify EtherChannel and trunk operation using Cisco IOS commands.

Network Topology

2 Cisco 2960 switches

2 physical links between the switches using Fa0/3 and Fa0/5

Port-Channel 1 configured using LACP

VLAN 10 and VLAN 20 carried across the trunk

A separate router connection using Fa0/4

Configuration

The two switch-to-switch links were configured as members of the same EtherChannel group using LACP active mode:

interface range fa0/3, fa0/5
 switchport mode trunk
 channel-group 1 mode active

Both physical interfaces were successfully bundled into Port-Channel 1.

Verification

EtherChannel status was verified using:

show etherchannel summary

The verification confirmed:

Po1(SU)  LACP  Fa0/3(P) Fa0/5(P)

This confirms that Port-Channel 1 is a Layer 2 EtherChannel in use and that both physical interfaces were successfully bundled.

Trunk operation was verified using:

show interfaces trunk

The output confirmed that Port-Channel 1 was trunking using 802.1Q and that VLANs 10 and 20 were active across the trunk.

Troubleshooting

During configuration, Fa0/5 initially failed to join the EtherChannel because its configuration was incompatible with Port-Channel 1. After configuring Fa0/5 with matching trunk settings, both physical links successfully joined the EtherChannel.

Technologies Used

Cisco Packet Tracer

Cisco IOS

EtherChannel

LACP

VLANs

802.1Q Trunking

Spanning Tree Protocol
