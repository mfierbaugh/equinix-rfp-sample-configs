# Syslog 5424 format

**Priority:** P2  
**Feature group:** Observation & Telemetry

## Overview

**RFC 5424** syslog structured data can be sent to remote servers using **logging** with **structured-data** where supported.

## Sample IOS XR configuration

```text
logging 198.51.100.250 vrf MGMT severity info
logging structured-data
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
