# Netflow

**Priority:** P1  
**Feature group:** —

## Overview

**NetFlow / IPFIX** exports flow records to a collector. Configure **flow monitors**, **exporters**, and apply to **interfaces**.

## Sample IOS XR configuration

```text
flow monitor-map FM-IPFIX
 record ipv4
 exporter EXP1
!
flow exporter-map EXP1
 destination 198.51.100.250
 source Loopback0
 transport udp 4739
!
sampler-map SM1
 random 1 out-of 1000
!
interface GigabitEthernet0/0/0/0
 flow ipv4 monitor FM-IPFIX sampler SM1 ingress
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
