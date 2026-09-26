# Zabbix Implementation

## 1. Zabbix Server Deployment

Zabbix 7.4 was deployed on an Ubuntu Server within the TheCoinSociety network to provide centralised infrastructure monitoring.

**Server Details**

| Component | Configuration |
|---|---|
| Operating System | Ubuntu Server |
| Zabbix Version | 7.4 |
| Server IP | `172.16.1.4` |
| Database | MySQL |
| Web Interface | `http://172.16.1.4/zabbix` |

The Zabbix repository was configured and the required server, frontend and database components were installed.

### Verification

The Zabbix server service was checked to confirm that it was running successfully.

**Evidence:**  
*[Insert screenshot showing Zabbix server service status]*

---

## 2. Database Configuration

MySQL was configured as the backend database for Zabbix.

A dedicated Zabbix database and database user were created, after which the Zabbix database schema was imported.

The Zabbix server configuration was then updated with the required database credentials.

### Verification

Successful communication between Zabbix and the database was confirmed by starting the Zabbix server without database connection errors.

**Evidence:**  
*[Insert screenshot showing database configuration or successful Zabbix service]*

---

## 3. Zabbix Web Interface

The Zabbix frontend was accessed through:

`http://172.16.1.4/zabbix`

The initial setup was completed and the web dashboard was used as the central management interface for the monitoring environment.

### Verification

The dashboard loaded successfully and the Zabbix server appeared as an active monitored host.

**Evidence:**  
*[Insert screenshot of the Zabbix dashboard]*

---

## 4. Windows Host Monitoring

A Zabbix Agent was installed on the Windows 10 system to allow Zabbix to collect operating system and performance metrics.

The agent was configured with:

- Zabbix Server: `172.16.1.4`
- Hostname matching the host configured within Zabbix
- Zabbix Agent service enabled and running

The Windows host was then added to the Zabbix web interface and linked to the appropriate Windows monitoring template.

### Verification

Communication between the Windows agent and Zabbix server was confirmed through successful metric collection.

**Evidence:**  
*[Insert screenshot showing Windows host availability and collected data]*

---

## 5. Network Device Monitoring Using SNMP

SNMP monitoring was configured for TheCoinSociety network infrastructure.

The following devices were added to Zabbix:

- TCS-Router
- TCS-Switch

The devices were configured to communicate with the Zabbix server using **SNMPv2c**.

Appropriate SNMP templates were assigned within Zabbix to collect device and interface information.

### Verification

Successful SNMP communication was confirmed when Zabbix began receiving monitoring data from the router and switch.

**Evidence:**  
*[Insert screenshot showing TCS-Router and TCS-Switch monitored through SNMP]*

---

## 6. Host Monitoring Verification

After configuration, the monitored hosts were reviewed from the Zabbix interface to verify connectivity and data collection.

The environment provided centralised visibility of both endpoint systems and network infrastructure from a single monitoring platform.

**Evidence:**  
*[Insert final screenshot showing monitored hosts and their availability]*

---

## Implementation Result

Zabbix was successfully integrated into the TheCoinSociety lab as the centralised infrastructure monitoring platform.

The implementation demonstrated monitoring across different infrastructure types using:

- **Zabbix Agent** for endpoint and server monitoring
- **SNMP** for network device monitoring
- **Zabbix Web Interface** for centralised monitoring and management

This established the monitoring foundation required for further practical work involving triggers, alerting, dashboards, service monitoring and simulated infrastructure failures.
