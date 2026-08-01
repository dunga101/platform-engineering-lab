# Platform Engineering Lab

This repository documents hands-on infrastructure labs built to develop and
demonstrate practical skills in Linux administration, virtualization,
networking, and security.

The focus is on building clean, reproducible server baselines and documenting
decisions, tradeoffs, and recovery strategies in a way that mirrors real-world
IT and infrastructure work.

## Network & Security Labs

- **pfSense Enterprise Firewall Lab**
  - Phase 2: Core Network Baseline  
  - Architecture and design decisions documented in  
    `docs/architecture/pfsense-phase-2-network-baseline.md`

- **FortiGate Hybrid Hypervisor Lab**
  - Physical FortiGate 80E integrated with Proxmox VE and Windows Server 2025 Hyper-V
  - Separate routed lab networks, bidirectional firewall policies, NAT, DHCP, and independent management paths
  - Architecture and validation documented in
    `docs/architecture/fortigate-hybrid-hypervisor-lab.md`
