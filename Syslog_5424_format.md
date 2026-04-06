# Syslog 5424 format

**Priority:** P2  
**Feature group:** Observation & Telemetry

## Overview

**RFC 5424** syslog uses **`logging format rfc5424`** on IOS XR together with **trap** level, **facility**, remote **logging** hosts (**VRF**, **port**), **source-interface**, and optional **hostnameprefix**. Pair with **ssh server logging** when SSH session logging is required.

## Sample IOS XR configuration

```text
logging trap informational
logging format rfc5424
logging console debugging
logging monitor debugging
logging facility local7
logging 198.18.201.22 vrf Mgmt-intf port 7514
logging 198.18.201.23 vrf Mgmt-intf port 6514
logging source-interface MgmtEth0/RP0/CPU0/0
logging hostnameprefix 8711-AGG-32
ssh server logging
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
