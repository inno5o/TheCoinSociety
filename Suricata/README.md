# Suricata Network Intrusion Detection System

## Project Overview

This project documents the implementation of **Suricata** as a Network Intrusion Detection System (NIDS) within **TheCoinSociety** simulated enterprise network.

The environment was built using **GNS3 and VMware**, with Suricata deployed on an Ubuntu Server to monitor network traffic and detect suspicious or potentially malicious activity.

The project focuses on the practical deployment and configuration of Suricata, including network integration, rule management, traffic monitoring and alert verification.

## Environment

- **Network Environment:** GNS3
- **Virtualisation:** VMware
- **Operating System:** Ubuntu Server
- **IDS/IPS Platform:** Suricata
- **Organisation:** TheCoinSociety *(simulated environment)*

## Implementation Scope

The implementation covered:

- Deployment of Suricata on Ubuntu Server
- Integration into the GNS3 network environment
- Configuration of network interfaces and monitored networks
- Installation and updating of Suricata detection rules
- Configuration of `suricata.yaml`
- Verification of Suricata services and traffic monitoring
- Review of generated alerts using Suricata logs
- Basic network traffic and detection testing

## Project Structure

```text
Suricata/
├── README.md
├── Implementation/
│   └── README.md
└── Detection-Testing/
    └── README.md
```

### Implementation

Documents the deployment and configuration of Suricata within TheCoinSociety network.

### Detection Testing

Documents practical tests performed against the monitored network to verify that Suricata can identify and generate alerts for relevant network activity.

## Key Skills Demonstrated

- Network intrusion detection
- Suricata deployment and configuration
- Linux server administration
- Network traffic monitoring
- IDS rule management
- Security alert analysis
- Network troubleshooting
- GNS3 network simulation

## Outcome

Suricata was successfully deployed within TheCoinSociety environment and configured to monitor network traffic and generate security alerts based on configured detection rules.

This implementation provides the network-based detection component of the wider TheCoinSociety security monitoring environment.
