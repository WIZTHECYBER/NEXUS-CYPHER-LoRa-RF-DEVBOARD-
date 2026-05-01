# 🛰️ NEXUS CYPHER: RP2040 LoRa RF Devboard

![KiCad](https://img.shields.io/badge/Designed_in-KiCad_9.0-blue.svg)
![Hardware](https://img.shields.io/badge/Hardware-Open_Source-green.svg)
![Status](https://img.shields.io/badge/Status-V1.0_Ready_for_Fab-orange.svg)

Yo! Welcome to the **Nexus Cypher**. 

I designed this board, and ngl, getting it to the finish line was a massive reality check. This repo doesn't just have the final manufacturing files—it’s the actual log of every time I got humbled by the reviewers and the factory robots. If you're designing your first complex RF board, please learn from my mistakes so you don't get kicked back as much as I did.

## 💡 What I Actually Made
The Nexus Cypher is a custom, open-source Long Range (LoRa) radio frequency devboard. I wanted a flexible, overpowered platform for RF hacking and experiments. 

**The Specs:**
* **Brain:** Raspberry Pi RP2040
* **Radio:** Semtech SX1262 (LoRa)
* **RF Switch:** PE4259 (UltraCMOS SPDT)
* **Storage:** W25Q128JVS (128M-bit Flash)
* **Power:** AP2112K-3.3V LDO
* **Extras:** USB-C, 0.96" OLED header, Reset & Boot buttons.

## Schematics 
<img width="1283" height="836" alt="Screenshot 2026-03-30 024654" src="https://github.com/user-attachments/assets/c6413717-07d1-4046-96aa-68a0806cc8d6" />

## PCB routing 
<img width="654" height="789" alt="Screenshot 2026-04-18 121721" src="https://github.com/user-attachments/assets/e3c543b0-8557-4793-b198-113bbf8ba515" />
<img width="1256" height="723" alt="Screenshot 2026-04-18 122549" src="https://github.com/user-attachments/assets/0666ffb0-5f84-406b-97cb-aaf0318e7531" />
<img width="717" height="693" alt="Screenshot 2026-04-18 132426" src="https://github.com/user-attachments/assets/99c7b23f-eb53-4e4a-b326-8e995ffb42ad" />

## FINAL PCB 
<img width="1919" height="994" alt="Screenshot 2026-04-24 202827" src="https://github.com/user-attachments/assets/9046c32f-5b22-47ef-8fc6-dc9d4684b6b3" />



## 💀 The "Wall of Shame" (Dev Journal)
I spent like 16 hours hyper-focusing on impedance matching and RF traces. I thought I was a genius. Then I submitted it for review and got hit with reality. Here is everything that went wrong and how I fixed it:

### 1. Forgetting humans actually hold these boards
I was so zoomed in on the physics of the RF traces that I completely ignored the physical board itself. 
* **The Roast:** The reviewer literally told me to *"Please neaten up your board a bit with silkscreen, rounded corners, ect."*. 
* **The Fix:** I had sharp 90-degree corners that would probably slice my hand open, and I just slapped my text (`R1`, `C12`, etc.) right on top of my carefully routed traces. I had to go back into KiCad, draw smooth arcs on the `Edge.Cuts` layer, and individually move every single piece of text so the factory could actually print it.

### 2. Asking for way too much money
I was submitting this for a hardware grant and totally fumbled the math.
* **The Roast:** *"Your bom cost is unrealistic you cant be requesting this number... please resubmit with the correcct tier"*.
* **The Fix:** Bruh, you can't just guess your numbers. I had to actually calculate the real-world cost of the RP2040, the LoRa IC, and the JLCPCB assembly fees, and request the correct tier that matched reality.

### 3. Excel cooked my BOM
I thought exporting a Bill of Materials (BOM) was just a one-click thing. 
* **The Roast:** The reviewer just straight up said *"your BOM.csv is broken"*.
* **The Fix:** Excel completely mangled my CSV file. All my capacitors (`C1`, `C8`, `C9`) spilled across 10 different columns, and it used semicolons instead of commas. Also, I learned that JLCPCB factory robots don't read English—they just match text. I had to manually sanitize the entire spreadsheet so the Pick & Place machines wouldn't throw an error. 

### 4. The "Ghost" Repo
I assumed the hardware spoke for itself and left everything blank.
* **The Roast:** *"your ReadME is missing description about your project. Your journals are also not descriptive enough, you need to explain what you did what went well / wrong etc"*.
* **The Fix:** Open-source hardware is literally useless if nobody knows *why* you built it or how it works. That's exactly why I'm writing this massive README right now.

## 🗂️ Files in this Repo
* `/Nexus Cypher production/` - The actual KiCad 9.0 source files.
* `Nexus cypher gerber.zip` - Production-ready Gerbers.
* `Nexus Cypher BOM.csv` - The sanitized, robot-approved Bill of Materials.
* `Nexus Cypher-all-pos.csv` - Pick & Place (CPL) file.

## ⚖️ License
This is open-source hardware, fr. 

* **Hardware:** Released under the **CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S)**. You can use it, mod it, and fab it, but if you change it, you gotta share it under the same terms.
* **Docs/Software:** Released under the **MIT License**.

---
*Built by WIZTHECYBER.*
