# Logs Fundamentals (Simple English)

## 1. What Are Logs

Logs are like digital footprints. When something happens on a computer (normal or bad), it leaves a trace. These traces are saved in files called logs.

Example  
Just like police look at footprints and broken doors to find a thief, cybersecurity teams look at logs to find hackers or errors.

---

## 2. Why Are Logs Important

Logs help us with many things

 Use Case  Explanation 
-----------------------
 Security Monitoring  Logs show if something strange is happening (a possible attack). 
 Incident Investigation  Logs show what happened and when during an attack. 
 Troubleshooting  Logs help fix system or app problems. 
 Performance  Logs tell us if systemsapps are running well. 
 Auditing  Logs help prove rules and security are followed. 

---

## 3. Types of Logs

There are many logs. Each type shows different info.

 Log Type  What It Shows  Example 
-----------------------------------
 System Logs  Operating system actions  Startup, shutdown, errors 
 Security Logs  Security actions  Logins, password changes 
 Application Logs  What apps do  Errors, updates 
 Audit Logs  User actions  File access, setting changes 
 Network Logs  Network traffic  Connections, firewall activity 
 Access Logs  Who accessed what  Website or database access 

---

## 4. What Is Log Analysis

Log analysis means reading logs to find useful or strange info.

- Manually Search by hand.
- Automatically Use tools like SIEM, ELK, or Splunk to find alerts.

---
# Windows Event Logs Analysis 

Windows keeps a record of many activities in special files called "logs". Each log file has a purpose:

### Types of Windows Logs

- **Application Logs**: These store info from apps. They include errors, warnings, and issues.
- **System Logs**: These show system activities like startup, shutdown, driver problems, and hardware issues.
- **Security Logs**: Very important for security. They show user logins, logouts, password changes, and more.

---

### Event Viewer

Windows has a built-in tool to check these logs. It's called **Event Viewer**.

#### How to open it:
1. Click the **Start** button.
2. Type **Event Viewer**.
3. Open it.

You will see:
- A list of log types (Application, System, Security, etc.).
- Each log contains many events.
- You can search and filter events.

---

### Important Fields in a Log

- **Description**: What happened.
- **Log Name**: Type of log.
- **Logged**: Date and time.
- **Event ID**: A unique number that shows what kind of activity happened.

---

### Common Event IDs

| Event ID | What It Means                             |
|----------|-------------------------------------------|
| 4624     | User logged in (successful login)         |
| 4625     | User login failed                         |
| 4634     | User logged off                           |
| 4720     | New user account created                  |
| 4724     | Tried to reset a password                 |
| 4722     | User account enabled                      |
| 4725     | User account disabled                     |
| 4726     | User account deleted                      |

---

### Filtering Logs by Event ID

To search for a specific activity:
1. In Event Viewer, click **"Filter Current Log"**.
2. Enter the Event ID (e.g., 4624 for login).
3. Click **OK**.
4. You will now see only the logs matching that ID.

You can double-click any log to see more details.

# Web Server Access Logs 

Web servers keep a log of every request made to a website, like visiting pages or submitting forms. These logs include key details: the user's IP address, time of request, type of HTTP method (e.g. GET), requested URL, status code (e.g. 200 for success), and browser details (User-Agent).

These logs are stored in files like /var/log/apache2/access.log. You can analyze them manually using Linux commands:

cat: shows the full content of the log file.
grep: searches for specific patterns (e.g. an IP address).
less: views the file page by page and lets you search inside.

Analyzing these logs helps in understanding website usage and detecting suspicious activity.
## 5. Summary

- Logs are traces of what happens on computers.
- They help with security, fixing problems, and more.
- There are many types of logs.
- Logs must be analyzed to understand incidents.
