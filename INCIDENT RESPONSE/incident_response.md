# Incident Response Fundamentals

## 1. What are Incidents?

Computers and mobile devices run both interactive (e.g., games, videos) and background (non-interactive) processes. These processes generate many events logged by the system. Security tools collect these logs to identify harmful activity. When a suspicious pattern is found, it generates an **alert**.

### Types of Alerts:
- **False Positive**: Looks dangerous but isn’t.  
  *Example*: A data transfer alert turns out to be a regular backup to cloud storage.
- **True Positive**: Alert that indicates real danger.  
  *Example*: A phishing email designed to hack into the system.

True positives often turn into **incidents**. Incidents are prioritized by **severity**:
- Low
- Medium
- High
- Critical

---

## 2. Types of Incidents

### ✅ Malware Infections
- Malicious programs (text files, executables, documents) that harm systems.
- Most common type of incident.

### ✅ Security Breaches
- Unauthorized access to sensitive data.
- Major threat to businesses.

### ✅ Data Leaks
- Exposure of confidential info to unauthorized people.
- Can be intentional (attack) or unintentional (misconfig).

### ✅ Insider Attacks
- Attacks from employees or internal staff.
- Example: Staff installs malware via USB before leaving job.

### ✅ Denial of Service (DoS)
- Flooding a system with fake requests to make it unavailable.
- Affects service availability.

---

## 3. Incident Response Process

### SANS Framework (PICERL)

| Phase         | Description                                                                 | Example |
|---------------|-----------------------------------------------------------------------------|---------|
| Preparation   | Prepare tools, teams, training, and plans.                                  | Employee phishing training |
| Identification| Detect unusual activity using security tools.                               | High data transfer analyzed as compromise |
| Containment   | Limit the attack spread.                                                    | Isolate affected host |
| Eradication   | Remove threat from environment.                                              | Run malware scan |
| Recovery      | Restore systems and confirm clean state.                                    | Restore data from backup |
| Lessons Learned| Analyze incident and improve response.                                      | Post-incident meeting |

### NIST Framework
Has similar phases but summarized in 4 steps:
1. Preparation
2. Detection and Analysis
3. Containment, Eradication, and Recovery
4. Post-Incident Activity

### 📄 Incident Response Plan
A formal document that includes:
- Roles and responsibilities
- Methodology
- Communication plan
- Escalation paths

---

## 4. Incident Response Techniques

### Tools Used:
- **SIEM**: Collects logs and detects incidents.
- **Antivirus (AV)**: Detects known threats.
- **EDR**: Protects systems from advanced threats and can contain/eradicate them.

### 📘 Playbooks
Standard response guidelines for incidents.

#### Example: Phishing Email Playbook
1. Notify stakeholders
2. Analyze email header and body
3. Analyze any attachments
4. Check if attachments were opened
5. Isolate infected systems
6. Block the sender

### 🛠️ Runbooks
Detailed technical instructions for handling specific incident types.

