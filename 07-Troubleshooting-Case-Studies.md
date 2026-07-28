# FortiGate 60F Troubleshooting Case Studies

## Overview

This document presents sanitized troubleshooting case studies involving FortiGate 60F firewall administration, ISP connectivity, Multi-WAN routing, NAT, VLAN communication and service restoration.

Organization names, provider names, IP addresses, usernames and production details have been replaced or generalized.

---

# Case Study 1: Packet Loss Affecting a Remote Business Application

## Problem

Users experienced slow or unreliable access to a remotely hosted business application.

## Symptoms

- Application pages opened slowly
- Some connection attempts failed
- Ping testing showed intermittent packet loss
- Local internet access remained partially available

## Investigation

The troubleshooting process included:

1. Confirming that the affected workstation had a valid IP address
2. Testing connectivity to the local gateway
3. Testing external internet destinations
4. Pinging the remote application address
5. Measuring packet loss and latency
6. Reviewing FortiGate WAN-interface status
7. Checking routing and firewall policies
8. Comparing results across available ISP connections
9. Escalating the issue to the ISP with technical evidence

## Finding

Local network connectivity was operational, but communication to the remote destination showed significant packet loss.

The evidence suggested that the problem was beyond the local access network and required ISP or upstream routing investigation.

## Resolution

- Test results were documented
- Packet-loss evidence was shared with the relevant technical teams
- ISP and remote-support teams investigated the affected path
- Connectivity was retested after corrective action

## Validation

- Ping tests were repeated
- Packet-loss levels were checked
- Application accessibility was confirmed
- Users verified that the service was operating normally

## Skills Demonstrated

- Ping and latency analysis
- Packet-loss investigation
- FortiGate WAN verification
- ISP escalation
- Remote-team coordination
- Service-restoration testing

---

# Case Study 2: Internet Outage and WAN Service Restoration

## Problem

Multiple systems became unreachable during an internet-service interruption.

## Symptoms

- Business devices appeared offline
- Remote systems could not connect to the site
- Firewall accessibility was affected
- Services began recovering intermittently

## Investigation

The investigation included:

- Checking whether the site had a power issue
- Confirming FortiGate availability
- Checking ISP equipment and upstream switches
- Reviewing WAN-interface status
- Testing gateway and internet reachability
- Coordinating an onsite equipment check
- Monitoring systems as they returned online

## Corrective Actions

- FortiGate and ISP equipment were checked
- A controlled restart was coordinated where necessary
- WAN connectivity was monitored during restoration
- Remote systems were tested as service returned

## Result

Affected systems gradually returned online and remote communication was restored.

## Lessons Learned

- Confirm power and physical connectivity early
- Check both firewall and ISP equipment
- Maintain an escalation path for restricted server-room access
- Verify every affected business service after connectivity returns
- Document outage timelines and restoration actions

---

# Case Study 3: Public IP Verification During ISP Migration

## Problem

New ISP links were being introduced, and the technical teams needed to confirm that traffic was leaving through the intended WAN connections.

## Objective

Verify that each test point presented the expected public egress address after the FortiGate Multi-WAN configuration was updated.

## Investigation

The validation process included:

1. Confirming WAN-interface addressing
2. Reviewing the selected FortiGate routing path
3. Checking LAN-to-WAN firewall policies
4. Confirming that NAT was enabled
5. Using an external public-IP verification service
6. Comparing results from multiple network points
7. Testing required business applications

## Possible Causes of an Unexpected Public IP

- Traffic using the wrong WAN interface
- Existing sessions remaining on a previous path
- Incorrect route priority
- SD-WAN rule selecting a different member
- Wrong firewall policy
- Incorrect IP-pool configuration
- ISP-side addressing changes

## Resolution Approach

- Review the active route
- Confirm the matching firewall policy
- Check the outgoing interface
- Verify NAT and IP-pool settings
- Clear or renew test sessions where appropriate
- Repeat public-IP verification

## Result

Public egress addresses were validated from the required test points, supporting the ISP migration and Multi-WAN implementation.

---

# Case Study 4: VLAN Communication Failure

## Problem

A system on one VLAN could not communicate with an approved server or service on another VLAN.

## Symptoms

- The source device could reach its gateway
- Internet access might still work
- Communication to the destination VLAN failed
- The destination could not be reached on the required application port

## Investigation

```text
Confirm the source IP address and VLAN
                ↓
Test the source VLAN gateway
                ↓
Confirm the destination IP address
                ↓
Verify switch trunk and access-port configuration
                ↓
Check the FortiGate VLAN interfaces
                ↓
Review the inter-VLAN firewall policy
                ↓
Confirm source, destination and service objects
                ↓
Inspect traffic logs
                ↓
Apply correction
                ↓
Retest the application
