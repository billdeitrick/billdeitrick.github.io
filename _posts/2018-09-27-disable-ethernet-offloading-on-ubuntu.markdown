---
layout: post
title: "Disabling Ethernet Offloading on Ubuntu"
date: "2018-09-27 17:28:00 -0500"
excerpt: "Disable ethernet offload on Ubuntu for packet sniffing."
---

## Introduction

Today I was troubleshooting an MTU issue with an IPSEC VPN link and I noticed something odd with both Wireshark and tcpdump. I was capturing packets with an MTU greater than 1500 on an ethernet network! This is impossible! Turns out, offloading on my NIC was automagically lumping TCP packets together. Furthermore, this is common in modern TCP/IP stacks, and while it definitely helps performance on gbps and faster links, it's a pain when trying to actually troubleshoot MTU issues. Fortunately, at least on my Ubuntu sniffer box, this feature was easy to disable.

## The fix

Here's my new config in `/etc/network/interfaces` for my sniffing interface that helps ensure I'm better capturing what's _actually_ happening on the wire:

```
# The sniffing interface
auto eno1
iface eno1 inet manual
offload-tx off
offload-rx off
offload-sg off
offload-tso off
offload-rxvlan off
offload-txvlan off
```

Of course, you probably don't want to do this on a production box. My setup uses a dedicated sniffer box with one interface for sniffing and another for remote connections. Adding the above on just my sniffing interface worked like a charm!

## Further Reading

There's lots more nitty gritty detail here; check out the links below!

* [Disable TCP-Offloading {completely, generically and easily}](https://serverfault.com/questions/421995/disable-tcp-offloading-completely-generically-and-easily)
* [Linux Networking: How to disable/enable offload features, RX/TX checksum, scatter, gather and beyond](http://docs.gz.ro/node/282)
* [JLS2009: Generic receive offload](https://lwn.net/Articles/358910/)

# Bonus

You can also accomplish the above temporarily with ethtool. To see what features are currently turned on or off for your interface, you can run:

```bash
ethtool -k eno1 # Where <eno1> is your interface:w
```