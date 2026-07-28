# FortiGate 60F VLAN Segmentation

## Project Overview

This document describes my practical approach to using FortiGate 60F firewall interfaces and policies to separate enterprise networks into controlled VLAN segments.

The objective is to improve security, reduce unnecessary communication between departments, simplify traffic management and restrict access to sensitive systems.

All IP addresses, VLAN names, company identifiers and production details are generalized for confidentiality.

## VLAN Segmentation Objectives

The VLAN design was intended to:

- Separate departments and business services
- Restrict unnecessary communication between networks
- Reduce broadcast traffic
- Protect sensitive systems
- Apply different firewall policies to each network
- Support controlled access to shared services
- Improve troubleshooting and network visibility
- Separate wired, wireless, management and operational traffic

## Example Sanitized VLAN Design

| VLAN | Sanitized Name | Example Subnet | Purpose |
|---:|---|---|---|
| 10 | Administration | 10.10.10.0/24 | Administrative users |
| 20 | Operations | 10.10.20.0/24 | Operational systems |
| 30 | Corporate Wi-Fi | 10.10.30.0/24 | Authorized wireless users |
| 40 | CCTV | 10.10.40.0/24 | Surveillance devices |
| 50 | Server Network | 10.10.50.0/24 | Internal servers |
| 60 | Management | 10.10.60.0/24 | Network-device administration |
| 70 | Guest Wi-Fi | 10.10.70.0/24 | Internet-only guest access |

These values are examples and do not represent the live production environment.

## FortiGate VLAN Components

A VLAN interface on FortiGate typically includes:

| Component | Purpose |
|---|---|
| Interface name | Identifies the VLAN |
| VLAN ID | Tags traffic for the network segment |
| Parent interface | Physical or aggregate interface carrying the VLAN |
| IP address | Provides the VLAN gateway |
| Administrative access | Controls management protocols |
| DHCP service | Provides client addressing where required |
| Firewall policies | Controls traffic entering or leaving the VLAN |
| Security profiles | Applies inspection and filtering where configured |

## Tasks Performed

- Reviewed departmental network requirements
- Identified systems that required separation
- Created or reviewed VLAN interfaces
- Assigned VLAN IDs and gateway addresses
- Verified parent-interface configuration
- Confirmed switch trunk and access-port requirements
- Reviewed DHCP requirements
- Created address objects for VLAN networks
- Configured firewall policies between VLANs
- Restricted access to sensitive networks
- Tested authorized communication
- Verified blocked communication
- Documented the VLAN design

## Inter-VLAN Policy Design

Traffic between VLANs is controlled by firewall policies.

Example:

```text
Policy Name: User-VLAN-to-Application-Server
Incoming Interface: User VLAN
Outgoing Interface: Server VLAN
Source: Authorized User Network
Destination: Approved Application Server
Service: Required Application Port
Action: Accept
NAT: Disabled
Logging: Enabled
