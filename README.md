# Platform Engineering Lab

This repository documents the design, implementation, validation, and ongoing evolution of a hands-on infrastructure platform built for practical systems, network, cloud, and security engineering.

The goal is not simply to deploy individual servers or appliances. Each lab is treated as a small engineering project with an emphasis on architecture, operational safety, recoverability, security boundaries, testing, and clear technical documentation.

The environment currently combines physical networking equipment, Proxmox VE, Windows Server 2025 with Hyper-V, Linux services, firewalls, virtual machines, containers, monitoring, backup systems, and automation tooling. These technologies are the present implementation stack; the broader purpose of the repository is to demonstrate platform-engineering principles that remain applicable across on-premises, hybrid, and cloud environments.

## What This Repository Demonstrates

- Infrastructure architecture and design decisions
- Linux and Windows server administration
- Proxmox VE and Hyper-V virtualization
- Network segmentation, routing, NAT, DHCP, and firewall policy
- Secure management-path design and failure recovery
- Multi-hypervisor integration
- Monitoring, logging, backup, and operational validation
- Infrastructure automation and repeatable configuration
- Technical documentation suitable for handoff, troubleshooting, and future expansion

## Engineering Approach

The work in this repository follows several practical principles:

### Architecture before implementation

Each lab begins with a defined purpose, traffic flow, addressing plan, trust boundaries, and recovery strategy. Configuration steps are documented in the context of the design rather than presented as isolated commands.

### Safe change management

Management access is preserved while new interfaces, routes, firewall policies, and virtual networks are introduced. Changes are tested incrementally so that failures can be isolated and reversed without unnecessarily disrupting the wider environment.

### Explicit security boundaries

Networks and workloads are separated according to function. Communication is permitted through documented firewall policies rather than assumed through flat Layer 2 connectivity. Broad policies may be used temporarily for initial validation, then refined as the lab matures.

### Validation and evidence

Labs include routing checks, interface-state verification, firewall-policy tests, NAT validation, host-firewall testing, and documented results. The focus is on proving that the architecture works as intended.

### Operational documentation

The repository records not only the final state, but also the reasoning, tradeoffs, recovery paths, and lessons learned. Sensitive details are excluded so that the material remains suitable for public review.

## Current Platform Direction

The platform is evolving into a mixed infrastructure environment that can support:

- Windows and Linux server workloads
- Active Directory, DNS, DHCP, and identity labs
- Proxmox and Hyper-V virtual machines
- Segmented management, server, client, monitoring, and security networks
- Firewall, VPN, routing, and packet-analysis exercises
- Infrastructure-as-code and configuration automation
- Monitoring, alerting, logging, backup, and recovery workflows
- Hybrid-cloud and Azure integration experiments

## Network and Security Labs

### FortiGate Hybrid Hypervisor Lab

A physical FortiGate 80E is used as the routed security boundary between a Proxmox VE environment and a Windows Server 2025 Hyper-V environment.

The design includes:

- Separate routed subnets for Proxmox and Hyper-V
- Bidirectional FortiGate firewall policies
- NAT-based Internet access for lab workloads
- Dedicated Proxmox and Hyper-V management paths
- A second Proxmox Linux bridge for FortiGate-controlled workloads
- Persistent routing between both hypervisor environments
- Windows Firewall controls and end-to-end connectivity validation
- Mermaid diagrams showing management, inter-lab, and Internet traffic paths

Documentation:

[`docs/architecture/fortigate-hybrid-hypervisor-lab.md`](docs/architecture/fortigate-hybrid-hypervisor-lab.md)

### pfSense Enterprise Firewall Lab

This lab documents the development of a structured pfSense network baseline, including architecture decisions, interface roles, segmentation strategy, and the foundation required for later security and service deployment.

Documentation:

[`docs/architecture/pfsense-phase-2-network-baseline.md`](docs/architecture/pfsense-phase-2-network-baseline.md)

## Repository Structure

```text
platform-engineering-lab/
├── README.md
└── docs/
    └── architecture/
        ├── fortigate-hybrid-hypervisor-lab.md
        └── pfsense-phase-2-network-baseline.md
```

The repository will continue to use one main project with a dedicated document or folder for each major lab. This keeps the platform architecture visible as a whole while allowing each implementation to be documented independently.

## Skills Demonstrated

| Area | Technologies and Practices |
|---|---|
| Virtualization | Proxmox VE, Hyper-V, Linux bridges, virtual switching |
| Networking | IPv4 addressing, routing, static routes, DHCP, NAT, VLAN planning |
| Security | FortiGate, pfSense, firewall policy, host firewalls, segmentation, implicit deny |
| Systems | Windows Server, Debian/Linux, interface configuration, service validation |
| Operations | Change safety, troubleshooting, recovery paths, configuration validation |
| Documentation | Architecture diagrams, implementation records, test evidence, sanitized public documentation |

## Security and Publication Scope

This is a public technical portfolio repository. Documentation may include private RFC 1918 subnet ranges, generic device roles, sanitized configuration examples, and architecture diagrams.

The repository does not intentionally publish:

- Passwords, API tokens, private keys, or recovery codes
- Public WAN addresses
- Device serial numbers, licence identifiers, or support-entitlement details
- VPN pre-shared keys or certificates
- MAC addresses or complete production configuration exports
- Screenshots containing active sessions or sensitive identifiers

## Roadmap

Planned areas of development include:

1. Refine broad firewall rules into named address objects and service-specific policies.
2. Create Hyper-V external virtual switches for dedicated lab workloads.
3. Attach selected Proxmox VMs to the FortiGate-controlled `vmbr1` network.
4. Introduce VLANs for management, servers, clients, monitoring, and security tooling.
5. Deploy Active Directory, DNS, DHCP, and certificate services.
6. Add centralized logging, monitoring, alerting, and packet-capture workflows.
7. Expand backup, restore, and disaster-recovery testing.
8. Introduce Terraform, Ansible, PowerShell, and other automation where appropriate.
9. Extend selected workloads into Azure and hybrid-cloud scenarios.

## Purpose

This repository is intended to provide clear evidence of practical infrastructure-engineering work. It is written for technical reviewers, hiring managers, engineers, and interviewers who want to understand not only what was built, but how the design was reasoned through, secured, tested, and prepared for future growth.
