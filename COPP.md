# COPP

**Priority:** P2  
**Feature group:** —

## Overview

**Control Plane Protection** includes **CoPP**, **control-plane ACL**, **rate limits**, and **LPTS** flow classification for protocol traffic to the RP/CPU.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-system-security-cg-cisco8000-26xx.pdf**; **b-routing-cg-cisco8000-26xx.pdf** (LPTS hardware police).

## Sample IOS XR configuration

```text
lpts pifib hardware police
 flow bgp known rate 10000
 flow icmp-default known rate 1000
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
