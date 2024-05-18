# Learning EP 2
All learning from https://youtu.be/p9ScLm9S3B4?si=lzUbWW49GKSJwct7

## ARP Frames
Here the device is trying to figure out what 10.1.1.2's MAC address is so it can send a frame/packet to that device:

This device will start by sending what's called an ARP Packet:
```
Layer 2: Ethernet II Header
00D0.9752.8936 >> FFFF.FFFF.FFFF
ARP Packet Src. IP: 10.1.1.3, Dest. IP: 10.1.1.2
```
* 10.1.1.3: The source IP
* 10.1.1.2: The destination IP
* 00D0.9752.8936: The source MAC address
* FFFF.FFFF.FFFF: The destination MAC address, this specific one is called a broadcast address, it's the layer2/switch equivalent of screaming "Who belongs to 10.1.1.2"

What happens is this frame is sent to the switch, the switch then sends the frame to all devices on layer 1.

When a device receives this ARP frame, the device will be like "I'm not 10.1.1.2" (doesn't actually send a frame back to the router), unless it is 10.1.1.2 - this device will then say "Hey, That's me. I'm your guy.", well really he will be sending his MAC address back to the switch, who will return it to the original sender (10.1.1.3), this is the only device that will respond. 10.1.1.3 will now know what 10.1.1.2's MAC Address is.

ARP Response:
```
Layer 2: Ethernet II Header
00D0.9752.8936 << 00E0.4C68.13A6
ARP Packet: Src. IP: 10.1.1.2, Dest. IP: 10.1.1.3
```

Summary:
* ARP is used to map IP addresses to MAC addresses on a local network.
* ARP requests are broadcast to all devices, while ARP responses are unicast back to the requester.
* This process allows devices to communicate using MAC addresses once the IP-to-MAC mapping is known.

## What happens if you connect two switches together, with no router?
1. We enter a command the command ```ping 23.227.38.65``` (the device sending the ping request is on 10.1.1.3)
2. The device sends an ICMP and ARP Packet (attempting to reach a device on another network - via the second router)
3. In the ARP package, something seems off, the device is trying to reach 10.1.1.1??? We're looking for 23.227.38.65.
```
Layer 2: Ethernet II Header
00D0.9752.8936 >> FFFF.FFFF.FFFF
ARP Packet Src. IP: 10.1.1.3, Dest. IP: 10.1.1.1
```
This is because the source knows that 23.227.38.65 isn't on its network. This device isn't even going to try to connect to that server/discover the MAC address.

The device does this because 10.1.1.1 is its Gateway or Router.

The device knows that any device has the IP range of 10.1.1.0 through to 10.1.1.255 that that device is on its network. But if that device tries to reach a device OUTSIDE of that range, it knows that it needs help from another device to connect the device on another network, this is where a router comes in.

## Router
How will the device at 10.1.1.3 reach the device at 23.227.38.65?

Well, this is what routers are made for, connecting to other switches/networks.

