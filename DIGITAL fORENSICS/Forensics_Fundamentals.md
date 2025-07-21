
## Introduction
Digital forensics is about investigating cyber crimes using methods and tools to find evidence.  

Cyber crime includes any illegal activity using digital devices.  

Example: Police find a suspect’s laptop, phone, hard drive, and USB. Forensics teams analyze them to find maps, plans, chats, photos used for crimes.

---

## Learning Objectives
- Phases of digital forensics
- Types of digital forensics
- Evidence acquisition
- Windows forensics
- Solving a case

---

## Digital Forensics Methodology
NIST defines 4 main phases:

1. **Collection**  
   - Identify and gather devices without changing data.  
   - Examples: PC, laptop, USB, camera.

2. **Examination**  
   - Filter and extract needed data.  
   - Example: Only specific dates or users.

3. **Analysis**  
   - Correlate data, find timeline, link evidence.

4. **Reporting**  
   - Create detailed report with methods, findings, recommendations.  
   - Include executive summary.

---

## Types of Digital Forensics
- **Computer forensics:** Investigating computers.  
- **Mobile forensics:** Extracting data from phones.  
- **Network forensics:** Analyzing network traffic logs.  
- **Database forensics:** Investigating database breaches.  
- **Cloud forensics:** Investigating data in cloud services.  
- **Email forensics:** Analyzing emails for fraud or phishing.

---

## Evidence Acquisition
Key practices:

- **Proper Authorization**  
  - Always get legal approval before collecting data.

- **Chain of Custody**  
  - Track who collected, accessed, stored evidence.  
  - Ensures integrity for court.

- **Use of Write Blockers**  
  - Prevent changes to data during collection.  
  - Keeps evidence in original state.

---

## Windows Forensics
Common in cases because many use Windows systems.

**Forensic Images:**  
- **Disk Image**  
  - Full copy of storage (files, history).  
  - Non-volatile (stays after restart).  
- **Memory Image**  
  - Copy of RAM data (open files, processes).  
  - Volatile (lost after shutdown).  
  - Priority to capture before power off.

---

## Tools
- **FTK Imager:**  
  - Create and view disk images.  
  - Easy GUI, multiple formats.  

- **Autopsy:**  
  - Analyze disk images.  
  - Search, recover deleted files, metadata analysis.

- **DumpIt:**  
  - Create memory images via command-line.  

- **Volatility:**  
  - Analyze memory images.  
  - Supports multiple OS.  
  - Plugins for detailed artifact analysis.

---
# Digital Forensics Methodology 
The National Institute of Standards and Technology (NIST) says that every digital forensics case should follow 4 steps:

1. 🧩 Collection
This is the first step. The goal is to find and collect any digital evidence without changing it.

**What the team does:**
Look for devices at the crime scene.
Carefully take them without damaging or changing the data.

📦 Examples of devices:
Laptops
USB drives
Mobile phones
Cameras
Hard drives

🧠 Example:
If a hacker attacked a company, the forensic team might collect:
The hacker’s laptop
Server logs
A USB drive found at the desk

2. 🔍 Examination
This step is about filtering the data and keeping only what’s important for the case.

**What the team does:**
Remove useless files.
Keep only the important data (like files from a certain date or user).

🧠 Example:
Imagine there are 10,000 pictures on a camera.
The crime happened on March 5th, so the team will keep only the pictures taken on March 5th, and ignore the rest.

3. 🧠 Analysis
This is the most important step. The team now studies the data to find out what really happened.

**What the team does:**
Combine data from different sources.
Look for links between files, messages, locations, or people.
Create a timeline of the events.

🧠 Example:
If they find:
A chat where the suspect says “Let’s meet at 8 PM.”
A GPS location showing movement at 7:45 PM.
A video at 8 PM showing the suspect at the location.
They now know when, where, and how the suspect acted.

4. 📝 Reporting
This is the final step. The team writes a report about the investigation.

**What the team does:**
Write a clear and complete report.
Explain the methods used.
Show the results and findings.
Give advice (sometimes).

🧠 Who gets the report?
Police or lawyers
Company managers
Judges or court officials

📄 Example:
“We found that Mr. X used a USB to steal company files on March 5th at 8:15 PM. The USB had over 1,000 private documents. The action was recorded by the security camera. The files were emailed to an unknown address.”


# Types of Digital Forensics 
During the collection phase, the forensic team may find many types of devices and data.
Each type of device or data needs special tools and techniques to investigate it.
Here are the main types of digital forensics:

1. 💻 Computer Forensics
This is the most common type. It focuses on computers (laptops or desktops).

🧠 Example:
If someone hacks into a system using their personal computer, the forensic team checks:
Files
Programs
Internet history
USB activity

2. 📱 Mobile Forensics
This is used to analyze mobile phones and tablets.

🔍 What they look for:
Call logs
Text messages
WhatsApp or Telegram chats
GPS locations
Photos and videos

🧠 Example:
If a suspect planned a crime by chatting on Telegram, mobile forensics helps find those chats.

3. 🌐 Network Forensics
This focuses on the network — not just one device, but how all the devices are connected.

🔍 What they check:
Internet traffic
IP addresses
Logs from routers or firewalls

🧠 Example:
If a hacker tried to break into a company’s network, forensic experts can trace:
Where the attack came from
What time it happened
What was accessed

4. 🗄️ Database Forensics
This focuses on databases — places where large amounts of important information are stored.

🔍 What they look for:
Who accessed the database
What data was changed or stolen
Any suspicious activity

🧠 Example:
If someone changed grades in a university database, forensic experts can find:
Which account made the change
When it happened
What was changed

5. ☁️ Cloud Forensics
This deals with cloud platforms like Google Drive, AWS, Microsoft Azure, etc.

⚠️ Challenge:
Cloud data is harder to investigate because it’s stored on remote servers, not on your own computer.

🧠 Example:
If a criminal used Dropbox to store illegal files, cloud forensics helps recover and analyze that data.

6. 📧 Email Forensics
This focuses on emails — especially in cases of fraud or phishing.

🔍 What they analyze:
Sender and receiver info
Email content
Attachments
IP addresses

🧠 Example:
If a company was tricked into paying money to a fake account, email forensics can help track:
The fake email
Who sent it
The tricks used (like fake domains or links)
***********************************************************************************************************************
🧾 Evidence Acquisition (Explained Simply)
Collecting digital evidence is a critical and sensitive task. The goal is to gather all useful data without changing or damaging it. Forensics teams follow strict steps and tools during this phase to protect the integrity of evidence.

1.  Proper Authorization
What is it?
Before collecting any data, the forensics team must have official permission (from law enforcement, court, etc.).
Why is it important?
Evidence without permission might be rejected in court.
Digital evidence often includes private or sensitive information.
Following legal procedures helps investigators stay within the law.

Example:
Before analyzing a suspect’s phone or laptop, the investigator must have a signed document from a judge or authority that clearly says which devices can be searched.

2. 🔗 Chain of Custody
What is it?
A formal document or record that tracks:
What was collected (type, description).
Who collected it.
When it was collected.
Where it was stored.
Who accessed it and when.
Why is it important?
Helps prove the evidence is authentic and untouched.
Prevents confusion or manipulation.
Allows accountability (if something goes wrong, we know who had it).

Example:
A USB is collected at the crime scene. The chain of custody shows the USB was collected by Officer John on July 18, stored in Locker A3, and only accessed by one analyst on July 19.

3. 🛑 Use of Write Blockers
What is it?
A hardware device that prevents any write (change) operations on storage devices (like hard drives or USBs) during evidence collection.
Why is it important?
Connecting a hard drive directly to a computer might accidentally change file timestamps or system files.
A write blocker makes sure nothing is modified, keeping the original data safe.

Example:
You want to collect data from a suspect’s hard disk. If you connect it directly to your analysis PC, background apps might change something. But if you use a write blocker, the data stays exactly the same as it was found.

*************************************************************************************************************************
# Windows Forensics

The most common digital evidence found at crime scenes is from personal computers and laptops. These devices usually run operating systems like **Windows**, which is why Windows forensics is a key part of investigations.

---

## 🧪 Forensic Images in Windows

During the **collection phase**, forensic investigators create **forensic images** — exact bit-by-bit copies of the system’s data. There are two main types:

### 1. Disk Image
- A complete copy of the system’s **hard drive** (HDD/SSD).
- Contains **non-volatile** data (does not disappear after shutdown).
- Examples of data:
  - Documents
  - Pictures
  - Videos
  - Internet history
  - Installed programs

### 2. Memory Image
- A copy of the **RAM (memory)**.
- Contains **volatile** data (disappears when the system is turned off).
- Must be collected **before** shutting down the system.
- Examples of data:
  - Open files
  - Running processes
  - Active network connections

---

## 🧰 Common Tools for Windows Forensics

### 🔹 FTK Imager
- Used to **create disk images**.
- Easy-to-use GUI.
- Can also be used to **analyze** disk contents.
- Supports multiple image formats.

### 🔹 Autopsy
- Free and open-source digital forensics tool.
- Used to analyze **disk images**.
- Features:
  - Search by keyword
  - Recover deleted files
  - Metadata analysis
  - Detect file extension mismatches

### 🔹 DumpIt
- Command-line tool to create **memory images**.
- Lightweight and simple.
- Used on live systems to dump RAM.

### 🔹 Volatility
- Open-source tool to **analyze memory images**.
- Works with Windows, Linux, macOS, and Android.
- Uses **plugins** to extract:
  - Running processes
  - Network activity
  - Loaded drivers
  - Many more artifacts

---
