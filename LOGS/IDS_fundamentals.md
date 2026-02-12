# IDS Fundamentals

## Etape 1: What Is an IDS

In the previous task "Intro to Firewalls," we saw the role of the firewall, which usually sits at the edge of the network and protects incoming and outgoing traffic. The firewall checks the traffic when a connection wants to go through and blocks it if it violates the rules.

But what if the traffic passes through the firewall and performs some bad actions inside the network? This is where the IDS comes in.

IDS (Intrusion Detection System) is a security solution inside the network that monitors traffic and detects any suspicious activity. Think of it like security cameras in a building: the firewall is like the guard at the door, and the IDS is like the cameras that watch for strange activity inside.

IDS works by using signatures (Signature-based) or detecting unusual patterns (Anomaly-based). When it sees something suspicious, it sends an alert to the security team.

> 🔒 The IDS only watches. It doesn't block traffic — it just gives alerts.

## Etape 2: Types of IDS

### 📍 Based on Deployment Mode

* **HIDS (Host-based IDS)**: Installed on a single machine and only watches that machine.

  * ✅ Gives detailed info.
  * ❌ Hard to manage in big networks.

* **NIDS (Network-based IDS)**: Watches all traffic in the network.

  * ✅ Protects the whole network.
  * ❌ Doesn't give deep details like HIDS.

### 🧠 Based on Detection Method

* **Signature-Based IDS**:

  * Uses known attack patterns (signatures).
  * ✅ Very accurate for known attacks.
  * ❌ Can't detect new (zero-day) attacks.

* **Anomaly-Based IDS**:

  * Learns the normal behavior of the network and looks for strange changes.
  * ✅ Can detect new attacks.
  * ❌ May give false alarms (false positives).

* **Hybrid IDS**:

  * Uses both Signature and Anomaly methods.
  * ✅ Best of both: finds known and new attacks.

> 📌 IDS is like the third eye of your network. Not a wall, but a silent watcher that says: "You're under attack!"

# 📦 Snort IDS - Simple Explanation (Darija + English)

Snort is an open-source **Intrusion Detection System (IDS)** used to monitor and analyze network traffic. Below is a simple explanation of how Snort works and its different modes.

---

## 🧠 What is Snort?

**Snort** is a free tool created in 1998 that helps detect **attacks** and **suspicious traffic** in real-time.

### 🛠️ Detection Types:
- **Signature-based**: Detects known attacks using predefined patterns (like antivirus).
- **Anomaly-based**: Detects abnormal behavior that doesn’t match usual traffic.

📁 Snort uses **rules files** to define attacks. You can:
- Use built-in rules.
- Create your own custom rules.
- Disable unnecessary rules.

---

## ⚙️ Snort Modes

Snort has 3 main modes. Each mode is used for a different purpose.

| Mode | Description | Use Case |
|------|-------------|----------|
| **Sniffer Mode** | Just views traffic (no analysis). Like Wireshark. | Useful for debugging or checking traffic flow. |
| **Logging Mode** | Records all traffic in a PCAP file. | Used for forensic analysis after an attack. |
| **NIDS Mode** | Main detection mode. Monitors traffic & gives alerts. | Used to detect real-time attacks. |

---

## 🔍 Mode Details with Examples

### 1️⃣ Sniffer Mode

> **Command Example:**  
```bash
snort -v
```

👀 **What it does:**  
- Displays all traffic on the console.
- Does **not** analyze or alert.
- Good for network troubleshooting.

🧪 **Example Use Case:**  
- Your network is slow? Use this mode to check what's going on.

---

### 2️⃣ Packet Logging Mode

> **Command Example:**  
```bash
snort -dev -l ./log -h 192.168.1.0/24
```

📝 **What it does:**  
- Saves all packets in PCAP files.
- You can analyze them later with Wireshark.

🧪 **Example Use Case:**  
- A cyber attack happened? Use this mode to collect logs for investigation.

---

### 3️⃣ NIDS Mode (Intrusion Detection)

> **Command Example:**  
```bash
snort -A console -q -c /etc/snort/snort.conf -i eth0
```

🚨 **What it does:**  
- Detects known attacks based on rules.
- Sends real-time alerts.

🧪 **Example Use Case:**  
- You want to monitor a live network and be alerted of any threats.

---

## 📌 Summary 

| Mode     | What it Does                            | When to Use It                             |
|----------|------------------------------------------|---------------------------------------------|
| Sniffer  | Shows the traffic without analyzing it   | When you want to observe the network flow   |
| Logging  | Saves the traffic into log files         | When an attack happened and you need logs   |
| NIDS     | Detects known attacks in real time       | When you want to protect your network live  |

---

##  Tips
- Always update your rules.
- Start with NIDS mode for protection.
- Use logging mode when investigating.

---
