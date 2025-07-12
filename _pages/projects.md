---
layout: single
title: "Projects"
permalink: /projects/
author_profile: true
---

## 🧪 Selected Projects

---

### 🔍 RED (Image Forensics CTF)

**Description**:  
Analyzed a suspicious `.png` image file to uncover a hidden flag using steganography and forensics tools.

**Tools Used**:  
`zsteg`, `binwalk`, `exiftool`, `xxd`, `base64`

**Approach**:  
- Started with metadata analysis using `exiftool` (red herring).
- Ran `binwalk` to identify embedded data at offset `0x11C`.
- Attempted decompression via `xxd` and zlib (unsuccessful).
- Successfully extracted and decoded a base64-encoded flag hidden in pixel LSBs using `zsteg`.

**Outcome**:  
Found and decoded the flag:  
`picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}`

**Key Lessons Learned**:  
- Always try `zsteg` early when analyzing `.png` files  
- Metadata can mislead — don’t chase every rabbit hole  
- Think visually: LSBs can hide textual data effectively

---

### 💾 Hidden Flag in Disk Image (CTF Challenge)

**Description**:  
Investigated a `.dd` (disk image) file for hidden content — focusing on plaintext extraction techniques.

**Tools Used**:  
`strings`, `grep`, `binwalk`, `file`, `unzip`

**Approach**:  
- Unzipped the `.dd` file to get raw disk image.
- Searched for readable flag patterns using `strings | grep pico`.
- Verified the flag in cleartext without needing advanced extraction.
- Explored file structure further with `binwalk`, `file`, and optionally mount (not needed in this case).

**Outcome**:  
Successfully retrieved the flag directly using simple command-line tools.

**Key Lessons Learned**:  
- Start simple: `strings` can be surprisingly effective.
- Not all disk image flags are deeply hidden — avoid overcomplicating.
- Reinforced core file carving and basic forensic skills.

