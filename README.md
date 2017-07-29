Welcome to the Networking-Tools wiki!

# Network Interfaces 

Get get the peer ifindex of a veth interface with ethtool.

    # ethtool -S veth1
    NIC statistics:
      peer_ifindex: 7


# Queueing

## Show queue length and statistics

    tc -s -p qdisc show
    qdisc mq 0: dev eth0 root 
      Sent 787136348 bytes 1146663 pkt (dropped 0, overlimits 0 requeues 8004) 
      backlog 0b 0p requeues 8004`

# Open vSwitch

## Check what OVS does to a packet

`ovs-appctl ofproto/trace br0 in_port=1,dl_dst=01:80:c2:00:00:05`

Details here: [Open vSwitch Advanced Features Tutorial](http://git.openvswitch.org/cgi-bin/gitweb.cgi?p=openvswitch;a=blob_plain;f=tutorial/Tutorial;hb=HEAD)

## Show mac forwarding table

Equivalent to `show mac address-table` on Cisco devices:
`ovs-appctl fdb/show br0`

## Show DPDK statistics

`ovs-appctl dpif-netdev/pmd-stats-show`

## Enable IGMP Snooping

`ovs-vsctl set Bridge switch0 mcast_snooping_enable=true`
