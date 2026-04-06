# Statistics on all levels

**Priority:** P1  
**Feature group:** —

## Overview

**Interface**, **QoS**, **routing**, and **telemetry** statistics are available via **CLI**, **SNMP**, **Model-Driven Telemetry (MDT)**, and **gNMI**. On **Cisco 8000**, production MDT often uses a **destination-group** (gRPC dial-out to a collector), multiple **sensor-group** definitions, and **subscription** stanzas with **strict-timer**, **sample-interval**, **source-interface**, and **destination-id**. The **dataplane-monitor** group below includes the **Cisco-IOS-XR-8000-platforms-npu-resources-oper** **hw-resources-data** sensor path for **NPU hardware resource** telemetry alongside **OFA** and **FIB** summaries. Full deployments typically add further sensor groups (BFD, L2VPN, optics, BGP, interfaces, etc.); **gRPC** dial-in and **SNMP** remain available for other access patterns.

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
