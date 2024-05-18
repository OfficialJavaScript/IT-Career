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
   1    00e0.b059.0a97    DYNAMIC     Fa0/1```
