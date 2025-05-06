# **PCB800099v1.2_RTD2662 Programmer**  

### **Description**  
This repository contains tools and firmware for programming the **RTD2662** IC used in the **PCB800099 v1.2** (also known as **P08-2AV-1VGA-1HDMI-TTL-LVDS-AUDIO-AOC-V1.2**) board to support various LCDs.  

---

## **Programming Methods**  
There are multiple ways to program the RTD2662 IC:  

1. **[Adafruit_RTD266X_I2CFlasher](https://github.com/adafruit/Adafruit_RTD266X_I2CFlasher/tree/master)**  
   - A forked project I successfully used for flashing.  
2. **[ghent360/RTD-2660-Programmer](https://github.com/ghent360/RTD-2660-Programmer)**  
   - An alternative method worth exploring.  

### **Complete Firmware & Tools Source**  
I found a comprehensive resource at **[kolins.cz](https://www.kolins.cz/share/RTD2662/)**, which I forked into this project. It includes:  
- Precompiled binaries (`*.bin` files)  
- Documentation & tools  
- (Possibly the most complete RTD2662 collection available online)  

**Board Manufacturer:** [AirDisp](http://www.airdisp.com/)  

---

## **Setup & Wiring Guide**  

### **Required Hardware**  
- **Arduino Mega 2560** (`arduino:avr:mega`)  
- **MicroSD Card Adapter**  

### **SD Card Connections**  
| SD Card Pin | Arduino Mega 2560 Pin |  
|-------------|----------------------|  
| CS          | 10                   |  
| SCK         | 52                   |  
| MOSI        | 51                   |  
| MISO        | 50                   |  
| VCC         | 5V                   |  
| GND         | GND                  |  

**Note:** Store the firmware `.bin` file on the SD card with the filename specified in the Arduino project.  

### **I²C & Power Connections (LCD Driver Board → Arduino)**  
- **SCL** → **SCL** (I²C Clock)  
- **SDA** → **SDA** (I²C Data)  
- **GND** → **GND** (Ground)  

---

## **Flashing Process**  
Once connected:  
1. Upload the **Adafruit_RTD266X_I2CFlasher** sketch to the Arduino.  
2. The firmware from the SD card will be flashed to the **RTD2662/RTD2660** IC.  

Now you can load your desired firmware onto the display controller!  
