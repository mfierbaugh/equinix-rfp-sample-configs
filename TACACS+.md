# TACACS+

**Priority:** P1  
**Feature group:** System

## Overview

**TACACS+** provides centralized authentication, authorization, and accounting. Configure **multiple methods** with **fallback** to local users as needed.

## Sample IOS XR configuration

```text
aaa group server tacacs+ TAC-GROUP1
 server 198.51.100.100
 server 198.51.100.101
!
aaa authentication login default group TAC-GROUP1 local
aaa authorization exec default group TAC-GROUP1 local
aaa accounting exec default group TAC-GROUP1
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
