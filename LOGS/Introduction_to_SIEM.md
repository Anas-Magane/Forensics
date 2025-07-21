
#  Security Information and Event Management (SIEM)

## 1. What is SIEM?

**SIEM** stands for **Security Information and Event Management**. It is a solution that:
- Collects logs and security events from all devices and systems in a network.
- Stores them in one central place.
- Analyzes and correlates them to detect threats.
- Provides alerts and dashboards for investigation and monitoring.

---

## 2. Network Visibility through SIEM

Before understanding the power of SIEM, we must first understand **why network visibility is important**.

###  Example Network Setup

A typical network may contain:
- Multiple Linux/Windows Endpoints
- One Data Server
- One Website
- Router for Internet Access

Each device in this network generates logs.

---

###  Types of Logs

#### 1) Host-Centric Logs: HCL
Logs generated from the machine itself.

Examples:
- File access by a user
- User login attempts
- Program execution
- Registry modification
- PowerShell script execution

Tools: **Sysmon**, **Windows Event Viewer**, **osquery**

#### 2) Network-Centric Logs: NCL
Logs generated when devices communicate with each other or the internet.

Examples:
- SSH connection
- FTP file transfer
- VPN activity
- HTTP/HTTPS web traffic
- Network file sharing

Protocols: **SSH**, **VPN**, **HTTP/s**, **FTP**, etc.

---

## 3. Why SIEM is Important

Each device produces hundreds of events per second. Without a central solution like SIEM, it's impossible to monitor everything.

SIEM allows you to:
- Ingest logs in real-time
- Detect abnormal activity
- Monitor 24/7
- Investigate past incidents
- Visualize insights
- Stay protected from threats

---

## 4. Log Sources and Ingestion Methods

###  Log Sources by Device Type

####  Windows:
Logs stored in **Event Viewer**, with unique IDs for each event.
Search: `Event Viewer` on Windows.

####  Linux:
Logs stored in `/var/log/` folder:

| Location | Description |
|----------|-------------|
| `/var/log/httpd` | Web requests/errors |
| `/var/log/cron` | Scheduled jobs |
| `/var/log/auth.log` or `/var/log/secure` | Authentication |
| `/var/log/kern` | Kernel logs |

**Sample cron log:**
```
May 28 13:04:20 crond[2843]: no timestamp found (user root job sys-hourly)
```

####  Web Servers (Apache):
Apache log examples:
```
192.168.21.200 - - [21/Mar/2022:10:17:10 -0300] "GET /cgi-bin/try/ HTTP/1.0" 200 3395
127.0.0.1 - - [21/Mar/2022:10:22:04 -0300] "GET / HTTP/1.0" 200 2216
```

---

###  How Logs Are Ingested into SIEM

1. **Agent / Forwarder:**
   Lightweight agents (like **Splunk Forwarder**) are installed on endpoints to collect and send logs.

2. **Syslog Protocol:**
   Used to collect real-time logs from systems (web servers, databases, etc.).

3. **Manual Upload:**
   Upload log files manually into SIEM (ex: Splunk or ELK).

4. **Port Forwarding:**
   Configure SIEM to listen on a port and receive logs directly from endpoints.

---

**Example: Splunk** supports all these methods of ingestion, offering flexibility in log analysis and visibility.

---


# Log Ingestion in SIEM (Explained in Simple English)

When we talk about **Log Ingestion** in SIEM (Security Information and Event Management), we are talking about the process of collecting logs from different sources and sending them to the SIEM system for monitoring and analysis.

These logs can help identify security threats, suspicious behavior, or system issues. Each SIEM platform has its own method to collect (ingest) these logs. Below are the common methods used:

## 1. Agent / Forwarder

Most SIEM systems provide a small software called **Agent** (also called **Forwarder** in Splunk).

- You install this agent on the endpoint (Windows, Linux, etc.).
- It captures important logs from the system (e.g. login attempts, process execution, file changes).
- Then it sends those logs in real-time to the SIEM server.

This is a reliable and real-time method.

## 2. Syslog

**Syslog** is a standard protocol used to send log messages between systems.

- Many devices (routers, firewalls, Linux servers, etc.) can send logs to a SIEM using Syslog.
- The SIEM listens on a specific port (usually UDP 514 or TCP 514) and collects logs from all the systems.

This is very useful for collecting logs from many different types of devices.

## 3. Manual Upload

Some SIEM tools (like **Splunk** or **ELK**) allow you to upload log files manually.

- This is useful when analyzing logs from a past incident.
- You can upload `.log`, `.json`, `.csv`, or other formats.
- The SIEM will process and normalize this data so it can be searched and analyzed.

## 4. Port Forwarding

In this method:

- You configure the endpoint device to send logs to a specific port on the SIEM server.
- The SIEM listens on that port and collects the incoming log data.

---

### Example: Splunk Log Ingestion

Splunk supports:

- Universal Forwarder (agent)
- Syslog ingestion
- Manual file upload
- HTTP Event Collector (HEC) to receive logs over HTTP/HTTPS

Each method is chosen based on the type of system, the log volume, and real-time needs.

---

**Summary Table**

| Method           | Description                                          | Real-time | Example Use Case                      |
|------------------|------------------------------------------------------|-----------|---------------------------------------|
| Agent / Forwarder | Installed on endpoint, sends logs to SIEM          | ✅        | Monitoring Windows or Linux machines |
| Syslog           | Sends logs using standard Syslog protocol            | ✅        | Routers, Firewalls, Linux logs       |
| Manual Upload    | User uploads log files manually                      | ❌        | Offline analysis of log files        |
| Port Forwarding  | Devices send logs directly to SIEM listening port   | ✅        | Custom devices or services           |


# Analyzing Logs and Alerts

## Log Analysis and Alerting in SIEM

SIEM tools collect all security-related logs through agents, port forwarding, etc. Once the logs are ingested, SIEM looks for suspicious behavior using predefined rules. If a rule condition is met, an alert is triggered, and the incident is investigated.

---

## Dashboards

Dashboards are critical in any SIEM. After data ingestion and normalization, dashboards present a summary of activities and alerts. These dashboards can be default or customized.

**Common Dashboard Information Includes:**
- Alert Highlights
- System Notifications
- Health Alerts
- Failed Login Attempts
- Events Count
- Triggered Rules
- Top Domains Visited

---

## Correlation Rules

Correlation rules detect threats in real-time. These rules are logical expressions that trigger alerts.

**Examples:**
- 5 failed login attempts in 10 seconds → Alert: Multiple Failed Logins
- Successful login after failed attempts → Alert: Suspicious Login
- USB inserted → Alert: Unauthorized USB Access
- Outbound traffic > 25 MB → Alert: Data Exfiltration Attempt

**Use-Case 1:** Event Log Clearing

- Event ID: 104 (Log Clearing)
- **Rule:** If `Log source = WinEventLog` AND `EventID = 104` → Alert: "Event Log Cleared"

**Use-Case 2:** Process Execution (e.g., `whoami`)

- Event ID: 4688
- **Rule:** If `Log source = WinEventLog` AND `EventID = 4688` AND `NewProcessName contains whoami` → Alert: "WHOAMI command detected"

**Note:** Correlation rules depend on normalized field-value pairs.

---

## Alert Investigation

Analysts review alerts via dashboards. When an alert is triggered, the related logs and rule conditions are reviewed. The alert is then classified as True Positive or False Positive.

**Post-Alert Actions:**
- **False Positive:** Tune rule to avoid recurrence.
- **True Positive:** Investigate further.
- Contact asset owner.
- Isolate infected host.
- Block suspicious IP.

---
