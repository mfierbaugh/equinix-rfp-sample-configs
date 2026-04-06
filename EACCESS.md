# E-Access (EPL & EVPL)

**Context:** Equinix **E-Access** handoff — access-side Ethernet toward the UNI. Separate samples for **EACCESS EPL** and **EACCESS EVPL** are in `EACCESS_EPL.md` and `EACCESS_EVPL.md`.

## `l2transport` placement

- **EPL / port handoff:** configure `l2transport` on the **main physical** interface before xconnect.
- **EVPL:** configure `l2transport` **only on the subinterface** (VLAN attachment circuit). Do **not** add `l2transport` on the parent physical interface.

## Sample: main interface + EPL-style xconnect

```text
! Main physical interface — L2 transport mode (EPL / port handoff)
interface GigabitEthernet0/0/0/20
 l2transport
!
l2vpn
 xconnect group ACC1
  p2p ACC-EPL
   interface GigabitEthernet0/0/0/20
   neighbor ipv4 198.51.100.10 pw-id 3010
!
```

## Sample: EVPL (subinterface only)

```text
! EVPL: only the subinterface uses l2transport
interface GigabitEthernet0/0/0/21.100 l2transport
 encapsulation dot1q 100 second-dot1q 200
 rewrite ingress tag push dot1q 100 symmetric
!
l2vpn
 bridge group ACC-EVPL
  bridge-domain BD-ACC
   interface GigabitEthernet0/0/0/21.100
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax and feature availability for your release (K100/P100).
