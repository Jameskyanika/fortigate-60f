# FortiGate 60F WAN Failover and Link Monitoring

## Project Overview

This document describes my practical approach to maintaining internet availability using multiple WAN connections on a FortiGate 60F firewall.

The objective was to monitor ISP-link health, prioritize the preferred connection and redirect traffic to an available backup link when the primary connection became unavailable.

All provider names, IP addresses, interface names and production details are generalized for confidentiality.

## Business Requirement

The enterprise environment required:

- Reliable internet connectivity
- A preferred high-capacity primary connection
- One or more backup ISP links
- Automatic or controlled failover
- Reduced disruption during ISP outages
- Continuous access to business applications
- Clear link-status monitoring
- Validation after service restoration

## Example Sanitized WAN Design

| Provider | Capacity | Sanitized Role |
|---|---:|---|
| ISP Alpha | 100 Mbps | Preferred primary link |
| ISP Alpha | 25 Mbps | Secondary business connection |
| ISP Beta | 50 Mbps | Transitional or backup link |
| ISP Beta | 16 Mbps | Legacy backup connection |

These values represent the documented project structure without publishing production addressing or circuit information.

## Failover Objectives

The configuration was intended to:

- Use the preferred WAN while it remained healthy
- Detect primary-link failure
- Redirect eligible traffic through an available backup connection
- Prevent traffic from using an unavailable gateway
- Restore the preferred path after service recovery
- Maintain firewall policy and NAT consistency
- Reduce business interruption

## FortiGate Components

WAN failover may involve:

| Component | Purpose |
|---|---|
| WAN interfaces | Represent the ISP connections |
| Static routes | Define available network paths |
| Administrative distance | Prioritizes routes |
| SD-WAN members | Groups WAN links for centralized control |
| Performance SLA | Measures link health and quality |
| Link monitor | Checks gateway or destination availability |
| SD-WAN rules | Select appropriate paths for traffic |
| Firewall policies | Permit traffic through the WAN environment |
| NAT | Translates internal addresses |
| Logs and events | Record failure and recovery activity |

## Health Monitoring

Link monitoring should test more than whether the physical interface is enabled.

Health checks may evaluate:

- Gateway reachability
- External destination reachability
- Packet loss
- Latency
- Jitter
- DNS availability
- Application accessibility

A physically active interface may still have no usable internet connection. Testing an external destination helps confirm whether the complete path is operational.

## Implementation Workflow

```text
Review all available ISP connections
                ↓
Identify primary and backup roles
                ↓
Configure or verify WAN interfaces
                ↓
Configure routes or SD-WAN members
                ↓
Define link-health checks
                ↓
Set path priorities
                ↓
Review firewall policies and NAT
                ↓
Test normal traffic flow
                ↓
Interrupt or disable the primary path
                ↓
Confirm backup-path operation
                ↓
Restore the primary connection
                ↓
Verify preferred-path recovery
                ↓
Document results
