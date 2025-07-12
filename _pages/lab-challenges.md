---
layout: single
title: "Lab Challenges"
permalink: /lab-challenges/
author_profile: true
---

## 🔐 CTF & Lab Challenges

---

### RED (Image Forensics CTF)

**Challenge Prompt**:  
"Can you find the flag in this disk image?"  
Given file: `red.png`

**Tools Used**:  
`zsteg`, `binwalk`, `exiftool`, `xxd`, `base64`

**What I Did**:
- Started with `exiftool` — found poetic metadata (red herring)
- Used `binwalk` to spot a compressed block at `0x11C`
- Tried decompressing with `xxd` and zlib (didn't work)
- Used `zsteg` → found base64 hidden in LSBs of the image
- Decoded the base64 flag:  
  `picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}`

**Key Takeaway**:  
Use `zsteg` early with PNGs. Some clues will mislead — stay focused.

---

### Hidden Flag in Disk Image

**Challenge Prompt**:  
"Can you find the flag in this disk image?"  
Given file: zipped `.dd` disk image

**Tools Used**:  
`strings`, `grep`, `binwalk`, `file`, `unzip`

**What I Did**:
- Unzipped `.dd` file
- Ran `strings | grep pico` — and found the flag in plaintext!
- Explored the image further with `binwalk` and `file`

**Key Takeaway**:  
Start with `strings` before diving deep. Flags are often easier to spot than you expect.
