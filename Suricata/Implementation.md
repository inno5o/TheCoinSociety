# Suricata Implementation

## Overview

Suricata was deployed on an **Ubuntu Server** within the simulated **TheCoinSociety** enterprise network built using GNS3 and VMware.

The objective was to configure Suricata as a **Network Intrusion Detection System (NIDS)** capable of monitoring network traffic and generating alerts when traffic matched configured detection rules.

---

## 1. Suricata Server Deployment

An Ubuntu Server virtual machine was deployed and connected to the appropriate network segment within the GNS3 environment.

Network connectivity was verified before installing Suricata.

> **Screenshot:** Suricata server within the GNS3 topology / network configuration.

---

## 2. Suricata Installation

Suricata was installed on the Ubuntu Server and the installation was verified.

```bash
sudo apt update
sudo apt install suricata -y
```

The installed version and service status were checked using:

```bash
suricata --build-info
sudo systemctl status suricata
```

> **Screenshot:** Successful Suricata installation and service status.

---

## 3. Detection Rule Updates

Suricata's detection rules were updated using `suricata-update`.

```bash
sudo suricata-update
```

This provided the IDS with an updated ruleset for identifying suspicious network activity.

> **Screenshot:** Successful Suricata rule update.

---

## 4. Suricata Configuration

The main Suricata configuration file was configured at:

```text
/etc/suricata/suricata.yaml
```

The configuration included defining the network ranges belonging to TheCoinSociety environment and selecting the interface Suricata would monitor.

The configuration was validated before restarting the service.

```bash
sudo suricata -T -c /etc/suricata/suricata.yaml
```

> **Screenshot:** `suricata.yaml` configuration and successful configuration test.

---

## 5. Network Interface Monitoring

Suricata was configured to inspect traffic passing through the designated network interface.

Available interfaces were verified using:

```bash
ip addr
```

The required interface was then configured within Suricata.

This allowed Suricata to inspect traffic traversing the monitored network segment.

> **Screenshot:** Network interface configuration.

---

## 6. Service Verification

After configuration, Suricata was restarted to apply the changes.

```bash
sudo systemctl restart suricata
sudo systemctl status suricata
```

The service was confirmed to be running successfully.

> **Screenshot:** Active Suricata service.

---

## 7. Alert Verification

Suricata alerts were monitored through the generated log files.

```bash
sudo tail -f /var/log/suricata/fast.log
```

Network activity was generated from systems within the lab environment to confirm that Suricata was inspecting traffic and producing alerts.

> **Screenshot:** Alerts generated in `fast.log`.

---

## 8. Implementation Validation

Basic network activity, including **ICMP traffic and Nmap scanning**, was used to verify the deployment.

Suricata successfully:

- Monitored traffic on the configured interface
- Processed the configured detection rules
- Identified matching network activity
- Generated alerts within the Suricata logs

More detailed detection exercises are documented separately under **Detection Testing**.

---

## Result

Suricata was successfully implemented as the **network intrusion detection component** of TheCoinSociety security environment.

The system was able to monitor network traffic, process detection rules and generate alerts for activity observed within the simulated enterprise network.
