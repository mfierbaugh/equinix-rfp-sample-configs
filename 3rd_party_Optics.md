# 3rd party Optics

**Priority:** P1  
**Feature group:** Optics

## Overview

Third-party **MSA-compliant** optics are supported when validated; **DOM** diagnostics are read via **show controllers** / **optics** CLIs. Some platforms allow **breakout** speed selection per port.

## Sample IOS XR configuration

```text
! No universal config — verify transceiver in inventory
! Example: show controllers optics …
transceiver permit pid all
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
