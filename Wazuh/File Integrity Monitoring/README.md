# File Integrity Monitoring

## Overview

File Integrity Monitoring (FIM) was configured on Wazuh agents to monitor selected directories for file changes.

The test focused on detecting **file creation and modification activity** on monitored Windows and Linux endpoints and confirming that the activity was reported to the Wazuh Dashboard.

---

## 1. FIM Configuration

The Wazuh agent configuration file was modified on the monitored endpoints.

### Linux

The agent configuration was opened using:

```bash
sudo nano /var/ossec/etc/ossec.conf
```

The user's **Documents** directory was selected for monitoring.

For testing purposes, the FIM scan frequency was reduced from the default `43200` seconds to `5` seconds to allow changes to be detected quickly.

```xml
<syscheck>
    <disabled>no</disabled>
    <frequency>5</frequency>
    <directories>/home/inno/Documents</directories>
</syscheck>
```

**Evidence:**

> 📷 `screenshots/linux-fim-configuration.png`  
> Wazuh agent configuration being modified on the Ubuntu endpoint.

### Windows

The Wazuh agent configuration file was also opened on the Windows endpoint and the user's Documents directory was configured for monitoring.

**Evidence:**

> 📷 `screenshots/windows-fim-configuration.png`  
> Wazuh FIM configuration on the Windows endpoint.

---

## 2. File Creation Test

A new file was created inside the monitored **Documents** directory on the Windows Server.

This provided a controlled change to verify whether Wazuh would detect activity within the monitored location.

**Evidence:**

> 📷 `screenshots/windows-file-creation.png`  
> Test file being created inside the monitored directory.

---

## 3. Detection

After the file was created, the Wazuh Dashboard was checked for File Integrity Monitoring events.

Wazuh generated an event for the newly created file, confirming that changes within the monitored directory were being detected and reported.

**Evidence:**

> 📷 `screenshots/fim-file-created-alert.png`  
> Wazuh File Integrity Monitoring event showing the detected file creation.

---

## 4. File Modification Test

The monitored file was modified to generate an additional integrity change.

The resulting activity was reviewed from the Wazuh Dashboard to confirm that changes to existing files were also being monitored.

**Evidence:**

> 📷 `screenshots/fim-file-modification.png`  
> File modification and corresponding FIM activity.

---

## Result

Wazuh File Integrity Monitoring was successfully configured and tested on monitored endpoints.

Changes made within the selected directories generated FIM events in Wazuh, demonstrating the ability to monitor endpoint files for unauthorized or unexpected changes.
