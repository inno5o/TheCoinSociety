# Wazuh SIEM Implementation

## Overview

Wazuh was deployed within the **TheCoinSociety** lab to provide centralised security monitoring for Windows and Linux endpoints.

The deployment used an **all-in-one Wazuh server**, with the Wazuh Manager, Indexer, and Dashboard running on a single Ubuntu Server. Wazuh agents were then deployed to endpoints within the internal network.

## Environment

| Component | Configuration |
|---|---|
| Lab Environment | GNS3 VM / VMware |
| Wazuh Server | Ubuntu Server |
| Server IP | `172.16.1.4` |
| Deployment | All-in-One |
| Wazuh Components | Manager, Indexer, Dashboard |
| Monitored Endpoints | Windows Server, Windows 10, Ubuntu Desktop |

> The Wazuh server was deployed within the same TheCoinSociety lab environment used by the other infrastructure and security projects.

---

## 1. Wazuh Server Deployment

The Ubuntu Server was updated and the required packages were installed before deploying Wazuh.

```bash
sudo apt update && sudo apt upgrade -y

sudo apt install curl apt-transport-https unzip wget libcap2-bin -y
```

The Wazuh installation assistant was then downloaded and executed using the all-in-one deployment option.

```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
chmod +x wazuh-install.sh

sudo ./wazuh-install.sh -a
```

This deployed the Wazuh components required for centralised monitoring.

**Evidence:**

> 📷 `screenshots/wazuh-installation.png`  
> Wazuh installation running on the Ubuntu Server.

---

## 2. Dashboard Access

After installation, the Wazuh Dashboard was accessed through the server's HTTPS interface.

```text
https://172.16.1.4
```

Successful dashboard access confirmed that the web interface was operational.

**Evidence:**

> 📷 `screenshots/wazuh-dashboard.png`  
> Wazuh Dashboard successfully accessed after deployment.

---

## 3. Endpoint Agent Deployment

Wazuh agents were deployed to systems within the internal network so that endpoint security events could be centrally monitored.

### Ubuntu Desktop

The Wazuh repository was configured on the Ubuntu endpoint and the agent was installed with the Wazuh Manager address set to `172.16.1.4`.

```bash
sudo WAZUH_MANAGER="172.16.1.4" apt install wazuh-agent -y

sudo systemctl daemon-reload
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```

### Windows Endpoints

The Wazuh Dashboard's **Deploy New Agent** function was used to generate the Windows deployment configuration.

The agent was installed through an Administrator PowerShell session and configured to communicate with the Wazuh Manager.

```powershell
WAZUH_MANAGER="172.16.1.4"
```

The Wazuh service was then started:

```powershell
NET START WazuhSvc
```

The same deployment process was used for the Windows Server endpoint.

**Evidence:**

> 📷 `screenshots/windows-agent-deployment.png`  
> Windows agent deployment and service startup.

---

## 4. Agent Verification

After deployment, the Wazuh Dashboard was used to verify connectivity between the Wazuh Manager and monitored endpoints.

The environment showed three active agents:

| Endpoint | Operating System | Status |
|---|---|---|
| Windows Server | Windows Server 2019 | Active |
| Windows Desktop | Windows 10 | Active |
| Ubuntu Desktop | Ubuntu 22.04 | Active |

**Evidence:**

> 📷 `screenshots/active-agents.png`  
> Wazuh Dashboard showing the deployed agents reporting as active.

---

## Result

Wazuh was successfully deployed as a centralised SIEM platform within the TheCoinSociety lab.

The Wazuh Manager, Indexer, and Dashboard were operational, and Windows and Linux endpoints were successfully enrolled and communicating with the server.

Further security monitoring and detection activities are documented separately from the core implementation.
