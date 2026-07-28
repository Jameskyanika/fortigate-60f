# FortiGate 60F Firewall Policy Administration

## Project Overview

This document describes my practical approach to configuring, reviewing and troubleshooting firewall policies on a FortiGate 60F.

The objective of firewall policy administration is to permit authorized business traffic while preventing unnecessary or unauthorized communication between internal networks, external services and internet connections.

All names, IP addresses and production details are generalized for confidentiality.

## Policy Objectives

Firewall policies were designed or reviewed to support:

- Secure internet access for internal users
- Controlled communication between VLANs
- Separation of departmental networks
- Access to approved business applications
- Multi-WAN internet connectivity
- NAT for outbound traffic
- Logging and troubleshooting
- Restriction of unnecessary services

## Policy Design Principles

The following principles were applied when planning firewall rules:

- Follow the principle of least privilege
- Permit only required traffic
- Use clearly named address and service objects
- Separate policies by source network and purpose
- Place specific rules above broad rules
- Enable logging for important traffic
- Avoid unnecessary `ANY` source, destination or service objects
- Review unused or duplicate policies
- Document the business purpose of every rule
- Test policies after configuration changes

## Policy Components

A FortiGate firewall policy normally includes:

| Component | Purpose |
|---|---|
| Policy name | Identifies the rule and its business purpose |
| Incoming interface | Network where traffic originates |
| Outgoing interface | Network or WAN where traffic is sent |
| Source | Authorized device, subnet or address group |
| Destination | Approved server, network or internet destination |
| Service | Permitted protocol or application port |
| Action | Allow or deny |
| Schedule | Time during which the rule is active |
| NAT | Translates private addresses for internet access |
| Security profiles | Applies additional inspection where configured |
| Logging | Records traffic for monitoring and troubleshooting |

## Example Sanitized Policy Categories

### Internal LAN to Internet

Purpose:

- Permit authorized users to access approved internet services
- Apply source NAT
- Record traffic for troubleshooting

Typical services:

- DNS
- HTTP
- HTTPS
- Approved business applications

### Back-Office Network to Internet

Purpose:

- Provide internet connectivity through the assigned WAN link
- Separate back-office traffic from the primary operational network
- Apply appropriate bandwidth and security controls

### VLAN-to-VLAN Communication

Purpose:

- Allow only required communication between segmented networks
- Restrict unnecessary lateral access
- Protect sensitive systems

Example:

```text
Source VLAN: User Network
Destination VLAN: Application Server Network
Allowed Services: Required application ports only
Default Behaviour: Deny all other traffic
