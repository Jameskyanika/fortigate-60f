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
## SD-WAN Traffic Steering and Validation Evidence

During the Multi-WAN implementation, four ISP connections were incorporated into the FortiGate SD-WAN environment.

The sanitized link structure consisted of:

| Provider | Capacity | Role |
|---|---:|---|
| ISP Alpha | 100 Mbps | High-capacity primary connection |
| ISP Alpha | 25 Mbps | Secondary connection |
| ISP Beta | 50 Mbps | Existing or backup connection |
| ISP Beta | 16 Mbps | Legacy backup connection |

The SD-WAN configuration was intended to improve internet availability and direct client traffic through an appropriate healthy connection.

Validation activities included:

- Confirming that all ISP links were represented in the SD-WAN environment
- Checking public egress addresses from different network endpoints
- Confirming that different endpoints could use different WAN paths
- Testing access to a required business application
- Coordinating validation with remote technical support teams
- Rechecking application accessibility after WAN changes

The original communication evidence is retained privately. Names, public IP addresses, organizations and application details are excluded from the public portfolio.
## Supporting Validation Evidence

The ISP migration was validated through coordinated testing from multiple network points.

The validation activities included:

- Confirming that the new WAN links presented the expected public addresses
- Comparing public egress addresses from different test locations
- Reviewing FortiGate SD-WAN and WAN-interface configuration
- Testing access to required business applications
- Confirming that traffic used the intended ISP connection
- Coordinating follow-up testing with remote technical teams
- Verifying readiness before final production use

The original communication records are retained privately.
