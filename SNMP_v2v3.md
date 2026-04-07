# SNMP v2/v3

**Priority:** P1  
**Feature group:** Telemetry & Observability

## Overview

**SNMP** v2c and v3 for monitoring. Use **SNMPv3** auth/priv for security; restrict to management VRF and ACL.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-system-monitoring-cg-cisco8k-26xx.pdf**; **b-system-security-cg-cisco8000-26xx.pdf** (SNMP).

## Sample IOS XR configuration

```text
snmp-server vrf MGMT
snmp-server community READONLY RO IPv4 ACL-SNMP
snmp-server user MONITOR v3 auth sha <auth> priv aes 128 <priv>
snmp-server host 198.51.100.50 vrf MGMT version 3 priv MONITOR
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
