# DFIR & Steganography Cheat-Sheet — Anas Education

**By Anas Education**

---

## مقدمة

هاد الملف فيه ملخص منظم على الأدوات والتقنيات اللي تهمّ **DFIR** (Digital Forensics & Incident Response) وبالخصوص قسم **steganography** (audio, image, video) وكذا شوية ملاحظات على التحليل ديال الذاكرة والشبكة. الهدف: مرجع سريع للـ CTF أو التحقيقات الواقعية.

---

## A) Audio Steganography

* **Audacity** — spectrogram / GUI (تحليل الصوت، عرض spectrogram باش تشوف تكميم/طيف الصوت).
* **Sonic Visualiser** — عرض وتحليل الطيف الصوتي.
* **Tones encrypt** (مثل Morse-like encodings).
* **DeepSound** (Windows) — hide/extract files in WAV/FLAC. (مثال: DeepSound installer).
* **SonicStrike / Coagula** — مشاريع لتحويل البيانات لصوت (encoding data to sound).
* **steganography-audio** (Python libs) — مكتبات بايثون مخصصة للصوت.
* **sox** — معالجة صوتية (تحويل، فلترة، استخراج معلومات).

### أوامر/نصائح

* استخراج spectrogram فـ Audacity أو Sonic Visualiser.
* تجربة تحويل للصوت إلى spectrogram وبحث عن نماذج مرئية.

---

## B) Image Steganography

أدوات أساسية:

* **exiftool** — قراءة وتعديل metadata.
* **strings** — استخراج نصوص داخل الصور.
* **exiv2** — قراءة metadata.
* **zsteg** — مخصص لصور PNG (كشف LSB، ألوان، channels).
* **stegsolve** — أداة GUI لتجريب عمليات تحويل الألوان/bit planes.
* **GIMP** — تحرير وفحص قنوات الصورة.
* **steghide** — استخراج/إدخال بيانات في BMP/JPEG.
* **stegseek / stegcracker** — هجمات كسر كلمات السر على steghide-like containers.
* **binwalk** — فحص واستخراج data مخفية داخل ملف (use --dd='.*').
* **hex editors**: xxd, hexdump, bless, wxHexEditor — مفيدين للفحص العميق.
* **stegoveritas**, **stegosuite**, **stegsnow** — أدوات إضافية لكشف وتقنيات متعددة.

### أوامر مفيدة

* `exiftool image.jpg`
* `binwalk --dd='.*' image.jpg`
* `zsteg image.png`
* `steghide extract -sf image.jpg`
* `strings image.jpg | less`
* `xxd -g 1 image.jpg | less`

---

## C) Video / Multimedia Steganography

* **ffmpeg** — استخراج الإطارات (frames) أو الـ audio من الفيديو، تحويل الصيغ (أساسيات).
* **stegseek / stegsolve** — بعض الأحيان يخدمو على frames المستخرجة.
* مشاريع بحثية / academic tools: **BBleisure**, **vikhyat** (أسماء أمثلة بحثية — تحقق من المصادر).

### Workflow مقترح

1. `ffmpeg -i video.mp4 -qscale:v 2 frames/frame_%04d.jpg`  # استخراج frames
2. استعمل `zsteg` أو `stegsolve` على frames.
3. استخرج audio: `ffmpeg -i video.mp4 -vn -acodec copy audio.wav` ثم طبق أدوات audio stego.

---

## D) Memory Analysis (Volatility)

* **Volatility 3** — نشتغلو على ملفات `.mem` ونستعملو plugins باش نتحقق من العمليات، الشبكات، injection...
* مستحسن: نشرح كل plugin اللي كيهمنا أو نستعمل ال-writeup الخاص بـ Volatility3.
* رابط للمصدر الرسمي plugins (Volatility): `https://github.com/volatilityfoundation/volatility/tree/master/volatility/plugins`

---

## E) Network Analysis

* **Wireshark** — تحليل شبكات بصري.
* **tshark** — نسخة CLI من Wireshark (مناسبة للـ automation و-scripts).

### أوامر سريعة

* `tshark -r capture.pcap -Y "http.request"`  # تصفية طلبات HTTP
* `tshark -r capture.pcap -T fields -e ip.src -e ip.dst -e tcp.port`  # استخلاص حقول محددة

---

## Checklist / Workflow DFIR مختصر

1. **Collect**: حافظ على الـ images الأصلية (memory, disk, pcap).
2. **Initial triage**: pslist/pstree/psscan, netscan، malfind.
3. **Dump**: procdump/vad_dump/dumpfiles لأي عناصر مشبوهة.
4. **Stego**: image/audio/video — استخرج frames/audio، طبق zsteg/DeepSound/stegsolve.
5. **Network**: استخرج الاتصالات المريبة، اربط بين PID والـ sockets.
6. **Timeline**: اجمع timestamps عبر shimcache/mftparser/timeliner.
7. **Report**: دون النتائج وخلاّص الأدلة (hashes, offsets, screenshots).

---

## مراجع وأدلة إضافية

* Volatility plugins repo — GitHub
* أدوات steganography documentation (Manual pages for exiftool, binwalk, steghide, ffmpeg)

---

**By Anas Education**

*End of document.*
