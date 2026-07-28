# FortiGate 60F Security Hardening

## Project Overview

This document describes my practical approach to improving the security of a FortiGate 60F firewall and reducing unnecessary exposure of the management and network environment.

The objective is to protect administrative access, maintain secure firewall configurations, improve monitoring and reduce risks caused by weak settings, outdated firmware or overly broad access policies.

All production details are generalized for confidentiality.

## Security-Hardening Objectives

The hardening process focuses on:

- Restricting administrative access
- Using secure management protocols
- Protecting administrator accounts
- Reviewing firewall policies
- Reducing unnecessary services
- Maintaining firmware and security updates
- Enabling logging and monitoring
- Protecting configuration backups
- Reviewing WAN exposure
- Applying least-privilege access

## Administrator Account Security

Administrative accounts should be protected through:

- Strong and unique passwords
- Separate administrator accounts for authorized personnel
- Role-based administrator profiles
- Multi-factor authentication where available
- Restricted login sources
- Removal or disabling of unused accounts
- Monitoring of administrator login activity
- Avoidance of shared administrator credentials

## Trusted Hosts

Trusted hosts can be used to restrict administrator access to approved IP addresses or management networks.

Example:

```text
Administrator Access Allowed From:
- Authorized Management VLAN
- Approved Administrator Workstation
- Secure Remote Management Network

Administrator Access Blocked From:
- Guest Wi-Fi
- General User VLANs
- Untrusted Internet Sources
