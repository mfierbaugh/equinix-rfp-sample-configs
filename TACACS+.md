# TACACS+

**Priority:** P1  
**Feature group:** System

## Overview

**TACACS+** provides centralized authentication, authorization, and accounting. Configure **multiple methods** with **fallback** to local users as needed.

## Configuration source (Cisco 8000, IOS XR 26.x)

[System Security Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/security/26xx/configuration/guide/b-system-security-cg-cisco8000-26xx.html) (AAA, TACACS+ server group).

## Sample IOS XR configuration

```text
tacacs-server host 198.51.100.100
 key TACACS_KEY
!
tacacs-server host 198.51.100.101
 key TACACS_KEY
!
aaa group server tacacs+ TAC-GROUP1
 server 198.51.100.100
 server 198.51.100.101
!
aaa authentication login default group TAC-GROUP1 local
aaa authorization exec default group TAC-GROUP1 local
aaa accounting exec default start-stop group TAC-GROUP1
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
