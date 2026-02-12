
# Diference between Magic number & File signature  : 

Magic Number = small part (usually first 2–4 bytes)
File Signature = sometimes same, sometimes larger structural pattern

Magic number = lbdya dyal lfile (1-4 bytes) li katban finno type dyal lfile.
```
Ex: FF D8 FF = JPEG
Ex: 89 50 4E 47 = PNG
Ex: 25 50 44 46 = PDF

```
File signature = parfois kat3ni nafs chi, walakin f b3d references kat3ni magic number + chi structure zayda (kima headers dyal ZIP, length, CRC...).

# Top Tools to View/Modify File Magic Numbers & Signatures

This is a list of well-known and open-source tools to view or inspect the magic numbers (file signatures) of any file
for exemple the file name is  :  `anas`. It includes both CLI and GUI tools, with usage and examples.

| Tool         | Interface | OS         | Description                        |
|--------------|-----------|------------|------------------------------------|
| `xxd`        | CLI        | Linux/macOS | Print file in hex + ASCII format  |
| `hexdump`    | CLI        | Linux       | Display structured hex output     |
| `file`       | CLI        | All         | Detect file type using magic bytes|
| `hexedit`    | CLI        | Linux       | Interactive hex editor in terminal|
| `Bless`      | GUI        | Linux       | Powerful hex editor for Linux     |
| `GHex`       | GUI        | Linux       | GTK-based hex viewer               |
| `HxD`        | GUI        | Windows     | Full-featured hex editor (GUI)    |
| `Hex Fiend`  | GUI        | macOS       | Fast hex viewer/editor             |

---

## CLI Tools

### 1. `xxd`

**Platform**: Linux, macOS  
**Use**: Print hex + ASCII of file

```bash
xxd anas | head
```

---

### 2. `hexdump`

**Platform**: Linux  
**Use**: Show clean hex dump

```bash
hexdump -C anas | head
```

---

### 3. `file`

**Platform**: All OS  
**Use**: Identify file type using magic number

```bash
file anas
```

---

### 4. `hexedit`

**Platform**: Linux  
**Use**: Edit hex directly in terminal (interactive)

```bash
sudo apt install hexedit
hexedit anas
```

---

## GUI Tools

### 5. Bless

**Platform**: Linux  
**Use**: Open `anas` in graphical hex editor

```bash
bless anas
```

---

### 6. GHex

**Platform**: Linux (GTK desktop)  
**Use**: Lightweight hex viewer

```bash
ghex anas
```

---

### 7. HxD

**Platform**: Windows  
**Use**: Full hex editor (copy/paste, overwrite, etc.)  
**Usage**: Open GUI ➤ File ➤ Open ➤ Select `anas`

---

### 8. Hex Fiend

**Platform**: macOS  
**Use**: Lightweight, fast, supports large files  
**Usage**: Launch Hex Fiend ➤ File ➤ Open ➤ `anas`

---

# Top Popular File Signatures (Magic Numbers)

This is a list of well-known file types and their magic numbers (first bytes in hex) for use in file detection, upload filtering, bypasses, and malware analysis.

---

## 📸 Image File Signatures

| Extension | Magic Number (Hex) | Signature (ASCII if any) | Notes         |
|-----------|--------------------|---------------------------|---------------|
| `.jpg`    | `FF D8 FF`         | —                         | JPEG/JFIF     |
| `.jpeg`   | `FF D8 FF`         | —                         | Same as .jpg  |
| `.png`    | `89 50 4E 47 0D 0A 1A 0A` | `‰PNG....`           | PNG image     |
| `.gif`    | `47 49 46 38 37 61` or `47 49 46 38 39 61` | `GIF87a / GIF89a` | GIF image     |
| `.bmp`    | `42 4D`            | `BM`                      | Bitmap image  |
| `.svg`    | XML-based (starts with `<svg`) | —              | Not binary    |
| `.tiff`   | `49 49 2A 00` or `4D 4D 00 2A` | —               | Little/big endian |
| `.ico`    | `00 00 01 00`      | —                         | Icon file     |
| `.webp`   | `52 49 46 46` + `WEBP` | `RIFF....WEBP`        | Google WebP   |

---

## 🎥 Video File Signatures

| Extension | Magic Number (Hex)            | Notes                   |
|-----------|-------------------------------|--------------------------|
| `.mp4`    | `00 00 00 18 66 74 79 70 69 73 6F 6D` | or contains `ftyp` box |
| `.avi`    | `52 49 46 46` + `41 56 49 20` | RIFF header             |
| `.mov`    | `00 00 00 14 66 74 79 70 71 74 20` | QuickTime format        |
| `.flv`    | `46 4C 56`                   | `FLV`                   |
| `.mkv`    | `1A 45 DF A3`                | Matroska                |
| `.webm`   | `1A 45 DF A3`                | WebM (subset of MKV)    |
| `.3gp`    | starts like `.mp4`           | Mobile 3G video         |

---

## 🔊 Audio File Signatures

| Extension | Magic Number (Hex) | Notes                     |
|-----------|--------------------|----------------------------|
| `.mp3`    | `FF FB` or `49 44 33` | `ID3` tag or MPEG stream |
| `.wav`    | `52 49 46 46` + `WAVE` | RIFF header             |
| `.flac`   | `66 4C 61 43`       | `fLaC`                    |
| `.ogg`    | `4F 67 67 53`       | `OggS`                    |
| `.m4a`    | like `.mp4`         | MPEG-4 Audio              |
| `.aac`    | `FF F1` / `FF F9`   | AAC stream                |

---

## 📄 Document File Signatures

| Extension | Magic Number (Hex) | Notes                        |
|-----------|--------------------|-------------------------------|
| `.pdf`    | `25 50 44 46`       | `%PDF`                       |
| `.doc`    | `D0 CF 11 E0 A1 B1 1A E1` | Old Word (97-2003)   |
| `.xls`    | `D0 CF 11 E0 A1 B1 1A E1` | Same format as .doc  |
| `.ppt`    | `D0 CF 11 E0 A1 B1 1A E1` | PowerPoint (old)     |
| `.docx`   | `50 4B 03 04`       | ZIP format, Office Open XML |
| `.xlsx`   | `50 4B 03 04`       | Same as above               |
| `.pptx`   | `50 4B 03 04`       | Same as above               |
| `.rtf`    | `7B 5C 72 74 66`    | RTF header                  |
| `.epub`   | `50 4B 03 04`       | ZIP-based eBook             |

---

## 🗜️ Archive / Compressed File Signatures

| Extension | Magic Number (Hex) | Notes                   |
|-----------|--------------------|--------------------------|
| `.zip`    | `50 4B 03 04`       | `PK..`                  |
| `.rar`    | `52 61 72 21 1A 07 00` | or `52 61 72 21 1A 07 01` |
| `.7z`     | `37 7A BC AF 27 1C` | `7z archive`            |
| `.tar`    | none (identified by structure) | text format       |
| `.gz`     | `1F 8B`             | GZIP                    |
| `.bz2`    | `42 5A 68`          | BZIP2                   |
| `.xz`     | `FD 37 7A 58 5A 00` | XZ compression          |

---

## ⚙️ Executables / Scripts

| Extension | Magic Number (Hex) | Notes                  |
|-----------|--------------------|-------------------------|
| `.exe`    | `4D 5A`            | Windows executable     |
| `.dll`    | `4D 5A`            | Same as `.exe`         |
| `.elf`    | `7F 45 4C 46`      | Linux binaries         |
| `.sh`     | ASCII, often starts with `#!` | Bash script |
| `.py`     | ASCII              | Python script (not binary) |
| `.jar`    | `50 4B 03 04`      | Java archive (ZIP)     |
| `.class`  | `CA FE BA BE`      | Java bytecode class    |

---

##  Tip to View Magic Number in Terminal

```bash
xxd -l 16 filename | head
hexdump -C filename | head
file filename
```

---

##  Note

- Files like `.docx`, `.xlsx`, `.epub`, `.jar` are actually **ZIP files** with different content structure.
- Always check the **magic number**, **not just the extension**.
- Useful in bypassing upload filters or forensics validation.