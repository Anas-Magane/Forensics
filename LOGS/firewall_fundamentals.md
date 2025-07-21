# What Is the Purpose of a Firewall

Imagine a security guard at the entrance of a mall or bank. His job is to check who is entering and leaving, making sure no one gets in without permission.  
A **firewall** works the same way for your computer or network. It is like a digital security guard.

Every day, your device sends and receives a lot of data through the Internet. A firewall checks all that traffic. Based on the **rules** you give it, the firewall allows or blocks the traffic.

- If traffic is safe or known → it is **allowed**.
- If it is unknown or dangerous → it is **blocked**.

Modern firewalls do more than just blocking or allowing. They help detect threats, protect systems, and provide better control.

###  Learning Objectives:
- Understand the **types of firewalls**
- Learn about **firewall rules** and their parts
- Practice with **Windows built-in firewall**
- Practice with **Linux built-in firewall**

# Types of Firewalls

Organizations use firewalls to protect their systems by filtering harmful traffic. There are several types of firewalls, each working on different OSI layers. Below are the most common types:

---
## Arabic mode
 1. Stateless Firewall – جدار ناري بدون ذاكرة
 كيفاش خدام؟

تخيل عندك حارس أمن فباب الشركة، وكل مرة كيجي شي واحد، الحارس كيسولو: "عندك ترخيص؟"، ولكن ما كيحتافظش فذاكرتو شكون دخل قبل ولا لا. كل واحد جديد كيتعامل معاه بوحدو، بلا ما يربطو باللي قبل.

🔧 مثال:
واحد دخل البارح وكان فيه مشكل، و جا اليوم، الحارس غادي يعاود يفحصو من جديد، وما غاديش يعرف أنه نفس الشخص فيه مشكل البارح.

 المميزات:

خفيف وسريع بزاف
مزيان فالشبكات اللي فيها بزاف ديال الترافيك

 العيوب:

ما كيعرفش واش هاد packet تابع لاتصال آمن ولا لا
ما كيديرش مراقبة معقدة

🔹 2. Stateful Firewall – جدار ناري عندو ذاكرة
 كيفاش خدام؟

نفس الحارس، ولكن دابا عندو دفتر صغير كيسجل فيه شكون دخل وشحال بقا. إذا جا نفس الشخص ثاني مرة، كيعرفو وممكن يدخلو بلا ما يعاود يسولو.

🔧 مثال:
عندك اتصال بين جهاز ديالك وسيرفر، الحيط كيسجل أن هاد الاتصال قانوني، وكل packet تابع له كيتسمح ليه يدوز بسهولة.

 المميزات:

كيعرف يتعامل مع الاتصالات المستمرة
كيعطي حماية أكثر

 العيوب:

شوية ثقيل من حيث الأداء
كيسحتاج RAM و CPU أكثر

🔹 3. Proxy Firewall – جدار ناري عبر وسيط
 كيفاش خدام؟

تخيل ماشي الحارس كيدخل الناس، ولكن عندو وسيط كيدخل فبلاصتهم، كيسول شنو بغاو، ويدير المهمة، ويرجع ليهم النتيجة. هاد الحارس ما كيعمر حتى واحد يدخل مباشرة.

🔧 مثال:
أنت فشركة، وكتطلب صفحة من Google. الحيط كياخد الطلب ديالك، كيمشي لGoogle، يجيب الصفحة، و يرجعها ليك، بلا ما Google يعرف شكون طلبها.

 المميزات:

كيخبي IP ديالك (أنونيم)
كيراقب المحتوى داخل packet
كيسمح بـ Content Filtering (مثلاً حظر مواقع إباحية)

 العيوب:

كيبطئ الأداء شوية
خاص إعدادات معقدة

🔹 4. Next-Generation Firewall (NGFW) – الجيل الجديد
 كيفاش خدام؟

تخيل عندك حارس ذكي بزاف، كيعرف يحلل الوجه، الصوت، التصرفات، وحتى النوايا. ماشي غير كيسولك شكون نتي، ولكن كيشوف واش نيت نتي باغي تدير شي حاجة خايبة، ويوقفك فبلاصتك.

🔧 مثال:
كتحاول تدير هجوم من نوع XSS ولا Brute Force، هاد الجدار الذكي كيعرف داك النمط، وكيوقفك قبل ما توصل.

 المميزات:

عندو IDS/IPS داخلي (يوقف الهجمات)
كيعرف يحلل الترافيك حتى فـ SSL/TLS (يفك التشفير)
فيه ذكاء اصطناعي (heuristic analysis)

 العيوب:
غالي بزاف
خاصو سيرفرات قوية
## English mode : 
### 🔹 Stateless Firewall
- Works on **Layer 3 and 4**
- Matches each packet to rules without checking past connections
- **Does not track** connections
- **Fast**, but can't apply advanced logic
- Example: Blocks some packets but still checks new ones from the same source again

---

### 🔹 Stateful Firewall
- Also works on **Layer 3 and 4**
- **Tracks connection states** using a state table
- If a connection is accepted, future packets are allowed automatically
- More secure than stateless
- Can block traffic from sources with rejected past connections

---

### 🔹 Proxy Firewall
- Works on **Layer 7**
- Acts as a **middleman** between network and internet
- Inspects packet content
- Can hide internal IPs
- Supports **content filtering**

---

### 🔹 Next-Generation Firewall (NGFW)
- Works on **Layer 3 to 7**
- Supports **deep packet inspection**
- Has **intrusion prevention system (IPS)**
- Uses **heuristic analysis** to detect new attack patterns
- Can **decrypt SSL/TLS** traffic

---

### 🔒 Comparison Table

| Firewall Type           | Features                                                                 |
|-------------------------|--------------------------------------------------------------------------|
| Stateless Firewall      | Basic filtering, no connection tracking, fast for high-speed networks    |
| Stateful Firewall       | Tracks sessions, applies complex rules, monitors traffic patterns        |
| Proxy Firewall          | Content inspection, app control, hides IPs, supports SSL/TLS filtering   |
| Next-Gen Firewall (NGFW)| Advanced protection, IPS, AI-based detection, SSL/TLS decryption         |


#  Firewall Rules Summary

A firewall rule consists of:

- **Source Address**: Where the traffic originates
- **Destination Address**: Where the traffic is going
- **Protocol**: TCP, UDP, etc.
- **Port**: Specific service port (22 for SSH, 80 for HTTP, etc.)
- **Action**: What to do with matching traffic
- **Direction**: Inbound, Outbound, Forward

##  Actions

###  Allow
> Permit the traffic.

Example: Allow all outbound HTTP traffic on port 80

```text
Action: Allow
Source: 192.168.1.0/24
Destination: Any
Protocol: TCP
Port: 80
Direction: Outbound
```
 Deny
Block the traffic.
Example: Block inbound SSH traffic on port 22
Block the traffic.
Example: Block inbound SSH traffic on port 22

```bash
Action: Deny
Source: Any
Destination: 192.168.1.0/24
Protocol: TCP
Port: 22
Direction: Inbound
```
🔁 Forward
Redirect traffic to another host.
Example: Forward incoming HTTP traffic to internal web server 192.168.1.8

```bash
Action: Forward
Source: Any
Destination: 192.168.1.8
Protocol: TCP
Port: 80
Direction: Inbound
```
🔄 Directions
Inbound: Rules for incoming traffic
Outbound: Rules for outgoing traffic
Forward: Rules to redirect traffic inside the network

# Exemple :   🛡 Windows Defender Firewall Guide

Windows Defender Firewall is a built-in firewall in Windows OS. It allows control over incoming and outgoing traffic using custom rules.

---

## Network Profiles

- **Private Networks**: For trusted networks like home
- **Public Networks**: For untrusted networks (coffee shops, airports)

Each profile can have different firewall settings.

---

##  App Control

```bash
You can allow or disallow specific applications for each network profile via:
`Control Panel > Windows Defender Firewall > Allow an app or feature...`
```
---

## ⚙️ Creating Custom Rules

To create a custom rule:

1. Open **Windows Defender Firewall with Advanced Security**
2. Choose **Outbound Rules**
3. Click **New Rule**

### 🚫 Example: Block HTTP/HTTPS Traffic

| Step | Option |
|------|--------|
| Rule Type | Custom |
| Program | All Programs |
| Protocol | TCP |
| Remote Ports | 80,443 |
| Action | Block the connection |
| Profile | All (Domain, Private, Public) |
| Name | Block_HTTP_HTTPS |

After creating the rule, browsing to `http://10.10.10.10/` should fail.

---

# Exemple 2 : Linux Firewall – Netfilter & UFW

Linux uses **Netfilter** as its core firewall system. Tools like `iptables`, `nftables`, `firewalld`, and `ufw` are used to control network traffic using Netfilter.

---

## ⚙️ UFW (Uncomplicated Firewall)

A user-friendly command-line interface to manage firewall rules easily.

---

###  Check UFW Status

```bash
sudo ufw status
```
🔛 Enable the Firewall
```bash
sudo ufw enable
```
❌ Disable the Firewall
```bash
sudo ufw disable
```
📤 Allow All Outgoing Traffic
```bash
sudo ufw default allow outgoing
```
📥 Deny Incoming SSH Traffic
```bash
sudo ufw deny 22/tcp
```
📋 List All Rules (Numbered)
```bash
sudo ufw status numbered
```
🗑 Delete a Rule by Number
```bash
sudo ufw delete <rule_number>
```
Example:

```bash
sudo ufw delete 2
```