---
author: Jason Davis
layout: post
title: CenturyLink IPv6 using 6rd on Linux router
---

After PPPoE is configured...

/etc/ppp/ip-up.d/0ip6up
```bash
#!/bin/bash
PATH=$PATH:/usr/sbin

#ref: https://kradalby.no/setting-up-6rd-on-my-linux-router.html

PREFIX=2602::
PREFIX_LENGTH=24
RELAY_PREFIX=205.171.2.64
RELAY_PREFIX_LENGTH=0
PUBLIC=`ip -o route get 8.8.8.8 | sed 's/.* src \([0-9.]*\) .*/\1/'`

IPv6_PREFIX=`ipv6calc --action 6rd_local_prefix --6rd_prefix $PREFIX/$PREFIX_LENGTH --6rd_relay_prefix $RELAY_PREFIX/$RELAY_PREFIX_LENGTH $PUBLIC`
echo ${IPv6_PREFIX::-5}
#Returns /56 but CTL uses 64 ¯\_(ツ)_/¯
#2602:12:34:56::/56

# IPv6 Prefix
IPv6_PREFIX=${IPv6_PREFIX::-5}
IPv6_PREFIX_LENGTH=64

ip tunnel add 6rd mode sit local $PUBLIC ttl 64
ip tunnel 6rd dev 6rd 6rd-prefix $PREFIX/$PREFIX_LENGTH
ip link set 6rd up
ip -6 addr add $IPv6_PREFIX::1/$PREFIX_LENGTH dev 6rd
#ip -6 addr add $IPv6_PREFIX::/$PREFIX_LENGTH dev 6rd
ip -6 route add ::/0 via ::$RELAY_PREFIX dev 6rd

LAN_INTERFACE=lan0
ip -6 addr add $IPv6_PREFIX::1/$IPv6_PREFIX_LENGTH dev $LAN_INTERFACE

``` 

/etc/ppp/ip-down.d/0ip6down
```bash
#!/bin/bash
PATH=$PATH:/usr/sbin

ip tunnel del 6rd

LAN_INTERFACE=lan0
ip -6 addr flush dev $LAN_INTERFACE to 2602::/24
```