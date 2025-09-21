# 🧪 FlareVM - ترسانة أدوات التحليل والهندسة العكسية

---

## 🔍 شنو هو FlareVM؟

**FlareVM** هو نظام Windows مهيأ خصيصًا لتحليل البرمجيات الخبيثة (malware) والهندسة العكسية (Reverse Engineering).  
الاسم ديالو هو اختصار لـ:

- **F**orensics  
- **L**ogic **A**nalysis  
- **R**everse **E**ngineering

🌐 طوراتو شركة **FireEye** (الـ FLARE Team) باش يكون عندك نظام Windows كامل فيه كل الأدوات لي كيتستعملو فـ:

- 🔬 تحليل المالوير (Malware Analysis)  
- ⚙️ الهندسة العكسية (Reverse Engineering)  
- 🚨 الاستجابة للحوادث (Incident Response)  
- 🧾 التحقيقات الجنائية الرقمية (Digital Forensics)  
- 💻 اختبار الاختراق (Pentesting)

---

## 🧰 شنو كيتضمن FlareVM؟

FlareVM ماشي غير VM، هو عبارة عن **بيئة Windows متكاملة** فيها أكثر من **100 أداة احترافية**.  
من بعد التثبيت، النظام كيكون عامر بأدوات متخصصة فكل مجال.

---

## 🛠️ أنواع الأدوات:

| 🧪 المجال                 | ⚙️ أمثلة ديال الأدوات                            |
|---------------------------|--------------------------------------------------|
| 🔬 تحليل المالوير         | PEStudio، x64dbg، IDA Free، dnSpy               |
| ⚙️ الهندسة العكسية       | Ghidra، Binary Ninja (Free)، Cutter             |
| 📂 تحليل المستندات الخبيثة| olevba، PDF Stream Dumper، rtfobj               |
| 🔍 الشبكة & الحزم         | Wireshark، NetworkMiner                         |
| 🧠 تحليل السلوك           | Procmon، Regshot، Process Explorer              |
| 💣 أدوات exploit          | Metasploit، PowerSploit (حسب الإعداد)           |
| 📚 أدوات عامة             | Python، YARA، Sysinternals Suite                |
"""


# 🧰 Arsenal of Tools - FlareVM

في هاد الجزء، غادي نكتاشفو الأدوات لي كيتضمنهم FlareVM.  
FlareVM كيحتوي على مجموعة ضخمة من الأدوات المتخصصة في:

- 🧬 التحقيقات الجنائية الرقمية (Forensics)
- 🚨 الاستجابة للحوادث (Incident Response)
- 🦠 تحليل المالوير (Malware Investigation)

---

## 🛠️ Reverse Engineering & Debugging

الهندسة العكسية بحال تحل لغز من الأخير للبداية: كتحاول تفهم كيفاش الخدمة مصوبة.  
والـ Debugging هو تصحيح الأخطاء وفهم السبب ديالهم.

| الأداة | الشرح |
|-------|-------|
| **Ghidra** | أداة مفتوحة المصدر من NSA للهندسة العكسية |
| **x64dbg** | Debugger مفتوح المصدر لـ x64 و x32 binaries |
| **OllyDbg** | Debugger على مستوى الـ Assembly |
| **Radare2** | منصة متقدمة للهندسة العكسية مفتوحة المصدر |
| **Binary Ninja** | أداة لـ disassembling و decompiling للبرمجيات |
| **PEiD** | أداة لاكتشاف الـ packers, cryptors, compilers |

---

## 🧩 Disassemblers & Decompilers

مهمين بزاف فـ تحليل المالوير، كيسهلو علينا نفهمو السلوك ديالو.

| الأداة | الشرح |
|-------|-------|
| **CFF Explorer** | محرر PE لفحص وتعديل ملفات Executable |
| **Hopper Disassembler** | Debugger و Disassembler و Decompiler |
| **RetDec** | Decompiler مفتوح المصدر للكود الآلي |

---

## 🔍 Static & Dynamic Analysis

- **Static Analysis**: تحليل الكود بلا تشغيله  
- **Dynamic Analysis**: ملاحظة السلوك أثناء التشغيل

| الأداة | الشرح |
|-------|-------|
| **Process Hacker** | أداة متقدمة لفحص العمليات والذاكرة |
| **PEview** | عارض لملفات PE |
| **Dependency Walker** | كيبين الـ DLLs اللي كيستعملهم البرنامج |
| **DIE (Detect It Easy)** | لكشف الـ packers والـ compilers |

---

## 🧠 Forensics & Incident Response

- **Forensics**: جمع وتحليل الأدلة الرقمية  
- **Incident Response**: كشف واحتواء ومعالجة الهجمات

| الأداة | الشرح |
|-------|-------|
| **Volatility** | تحليل RAM dump |
| **Rekall** | إطار لتحليل الذاكرة |
| **FTK Imager** | أداة للحصول على صورة من القرص وتحليلها |

---

## 🌐 Network Analysis

فحص الشبكات وتحليل الـ traffic والهيكلة ديالها.

| الأداة | الشرح |
|-------|-------|
| **Wireshark** | محلل بروتوكولات الشبكة |
| **Nmap** | أداة كشف الثغرات وخريطة الشبكة |
| **Netcat** | إرسال واستقبال البيانات عبر الشبكة |

---

## 📁 File Analysis

تحليل الملفات وكشف التهديدات فيها.

| الأداة | الشرح |
|-------|-------|
| **FileInsight** | محرر للملفات الثنائية (binary) |
| **Hex Fiend** | محرر Hex سريع |
| **HxD** | محرر للملفات الثنائية بـ Hex |

---

## 🤖 Scripting & Automation

القيام بالمهام المتكررة أوتوماتيكياً باستعمال PowerShell أو Python.

| الأداة | الشرح |
|-------|-------|
| **Python** | اللغة الأساسية للسكريبتات |
| **PowerShell Empire** | إطار عمل بعد الاستغلال بـ PowerShell |

---

## 🧰 Sysinternals Suite

مجموعة من الأدوات القوية لإدارة وتحليل نظام Windows.

| الأداة | الشرح |
|-------|-------|
| **Autoruns** | كيبين البرامج اللي كتبدأ مع النظام |
| **Process Explorer** | معلومات متقدمة على العمليات |
| **Process Monitor** | مراقبة النشاط فـ الوقت الحقيقي |

---
