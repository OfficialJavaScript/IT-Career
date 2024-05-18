# Learning EP 1

All learning from https://www.youtube.com/watch?v=9eH16Fxeb9o

First command I learned for when you have your switch first running is to use 'enable' a little # will appear, for example:

```
%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/2, changed state to up

%LINK-5-CHANGED: Interface FastEthernet0/3, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/3, changed state to up

%LINK-5-CHANGED: Interface FastEthernet0/4, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/4, changed state to up


Switch>enable
Switch#
```

Next I learned how to show the mac address table, this is a table of what the mac address of a device is, and what port it's on. It also shows the 'Vlan' and 'Type' - which I will learn about later.
It looks like this:

```
Switch#show mac-address-table
          Mac Address Table
-------------------------------------------

Vlan    Mac Address       Type        Ports
----    -----------       --------    -----

   1    0001.4298.a262    DYNAMIC     Fa0/4
   1    0009.7ce3.3271    DYNAMIC     Fa0/3
   1    00d0.9752.8936    DYNAMIC     Fa0/2
   1    00e0.b059.0a97    DYNAMIC     Fa0/1
```

## Questions
### Which of the following addresses will a switch use to populate a CAM table? (Select the best answer.)

A. destination IP addresses

B. source IP addresses

C. destination MAC addresses

D. source MAC addresses

The answer is D. source MAC addresses

Explanation:

A switch will use source Media Access Control (MAC) addresses to populate the Content Addressable Memory (CAM) table. The CAM table, which is also called the switching table, is used by a switch to discover the relationship between the Open Systems Interconnection (OSI) Layer 2 address of a device and the physical port used to reach the device. The switch populates the CAM table by recording the source MAC address of an inbound Layer 2 frame and the corresponding switch port that the frame arrived on.

Switches make forwarding decisions based on the destination MAC address contained in a frame's header. The switch first searches the CAM table for an entry that matches the frame's destination MAC address. If the frame's destination MAC address is not found in the table, the switch forwards the frame to all its ports, except the port from which it received the frame. If the destination MAC address is found in the table, the switch forwards the frame to the appropriate port. The source MAC address is also recorded if it did not previously exist in the CAM table.

A switch will not use destination MAC addresses to populate the CAM table. However, if a switch already has entries in the CAM table for a frame's source and destination MAC addresses, the switch can forward frames between them.

A switch will not use source or destination Internet Protocol (IP) addresses to populate the CAM table. IP addresses are Layer 3 addresses that are typically used to populate the routing table, which is stored in the Ternary Content Addressable Memory (TCAM) table.

Reference:

CCNA 200-301 Official Cert Guide, Volume 1, Chapter 5: Analyzing Ethernet LAN Switching, Learning MAC Addresses

Cisco: Catalyst 6500/6000 Switches ARP or CAM Table Issues Troubleshooting: Background Information

Category: Network Fundamentals


### Which of the following addresses will a switch use to make forwarding decisions? (Select the best answer.)
A. source MAC addresses

B. source IP addresses

C. destination IP addresses

D. destination MAC addresses

The answer is D. destination MAC addresses

Explanation:

A switch will use destination Media Access Control (MAC) addresses to make forwarding decisions. Switches make forwarding decisions based on the destination MAC address contained in a frame's header. The switch first searches the Content Addressable Memory (CAM) table for an entry that matches the frame's destination MAC address. The CAM table, which is also called the switching table, is used by a switch to discover the relationship between the Layer 2 address of a device and the physical port used to reach the device. If the frame's destination MAC address is not found in the table, the switch forwards the frame to all its ports, except the port from which it received the frame. If the destination MAC address is found in the table, the switch forwards the frame to the appropriate port. The source MAC address is also recorded if it did not previously exist in the CAM table.

A switch will not use source MAC addresses to make forwarding decisions. However, a switch will use source MAC addresses to populate the CAM table by recording the source MAC address of an inbound Layer 2 frame and the corresponding switch port that the frame arrived on.

A switch will not use source or destination Internet Protocol (IP) addresses to make forwarding decisions. IP addresses are Open Systems Interconnection (OST) Layer 3 addresses and are typically used by devices such as routers to make forwarding decisions.

Reference:

CCNA 200-301 Official Cert Gulde, Volume 1, Chapter 5: Analyzing Ethernet LAN Switching, Leaming MAC Addresses

Cisco: Catalyst 6500/6000 Switches ARP or CAM Table Issues Troubleshooting: Background Information.

Category: Network Fundamentals
