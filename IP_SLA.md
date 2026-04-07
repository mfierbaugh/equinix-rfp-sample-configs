# IP SLA

**Priority:** P1  
**Feature group:** —

## Overview

**IP SLA** probes (e.g., **ICMP echo**) measure latency/jitter toward targets; results can trigger **track objects** or **policy** actions.

## Configuration source (Cisco 8000, IOS XR 26.x)

[Implementing IP Service Level Agreements](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/system-monitoring/26xx/configuration/guide/b-system-monitoring-cg-cisco8k-26xx/implementing-ip-service-level-agreements.html) (see also [IP Addresses and Services](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/ip-addresses/26xx/configuration/guide/b-ip-addresses-cg-8k-26xx.html) for related topics).

## Sample IOS XR configuration

```text
ipsla
 operation 1
  type icmp echo
   destination address 198.51.100.77
   source address 192.0.2.1
   frequency 10
  !
 !
 schedule operation 1
  life forever
  start-time now
 !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
