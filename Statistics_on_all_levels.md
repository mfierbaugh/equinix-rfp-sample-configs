# Statistics on all levels

**Priority:** P1  
**Feature group:** —

## Overview

**Interface**, **QoS**, **routing**, and **telemetry** statistics are available via **CLI**, **SNMP**, **Model-Driven Telemetry (MDT)**, and **gNMI**. Use **sensor-paths** for high-velocity counters.

## Sample IOS XR configuration

```text
telemetry model-driven
 sensor-group SG-IF
  sensor-path Cisco-IOS-XR-infra-statsd-oper:infra-statistics/interfaces/interface/latest/generic-counters
!
! Add subscription as needed
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
