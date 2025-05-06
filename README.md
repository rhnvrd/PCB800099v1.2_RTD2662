# **RTD2662-Arduino-LCD-Flasher**  
*A universal tool to flash firmware for RTD2662/RTD2660 chips (e.g., PCB800099/P08 v1.2) using Arduino and I²C.*  

---

## **Key Features**  
- ✅ **Multi-Arduino support**: Works with **any Arduino board** (Mega, Uno, Nano, etc.)—just adjust pins tell me if you want more info.  
- 📌 **Pin flexibility**: Customize connections via `#define` in the sketch.  
- 🔄 **Simple commands**: Write, verify, erase, or backup firmware via Serial Monitor.  
- 💾 **SD card support**: Load firmware from a microSD (FAT32).  

---

## **Compatibility & Pin Configuration**  
### **Supported Arduino Boards**  
The project works with **all Arduino boards** (e.g., Mega 2560, Uno, Nano, Leonardo) by modifying these pins in the sketch:  

| Function       | Arduino Mega 2560 | Arduino Uno/Nano | Custom Board?  |  
|----------------|-------------------|------------------|----------------|  
| **SD Card CS** | Pin 10            | Pin 10           | Define in code |  
| **SD SCK**     | Pin 52            | Pin 13           |                |  
| **SD MOSI**    | Pin 51            | Pin 11           |                |  
| **SD MISO**    | Pin 50            | Pin 12           |                |  
| **I²C SDA**    | SDA (Pin 20)       | A4               |                |  
| **I²C SCL**    | SCL (Pin 21)       | A5               |                |  

### **How to Adapt for Other Boards**  
1. **Edit the sketch**: Update these lines in `Adafruit_RTD266X_I2CFlasher.ino`:  
   ```cpp
   #define SD_CS   10   // Change to your CS pin
   #define SD_SCK  13   // e.g., Uno/Nano use 13
   #define SD_MOSI 11   // Uno/Nano use 11
   #define SD_MISO 12   // Uno/Nano use 12
   ```  
2. **I²C pins are fixed per board** (e.g., Uno uses `A4/A5`). No changes needed unless using a non-standard board.  

---

## **Setup & Wiring**  
### **Universal Connections**  
1. **SD Card Module**:  
   ```plaintext
   CS   → Arduino Digital Pin (e.g., 10)  
   SCK  → Arduino SCK (Mega:52, Uno:13)  
   MOSI → Arduino MOSI (Mega:51, Uno:11)  
   MISO → Arduino MISO (Mega:50, Uno:12)  
   VCC  → 5V  
   GND  → GND  
   ```  
2. **RTD2662 Board**:  
   ```plaintext
   SCL → Arduino SCL (Mega:21, Uno:A5)  
   SDA → Arduino SDA (Mega:20, Uno:A4)  
   GND → GND  
   ```  

---

## **Usage**  
### **Serial Monitor Commands**  
Send commands in format: `[command]_[filename.bin]` (max 8-char filename):  
- **`w_1.bin`** → Write `1.bin` to chip.  
- **`v`** → Verify firmware.  
- **`e`** → Erase chip.  
- **`r`** → Read firmware to a file in sdcard (backup).  

**Example**:  
```plaintext
w_fw.bin    // Writes firmware (fw.bin) 
v    // Verifies  
```

---

## **Why This Project?**  
- **No proprietary tools**: Just an Arduino and SD card.  
- **Cross-board support**: Mega, Uno, Nano, etc.  
- **Backup-friendly**: Save OEM firmware with `r` command.  

**License**: MIT.  
**Contributions welcome!**  