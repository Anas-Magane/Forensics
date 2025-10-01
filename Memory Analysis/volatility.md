# Volatility3 Writeup — Anas Education

**By Anas Education**

---

## مقدمة

هاد ال-writeup مخصّص لـ **Volatility 3** باش يعاونك تدير memory forensics فـ CTF ولا في تحليل حادثة. غادي تلقى هنا لائحة plugins مهمّين، شنو كيديرو، كيفاش تستعملهم بالـ commands، وشي نصائح عملية باش تنظّم workflow ديالك.

> ملاحظة: الأوامر مكتوبة باستعمال Volatility 3 (مثال: `python vol.py -f mem.img windows.pslist.PsList`).

we have another tools to extract memory like : 
FTK Imager
Redline
DumpIt.exe
win32dd.exe / win64dd.exe
Memoryze
FastDump 
---

## 1) pslist — `windows.pslist.PsList`

**شنو كيدير:** كيوري لائحة البروسيس اللي كانوا فذاك اللقطة ديال الميموار.

**علاش مهم:** بداية التحليل — كتقلب على processes مشبوهين، PID بدون parent، أوقات إنشاء غريبة.

**شنو تشوف:** PID, PPID, ImageFileName, Threads, Handles, CreateTime.

**أمر مثال:**

```
python vol.py -f mem.img windows.pslist.PsList
```

---

## 2) pstree — `windows.pstree.PsTree`

**شنو كيدير:** يظهر لك شجرة العمليات (parent → child).

**علاش مهم:** باش تفهم العلاقة بين العمليات وتشوف عمليات تالفة أو مولدة من عملية مشبوهة.

**أمر مثال:**

```
python vol.py -f mem.img windows.pstree.PsTree
```

---

## 3) psscan — `windows.psscan.PsScan`

**شنو كيدير:** يبحث عن هياكل process فالميموار حتى إلا ما كانوش فـ pslist (مخفيين أو terminated).

**علاش مهم:** كيكشف rootkits و stealth processes.

**أمر مثال:**

```
python vol.py -f mem.img windows.psscan.PsScan
```

---

## 4) netscan — `windows.netscan.NetScan`

**شنو كيدير:** يجبد sockets و connections (TCP/UDP) اللي موجودين فالميموار.

**علاش مهم:** تتبّع اتصالات خارجية ديال malware، backdoor أو C2.

**شنو تشوف:** local/remote IP, ports, PID، state.

**أمر مثال:**

```
python vol.py -f mem.img windows.netscan.NetScan
```

---

## 5) connscan — `windows.connscan.ConnScan`

**شنو كيدير:** low-level scan لبنيات TCP connections.

**علاش مهم:** يلقا اتصالات حتى إلا كانت مخفية أو تم التلاعب بها.

**أمر مثال:**

```
python vol.py -f mem.img windows.connscan.ConnScan
```

---

## 6) dlllist — `windows.dlllist.DllList`

**شنو كيدير:** يعرض DLLs المحمّلين فكل process.

**علاش مهم:** باش تكتاشف DLL injection أو DLLs مشبوهة.

**أمر مثال:**

```
python vol.py -f mem.img windows.dlllist.DllList --pid <PID>
```

---

## 7) handles — `windows.handles.Handles`

**شنو كيدير:** يبيّن handles (ملفات، registry keys, events...) لكل process.

**علاش مهم:** يمكن تكتشف ملفات مفتوحة مشبوهة، mutex خاص بالـ malware.

**أمر مثال:**

```
python vol.py -f mem.img windows.handles.Handles --pid <PID>
```

---

## 8) malfind — `windows.malfind.Malfind`

**شنو كيدير:** يبحث على مناطق ذاكرة executable ومشتبه فيها (possible code injection أو unpacked code).

**علاش مهم:** أداة أساسية لاكتشاف injection و shellcode.

**شنو تشوف:** PID, base address, size، وكيعطيك إمكانية لتفريغ المنطقة.

**أمر مثال:**

```
python vol.py -f mem.img windows.malfind.Malfind
```

---

## 9) yarascan / strings / procdump

* **yarascan (windows.yarascan.YaraScan):** تطبق قواعد YARA على الميموار.
* **strings (windows.strings.Strings):** استخراج ASCII/Unicode strings من الميموار.
* **procdump (windows.procdump.ProcDump):** تفريغ عملية (proc dump) لملف exe قابل للتحليل.

**أمثلة:**

```
python vol.py -f mem.img windows.yarascan.YaraScan -y rules.yar
python vol.py -f mem.img windows.strings.Strings
python vol.py -f mem.img windows.procdump.ProcDump --pid <PID> --dump-dir ./dumps
```

---

## 10) filescan + dumpfiles

**شنو كيديرو:** filescan يلقا File objects فالميموار. dumpfiles يخرّج الملفات لي لقا.

**علاش مهم:** تلقى نسخ ديال ملفات DLL، temp files، أو ملفات malware مخفية.

**أمر مثال:**

```
python vol.py -f mem.img windows.filescan.FileScan
# ثم استعمل dump مع الـ offset اللي عطاك filescan
python vol.py -f mem.img windows.dumpfiles.DumpFiles -Q <offset> --dump-dir ./files
```

---

## 11) cmdline / consoles (CommandLine history)

**شنو كيديرو:** يطلعو command-line اللي استعملو باش يشغلو العمليات.

**علاش مهم:** تقدر تلقى arguments مشبوهة، مسارات تنفيذية، سكربتات.

**أمر مثال:**

```
python vol.py -f mem.img windows.cmdline.CmdLine --pid <PID>
```

---

## 12) shimcache / mftparser / timeliner

* **shimcache (AppCompatCache):** لائحة البرامج اللي تشتغلات فالنظام.
* **mftparser:** يقرا MFT ويعطي timestamps ديال الملفات.
* **timeliner / windows.timers:** يبني timeline للأحداث.

**علاش مهم:** لبناء قصة الحدث وربط النشاطات الزمنية.

---

kayn htta 
```bash
modscan
driverirp
callbacks
idt
apihooks
moddump
handles
```
## Checklist عملي (workflow)

1. احتفظ بنسخة من ال-memory image (backup).
2. بدا بـ `windows.pslist.PsList` و `windows.pstree.PsTree`.
3. استعمل `windows.psscan.PsScan` باش تكشف العمليات المخفية.
4. بحث على شبكات بـ `windows.netscan.NetScan` و `windows.connscan.ConnScan`.
5. دورّ على injection بـ `windows.malfind.Malfind` و `windows.yarascan.YaraScan`.
6. dump للـ processes المشبوهين: `windows.procdump.ProcDump --pid <PID>`.
7. استخرج ملفات مهمة بـ `windows.filescan.FileScan` و `windows.dumpfiles.DumpFiles`.
8. جمّع timeline بـ `shimcache`, `mftparser`, `timeliner`.

---

## CTF Tips

* دائما خذ snapshot backup قبل أي write.
* استعمل `psscan + pslist + pstree` مع بعض باش تلصق النتائج.
* إذا لقيت malfind output، dump region وفتحو فـ IDA/Ghidra.
* استعمل YARA rules عامة (MZ header, shellcode patterns, suspicious strings).

---

## مثال عملي: dump ديال mspaint (PID 800)

1. تفقد الـ VADs:

```
python vol.py -f mem.img windows.vadinfo.VadInfo --pid 800
```

2. dump كامل ديال process (procdump):

```
python vol.py -f mem.img windows.procdump.ProcDump --pid 800 --dump-dir ./dumps
```

3. ولا dump كل VADs:

```
python vol.py -f mem.img windows.vad_dump.VadDump --pid 800 --dump-dir ./dumps
```

4. تحقق بالـ `file` و `strings` على الملفات اللي خرجت.

---

*to find history of chrome for the user  use this*
```bash
vol -f memdump1.mem windows.filescan | grep -i "Google\\\\Chrome\\\\User Data\\\\Default\\\\History" 
```
 and the result like this 
 ```
0x81595680 100.0\Users\d33znu75\AppData\Local\Google\Chrome\User Data\Default\History
```

## خاتمة

هاد ال-writeup هو cheat-sheet عملي لـ Volatility3 باش تبدا تحلل memory images فالـ CTF ولا فالـ forensic investigation. استعملو كـ مرجع وخد ملاحظاتك لكل حالة.

---
# CTFs

## memory dump 


```bash
python vol.py -f ../monaliza.mem windows.pslist
```
Results  :

```bash
PID     PPID    ImageFileName   Offset(V)       Threads Handles SessionId       Wow64   CreateTime      ExitTime        File output

4       0       System  0x821c87c0      50      256     N/A     False   N/A     N/A     Disabled
400     4       smss.exe        0x81f0b020      3       19      N/A     False   2020-03-21 07:59:05.000000 UTC  N/A     Disabled
456     400     csrss.exe       0x81fa0020      10      331     0       False   2020-03-21 07:59:06.000000 UTC  N/A     Disabled
480     400     winlogon.exe    0x81f56128      16      561     0       False   2020-03-21 07:59:06.000000 UTC  N/A     Disabled
524     480     services.exe    0x81f5f020      15      266     0       False   2020-03-21 07:59:07.000000 UTC  N/A     Disabled
536     480     lsass.exe       0x81f6e128      20      361     0       False   2020-03-21 07:59:07.000000 UTC  N/A     Disabled
688     524     svchost.exe     0x82063210      17      212     0       False   2020-03-21 07:59:07.000000 UTC  N/A     Disabled
748     524     svchost.exe     0x81ffdda0      10      275     0       False   2020-03-21 07:59:08.000000 UTC  N/A     Disabled
812     524     svchost.exe     0x81f28230      69      1367    0       False   2020-03-21 07:59:08.000000 UTC  N/A     Disabled
860     524     svchost.exe     0x81e5e7a8      4       71      0       False   2020-03-21 07:59:08.000000 UTC  N/A     Disabled
1032    524     svchost.exe     0x81f2cc10      11      178     0       False   2020-03-21 07:59:09.000000 UTC  N/A     Disabled
1248    1228    explorer.exe    0x81e29188      12      526     0       False   2020-03-21 07:59:10.000000 UTC  N/A     Disabled
1368    524     spoolsv.exe     0x81e18758      10      120     0       False   2020-03-21 07:59:10.000000 UTC  N/A     Disabled
1488    524     svchost.exe     0x81f4d7e8      4       105     0       False   2020-03-21 07:59:18.000000 UTC  N/A     Disabled
2032    524     alg.exe 0x81f6fc20      6       105     0       False   2020-03-21 07:59:22.000000 UTC  N/A     Disabled
364     812     wscntfy.exe     0x81f8d7f8      1       31      0       False   2020-03-21 07:59:23.000000 UTC  N/A     Disabled
1464    812     wuauclt.exe     0x81fe8398      3       105     0       False   2020-03-21 08:00:25.000000 UTC  N/A     Disabled
1944    1592    FTK Imager.exe  0x81fe17c0      0       -       0       False   2020-03-21 08:07:09.000000 UTC  2020-03-21 08:20:25.000000 UTC       Disabled
1064    1248    FTK Imager.exe  0x820c51a8      0       -       0       False   2020-03-21 08:18:50.000000 UTC  2020-03-21 08:35:39.000000 UTC       Disabled
964     1248    FTK Imager.exe  0x81dd0c98      0       -       0       False   2020-03-21 10:01:19.000000 UTC  2020-03-21 10:01:21.000000 UTC       Disabled
800     1248    mspaint.exe     0x8201b3c0      6       103     0       False   2020-03-21 10:10:29.000000 UTC  N/A     Disabled
924     524     svchost.exe     0x81ea8b70      9       137     0       False   2020-03-21 10:10:29.000000 UTC  N/A     Disabled

```
daba endna wahed l file mchkok fih matalan 
```bash
mspaint.exe
```
ghadi nzido check var nt2kkdo bli bssh mchkok fih

```bash
python3 vol.py -f ../monaliza.mem windows.malfind --pid 800
```
ghadi tbanlina chi haja bhal 

```bash
800 mspaint.exe 0x290000 0x357fff Vad PAGE_EXECUTE_READ 0 0 Disabled N/A

```
wndiro dump lkoll memory region 

```bash
python3 ~/Desktop/CyberTalents/DFIR/monaliza/volatility3/vol.py -f ../monaliza.mem windows.dumpfiles --pid 800

```
hada hsssn bach 
```bash
python3 ~/Desktop/CyberTalents/DFIR/monaliza/volatility3/vol.py -f ../monaliza.mem windows.memmap --pid 800 --dump
```
safe moraha imma ndiro strings grep flag|ctf.... wn9llbo f dok all files /*.dmp
```bash 
strings /*.dmp | grep -E "password|flag|user"
strings /*.dmp | grep -i "ctf"  

```
*There are also a number of wikis and various community resources that can be used for more information about Volatility techniques found below.*
```
https://github.com/volatilityfoundation/volatility/wiki
https://github.com/volatilityfoundation/volatility/wiki/Volatility-Documentation-Projec
https://digital-forensics.sans.org/media/Poster-2015-Memory-Forensics.pdf
https://eforensicsmag.com/finding-advanced-malware-using-volatility/
```

**By Anas Education**

*End of document.*
