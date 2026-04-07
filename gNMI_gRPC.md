# gNMI / gRPC

**Priority:** P1  
**Feature group:** Telemetry & Observability

## Overview

**gNMI** (often with **gRPC**) provides subscription-based telemetry and RPC-based configuration on IOS XR. Enable **grpc** and **gnmi** under telemetry.

## Configuration source (Cisco 8000, IOS XR 26.x)

[Telemetry Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/telemetry/26xx/configuration/guide/b-telemetry-cg-8000-26xx.html); [Programmability Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/programmability/b-programmability-configuration-guide-cisco8000.html) (gRPC, telemetry).

## Sample IOS XR configuration

```text
grpc
 port 57400
!
telemetry model-driven
 destination-group DG1
  address-family ipv4 198.51.100.60 port 57400
 !
 sensor-group SG1
  sensor-path Cisco-IOS-XR-infra-statsd-oper:infra-statistics/interfaces/interface/latest/generic-counters
 !
 subscription SUB1
  sensor-group-id SG1 sample-interval 10000
  destination-id DG1
 !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
