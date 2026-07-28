# FortiGate 60F NAT and Internet Access

## Project Overview

This document describes my practical approach to configuring and validating outbound internet access through a FortiGate 60F firewall.

The work includes source NAT, LAN-to-WAN connectivity, public IP verification, DNS testing, routing checks and troubleshooting.

All production names, addresses and identifiers are generalized for confidentiality.

## Purpose of NAT

Internal devices normally use private IP addresses that cannot communicate directly across the public internet.

Source NAT allows the FortiGate firewall to translate internal private addresses into an approved public address when traffic leaves through a WAN interface.

## Configuration Objectives

The configuration was designed to:

- Provide controlled internet access to internal users
- Translate private addresses for outbound communication
- Support multiple WAN connections
- Ensure traffic exits through the intended ISP link
- Maintain connectivity during WAN changes or migration
- Support troubleshooting through traffic logs
- Protect internal addressing information

## NAT Components

| Component | Purpose |
|---|---|
| Incoming interface | Identifies the internal source network |
| Outgoing interface | Identifies the WAN connection |
| Source address | Defines authorized internal devices or networks |
| Destination address | Defines the allowed internet destination |
| Service | Defines permitted protocols and ports |
| NAT | Enables source-address translation |
| IP pool | Uses a specified public address when required |
| Logging | Records permitted or denied traffic |

## Example Outbound Policy

```text
Policy Name: User-Network-to-Internet
Incoming Interface: Internal VLAN
Outgoing Interface: Primary WAN
Source: Authorized User Network
Destination: Internet
Services: DNS, HTTP, HTTPS and approved applications
Action: Accept
NAT: Enabled
Logging: Enabled
