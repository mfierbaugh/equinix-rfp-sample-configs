# ZTP (Zero Touch Provisioning)

**Priority:** P2  
**Feature group:** —

## Overview

**ZTP** boots a device with DHCP/TFTP options to retrieve a bootstrap config. Typically combined with **secure bootstrap** and **certificate** onboarding.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-setup-and-upgrade-cisco8k.pdf** (ZTP/bootstrap).

## Sample IOS XR configuration

```text
! ZTP is bootstrap-time; ensure DHCP options 67/66 / ZTP script URL per design
! Example: archive bootstrap URL or pnpa discovery — platform specific
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
