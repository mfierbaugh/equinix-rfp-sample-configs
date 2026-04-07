# Netconf/Yang

**Priority:** P1  
**Feature group:** —

## Overview

**NETCONF** and **YANG** models on IOS XR enable structured configuration and RPCs. Enable **netconf-yang** and restrict access via **SSH** and **VRF** management.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-programmability-configuration-guide-cisco8000.pdf** (netconf-yang agent).

## Sample IOS XR configuration

```text
ssh server v2
ssh server netconf vrf default
netconf-yang agent
 ssh
!
! Example: connect with ncclient / gnmi clients to port 830
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
