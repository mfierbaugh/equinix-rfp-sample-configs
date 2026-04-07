# IP SLA

**Priority:** P1  
**Feature group:** —

## Overview

**IP SLA** probes (e.g., **ICMP echo**) measure latency/jitter toward targets; results can trigger **track objects** or **policy** actions.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-ip-addresses-cg-8k-26xx.pdf** / IP SLA feature guide topics in Cisco 8000 26.x doc set.

## Sample IOS XR configuration

```text
ipsla
 operation 1
  type icmp echo 198.51.100.77 source-interface Loopback0
  frequency 10
 !
!
ipsla schedule operation 1 life forever start-time now
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
