# Monitoring

**Priority:** P1  
**Feature group:** —

## Overview

**Monitoring** covers **TCAM** / **ACL** usage, **platform** and dataplane **resource** visibility, **OAM**, and streaming exports. On **Cisco 8000**, **Model-Driven Telemetry** dial-out can use a **dataplane-monitor** **sensor-group** with **OFA** statistics, **FIB** summaries, and the **Cisco-IOS-XR-8000-platforms-npu-resources-oper** **hw-resources-data** path for **NPU hardware** telemetry—paired with **destination-group** (VRF, gRPC, encoding), **subscription** (**strict-timer**, **sample-interval**, **source-interface**), and CLI (**show platform** / **show controllers**) as needed for your release.

## Configuration source (Cisco 8000, IOS XR 26.x)

[Telemetry Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/telemetry/26xx/configuration/guide/b-telemetry-cg-8000-26xx.html); [System Monitoring Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/system-monitoring/26xx/configuration/guide/b-system-monitoring-cg-cisco8k-26xx.html).

## Sample IOS XR configuration

```text
! Cisco 8000 Model-Driven Telemetry (dataplane monitor + 8000 NPU hw-resources sensor path)
telemetry model-driven
 destination-group DGroup1
  vrf Mgmt-intf
  address-family ipv4 198.18.201.23 port 57400
   encoding self-describing-gpb
   protocol grpc no-tls
  !
 !
 sensor-group dataplane-monitor
  sensor-path Cisco-IOS-XR-platforms-ofa-oper:ofa/stats/nodes/node
  sensor-path Cisco-IOS-XR-fib-common-oper:fib/nodes/node/protocols/protocol/fib-summaries/fib-summary
  sensor-path Cisco-IOS-XR-platforms-ofa-oper:ofa/stats/nodes/node/Cisco-IOS-XR-8000-platforms-npu-resources-oper:hw-resources-datas/hw-resources-data
 !
 subscription dataplane-monitor
  sensor-group-id dataplane-monitor strict-timer
  sensor-group-id dataplane-monitor sample-interval 60000
  destination-id DGroup1
  source-interface MgmtEth0/RP0/CPU0/0
 !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
