# Suricata Detection Testing

## Overview

After implementing Suricata within **TheCoinSociety** network, detection testing was performed to verify that the IDS could identify network activity and generate alerts.

Testing was conducted from systems within the GNS3 lab environment against hosts monitored by Suricata.

---

## 1. ICMP Traffic Detection

ICMP traffic was generated using `ping` to confirm that Suricata could observe traffic passing through the monitored network.

```bash
ping <target-ip>
```

Suricata logs were monitored during the test:

```bash
sudo tail -f /var/log/suricata/fast.log
```

The traffic was successfully observed and corresponding alerts were generated where applicable detection rules were configured.

> **Screenshot:** ICMP test and corresponding Suricata output.

---

## 2. Nmap Scan Detection

An Nmap scan was performed against a system within the monitored network.

```bash
nmap <target-ip>
```

The purpose of the test was to generate reconnaissance traffic and verify whether Suricata could identify scanning activity.

Suricata generated alerts associated with the network activity, confirming that the IDS was actively inspecting traffic.

> **Screenshot:** Nmap scan from the testing machine.

> **Screenshot:** Corresponding Suricata alert.

---

## 3. Alert Analysis

Generated alerts were reviewed through:

```text
/var/log/suricata/fast.log
```

The alerts provided information including:

- Detection timestamp
- Rule/signature triggered
- Source IP address
- Destination IP address
- Network protocol
- Source and destination ports where applicable

This confirmed that Suricata was not only receiving network traffic but also processing it against the configured detection rules.

---

## Result

The detection tests confirmed that the Suricata deployment was operational within TheCoinSociety network.

Suricata successfully monitored network traffic and generated alerts from test activity, demonstrating basic **network intrusion detection and security monitoring capability**.
