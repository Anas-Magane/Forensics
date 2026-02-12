
# 🧪 CAPA - Tool Overview & Usage Guide

## 📌 What is CAPA?

**CAPA** (Common Analysis Platform for Artifacts) is a static analysis tool designed to identify potential behaviors and capabilities in executable files.  
Developed by Mandiant (FireEye), it allows analysts and defenders to extract high-level functionality from suspicious binaries **without executing them**, making it ideal for safe and efficient malware triage.

---

## ⚙️ Why Use CAPA?

- CAPA helps analysts determine what a binary is capable of doing.
- It's widely used in **malware analysis**, **incident response**, and **threat hunting**.
- It provides **behavioral insights** without requiring full reverse engineering skills.
- The results are mapped to well-known frameworks like **MITRE ATT&CK** and **MBC (Malware Behavior Catalog)**.

---

## 🛠️ How to Use CAPA (Step-by-Step)

### Step 1: Open PowerShell
Start a PowerShell terminal. It might take a few seconds for the prompt to appear.

### Step 2: Navigate to the Directory
Make sure you're in the correct directory where CAPA is located:

```powershell
cd C:\Users\Administrator\Desktop\capa
```

### Step 3: Run CAPA on a File
To analyze a binary (example: `cryptbot.bin`):

```powershell
capa.exe .\cryptbot.bin
```

---

## 🔍 Common CAPA Parameters

| Option | Description                                 | Example                            |
|--------|---------------------------------------------|------------------------------------|
| `-h`   | Show help message                           | `capa -h`                          |
| `-v`   | Verbose output (more detail)                | `capa.exe .\file.bin -v`          |
| `-vv`  | Very verbose output (extensive details)     | `capa.exe .\file.bin -vv`         |

---

## 📊 Example Output Overview

CAPA results typically include:

- **Hashes**: MD5, SHA1, SHA256
- **Metadata**: OS type, architecture, file format
- **MITRE ATT&CK Tactics & Techniques**: Mapped behaviors
- **MBC Behaviors**: Anti-analysis, communication, file interaction, etc.
- **Capabilities**: Specific actions detected (e.g., PowerShell execution, file creation)

Example command:
```powershell
capa.exe .\cryptbot.bin
```

---

## 📁 View Pre-Processed Results

If a processed result file exists (e.g., `cryptbot.txt`):

```powershell
Get-Content .\cryptbot.txt
```

This displays the same output that CAPA generates in the terminal.


---
**Exempe Results of CAPA look at the file cryptobot-1726590367927.txt**

## 🧠 Final Notes

- CAPA is an essential tool for anyone working in **defensive security**.
- It provides immediate insights into malware functionality.
- Perfect for automating the first steps in a malware triage workflow.
- Results should be interpreted by someone with knowledge of **TTPs** and frameworks like **MITRE ATT&CK**.

Feel free to contribute to this guide or improve it for other analysts and blue teamers!


# ***Version Arabe***
# 📌 مقدمة حول CAPA: الأساسيات

---

##  شنو هو المشكل فـ تحليل البرامج الخبيثة؟
واحد من أكبر التحديات اللي كيواجهو الباحثين في الأمن السيبراني هو:

> **كيفاش نحلل واحد البرنامج ممكن يكون خبيث، بلا ما نخاطر بالجهاز ديالنا؟**

🎯 الجواب كاين فـ طريقتين:

- **التحليل الديناميكي (Dynamic Analysis):**  
نشغلو البرنامج فـ بيئة مراقبة ونشوفو السلوك ديالو.

- **التحليل الثابت (Static Analysis):**  
نفحصو الكود ديالو، البنية ديال الملف، والأوامر لي فيه بلا ما نشغلوه.

---

## 🧠 شنو هو CAPA؟

**CAPA** هو أداة متطورة من تطوير فريق **Mandiant** التابع لشركة **FireEye**.  
الاسم ديالها اختصار لـ:

> **Common Analysis Platform for Artifacts**

✨ **الهدف ديالها:**

كتحلل البرامج التنفيذية (Executables) بحال:

- ملفات **PE** (Windows)  
- **ELF binaries** (Linux)  
- **.NET modules**  
- **Shellcode**  
- **تقارير Sandbox**

🎯 **CAPA كتقلب فـ هاد الملفات وتطبق عليهم قواعد (Rules)**  
باش تعرف شنو ممكن يدير هاد البرنامج.

---

## 🛠️ شنو تقدر CAPA تكتاشف؟

مثلاً، تقدر تكتاشف واش البرنامج فيه:

- 📡 تواصل مع الشبكة  
- 📁 تعديل أو إنشاء ملفات  
- 🧬 حقن العمليات (Process Injection)  
- 🕵️‍♂️ مراقبة الأنشطة  
- 🔐 تقنيات الإخفاء (Obfuscation)

وماشي غير هادشي، بل كتغطّي **العشرات من القدرات الخطيرة**.

---

## 💎 القوة ديال CAPA؟

CAPA فيها خلاصة **سنين من الخبرة فالهندسة العكسية**، وكلها مدخولة فـ أداة أوتوماتيكية:

-  ماشي ضروري تكون خبير فـ Assembly  
-  ماشي خاصك تكون محترف فـ Reverse Engineering  
-  فقط تستعمل CAPA وتعطيك **خلاصة مفهومة** على البرنامج

---

## 🎯 فوقاش تنفعني CAPA؟

- 🔬 تحليل المالوير (Malware Analysis)  
- 🔎 البحث عن التهديدات (Threat Hunting)  
- 🚨 الاستجابة للحوادث (Incident Response)  
- 🛡️ الدفاع الاستباقي فالشبكات

---
---

# 🧠 MITRE ATT&CK Framework

## 📚 التعريف

**MITRE ATT&CK** هو إطار عمل منظم طوراتو منظمة MITRE،  
ATT&CK = **Adversarial Tactics, Techniques & Common Knowledge**  
بالعربية: **التكتيكات، التقنيات، والمعرفة المشتركة للهجمات العدائية**

---

## 🎯 الهدف منو

- فهم كيفاش كيتصرفو المهاجمين (Attackers)
- تنظيم وتحليل مراحل الهجوم
- تحسين الدفاعات السيبرانية
- استعمالو فـ Threat Hunting و Incident Response

---

## 🧱 البنية ديالو

| العنصر      | المعنى                                                 |
|-------------|---------------------------------------------------------|
| **Tactic**  | الهدف ديال المهاجم فـ مرحلة معينة (مثلاً: Execution)   |
| **Technique** | الطريقة باش كيحقق الهدف (مثلاً: PowerShell Execution) |
| **Procedure** | تطبيق حقيقي من طرف مجموعة (مثلاً: APT29 تستعمل Mimikatz) |

---

## 🔁 التسلسل الهجومي (Kill Chain) حسب MITRE

| المرحلة           | التكتيك              | التقنية                                 |
|--------------------|----------------------|------------------------------------------|
| الدخول الأولي      | Initial Access        | Spearphishing Attachment                 |
| التنفيذ            | Execution             | PowerShell                               |
| التصعيد الصلاحي    | Privilege Escalation | Exploitation for Privilege Escalation   |
| التنقل الجانبي     | Lateral Movement      | Remote Desktop Protocol                  |
| جمع البيانات       | Collection            | Screen Capture                           |
| إخراج البيانات     | Exfiltration          | Data Transfer to Cloud Storage           |

---

## 🛠️ المجالات اللي كنستعملو فيه MITRE

- تهديدات متقدمة (APT Tracking)
- تحليل البرمجيات الخبيثة
- بناء SOC واختبار فعاليته
- تدريب وتحسين فرق Blue Team و Red Team

---

## 🌐 الموارد

الموقع الرسمي:  
🔗 https://attack.mitre.org

كاين فيه:
- Matrix منظمة
- Techniques و Sub-techniques
- Tools و Software
- مجموعات APT (بحال APT28, APT29…)

---