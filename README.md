PAFLib
======

PAFLib is a IBM written library which exposes Power Architecture Facilities to
userspace via an API. This includes the Data Stream Control Register Facility
(DSCR) and the Event-Based Branching facility (EBB). Linux kernel 3.9 has exposed
problem-state DSCR usage for ISA 2.06 (POWER7 – emulated) and ISA 2.07 (POWER8
– in hardware). Linux 3.10 has exposed the EBB facility.


Event Based Branching
=====================

To use the EBB library Just link to -lpaf-ebb. The system must be POWER ISA
2.07 compliant (POWER8+) to get EBB functionality.


Data Stream Control Register
============================

To use the DSCR library just link to -lpaf-dsc. The system must be POWER ISA
2.05 compliant (POWER6+) to get DSCR functionality and depending of the system
supportted ISA the DSCR will operate in a different manner:

 * Power ISA 2.05 (POWER6): SSE (Store Stream Enable) and DPFD (Default Prefetch
   Depth);
 * Power ISA 2.06 (POWER7): SNSE (Stride-N Stream Enable);
 * Power ISA 2.06+ (POWER7+): LSD (Load Stream Disable)
 * Power ISA 2.07 (POWER8): URG (Depth Attainment Urgency), SWTE (Software
   Transient Enable), HWTE (Hardware Transient Enable), STE (Store Transient
   Enable), LTE (Load Transient Enable), SWUE (Software Unit Count Enable),
   HWUE (Hardware Unit Count Enable), and UNITCNT (Unit Count).
   
Also depending of the ISA the access to DSCR is privileged or not:

 * Power ISA 2.05/2.06/2.06+: Privileged
 * Power ISA 2.07: Problem-state (userland accessible).
