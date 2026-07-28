# FortiGate 60F Multi-WAN ISP Migration and Failover

## Project Overview

This project documents the reconfiguration of an enterprise FortiGate 60F firewall during an ISP migration.

The environment required multiple internet links to support business continuity, traffic separation and failover.

All provider names, IP addresses, device names and organization details have been replaced or generalized for confidentiality.

## Business Requirement

The organization needed to:

- Introduce higher-capacity ISP connections
- Maintain the existing links during the migration period
- Minimize service interruption
- Preserve internet redundancy
- Separate primary, secondary and backup traffic
- Confirm that business systems remained reachable after the change

## WAN Environment

| Provider | Link | Sanitized Role |
|---|---:|---|
| ISP Alpha | 100 Mbps | Primary enterprise connection |
| ISP Alpha | 25 Mbps | Secondary and back-office connection |
| ISP Beta | 50 Mbps | Existing primary connection |
| ISP Beta | 16 Mbps | Existing backup connection |

## Technologies Used

- FortiGate 60F
- FortiOS
- Multi-WAN routing
- Firewall policies
- Source NAT
- WAN health monitoring
- Failover configuration
- Ping and public-IP verification
- ISP coordination and testing

## Implementation Workflow

```text
Review the existing WAN configuration
                ↓
Document all existing and new ISP links
                ↓
Configure the new WAN interfaces
                ↓
Set routing priorities and link roles
                ↓
Review and update firewall policies
                ↓
Configure outbound NAT
                ↓
Validate internet connectivity
                ↓
Verify the public egress IP address
                ↓
Test primary and backup link behaviour
                ↓
Confirm business application access
                ↓
Document the completed migration
