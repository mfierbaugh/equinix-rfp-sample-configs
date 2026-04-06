# Monitoring

**Priority:** P1  
**Feature group:** —

## Overview

**Monitoring** includes **TCAM** / **ACL** resource visibility, **telemetry** exports, and **OAM** where applicable. Use **show platform** / **show controllers** and **MDT** for utilization.

## Sample IOS XR configuration

```text
telemetry model-driven
 destination-group DG-MON
  address-family ipv4 198.51.100.99 port 57400
!
! Platform resource commands are release-specific
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
