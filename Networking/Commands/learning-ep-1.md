# Learning EP 1

All learning from https://www.youtube.com/watch?v=9eH16Fxeb9o

Today (18/05/2024) - Today I learned and issued my first Cisco CLI command.

### Commands

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

### Layers:

Layer 1 (Physical Layer): This layer deals with the physical aspects of network communication, including the hardware used for transmitting and receiving data. It includes connectors, cables, switches, and hubs. The primary focus is on bit-level transmission between network nodes. While it doesn't use addresses like MAC or IP, it ensures that the physical signals are transmitted correctly.

Layer 2 (Data Link Layer): This layer uses MAC addresses to handle data transfer between devices on the same network. It ensures error-free transmission between devices and manages physical addressing through the use of MAC addresses.

Layer 3 (Network Layer): This layer is essential for inter-network communication. It handles logical addressing, packet routing, and forwarding, ensuring data can travel across diverse networks efficiently. Routers and protocols like IP, ICMP, OSPF, BGP, and RIP play crucial roles in enabling these functions, making it possible for devices to communicate over vast and varied network infrastructures.

### Packets and Frames
When a device sends a message to another device, the message is encapsulated into frames at the Data Link layer (Layer 2) of the OSI model. These frames contain the MAC addresses necessary for Layer 2 communication. As the frames travel across the network, they are forwarded by switches that operate at this layer. Once the frames reach the destination device, the Layer 2 information is stripped away, and what remains are the packets. These packets contain the logical addressing information (IP addresses) used at the Network layer (Layer 3).

To summarize:

* Sending Device: Encapsulates the message into frames (Layer 2) for transmission over the network.
* Network Transmission: Frames are forwarded by switches based on MAC addresses.
* Destination Device: Frames are decapsulated to reveal the packets (Layer 3), which contain IP addresses for further processing.

This process ensures that data is correctly transmitted and routed through the network, transitioning from frames at Layer 2 to packets at Layer 3.

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

