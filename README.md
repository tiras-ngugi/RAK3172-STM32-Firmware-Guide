# RAK3172 STM32 Firmware Development Guide

![STM32WL](https://img.shields.io/badge/STM32WL-SDK%20V1.4.0+-blue)
![RAK3172](https://img.shields.io/badge/RAK3172-STM32WLE5CCU6-green)
![License](https://img.shields.io/badge/license-MIT-orange)

Complete, documentation for setting up STM32CubeIDE with RAK3172 custom firmware development using the latest STM32WL SDK. Goes beyond the outdated RAKwireless v0.1/v0.2 guides with current tools and procedures, that i have tested so far.

---

## 🎯 **What This Guide Covers**

This comprehensive guide addresses the critical gap in RAK3172 firmware development documentation by providing up-to-date procedures for:

- **Latest Tool Versions**: STM32CubeIDE 1.16-1.19, STM32WL SDK V1.4.0+
- **Complete Installation**: Zero-error, step-by-step procedures
- **RAK3172 Configuration**: Specific .c/.h file modifications for STM32WLE5CCU6
- **Build & Test Procedures**: Validation at each step with troubleshooting
- **Debugging Setup**: Complete ST-LINK and GDB integration
- **Low-Level Programming**: HAL vs LL driver usage and custom code integration
- **Production Ready**: Release builds, security settings, and deployment

---

## 📚 **Documentation**

### **[📖 Complete Setup Guide - View Here](https://www.genspark.ai/doc_agent?id=71b8aee2-f5cc-41e8-82d8-3aad004cb6d8)**

The complete documentation includes:

1. **Hardware and Software Stack Overview**
2. **Prerequisites and System Requirements**
3. **Step-by-Step Installation Guide**
4. **Configuring STM32CubeIDE for RAK3172**
5. **Building and Testing the Firmware**
6. **Programming the RAK3172** (ST-LINK & UART methods)
7. **Low-Level Programming and Customization**
8. **Debugging and Troubleshooting**
9. **Version Updates and Migration**
10. **Production Considerations**
11. **Additional Resources**
12. **Quick Reference Tables**

---

## 🛠️ **Hardware Requirements**

| Component | Specification |
|-----------|---------------|
| **Module** | RAK3172 Module or Evaluation Board (STM32WLE5CCU6) |
| **Programmer** | ST-LINK V2/V3 or compatible JTAG/SWD programmer |
| **Serial Adapter** | USB-to-Serial (3.3V TTL) for UART bootloader programming |
| **Power Supply** | 3.3V regulated, minimum 500mA capability |
| **Antenna** | 868MHz or 915MHz (region dependent) |

### **Connections Required:**
- **SWD Interface**: SWDIO, SWCLK, GND, VDD (for ST-LINK)
- **UART Interface**: TX, RX, GND (for bootloader and debugging)
- **Power**: 3.3V and GND

---

## 💻 **Software Requirements**

| Software | Version | Platform | Notes |
|----------|---------|----------|-------|
| **STM32CubeIDE** | 1.16.0+ | Windows/Linux/macOS | Tested up to 1.19.0 |
| **STM32CubeWL SDK** | V1.4.0+ | Cross-platform | LoRaWAN middleware included |
| **STM32CubeProgrammer** | 2.12.0+ | Windows/Linux/macOS | For flashing firmware |
| **ST-LINK Drivers** | Latest | Windows/Linux | Included in CubeIDE install |

### **Download Links:**
- [STM32CubeIDE Official Download](https://www.st.com/en/development-tools/stm32cubeide.html)
- [STM32CubeWL SDK](https://www.st.com/en/embedded-software/stm32cubewl.html)
- [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html)

---

## 🚀 **Quick Start Guide**

### **5-Step Setup:**

```bash
1. Download and install STM32CubeIDE 1.16+
   └─ Install ST-LINK drivers during setup

2. Download STM32CubeWL SDK V1.4.0+ package
   └─ Extract to: C:\STM32Cube\Repository (Windows)
                   ~/STM32Cube/Repository (Linux/Mac)

3. Open STM32CubeIDE and import example project
   └─ Location: STM32Cube_FW_WL_V1.4.0\Projects\NUCLEO-WL55JC\
                Applications\LoRaWAN\LoRaWAN_End_Node

4. Modify project for RAK3172 compatibility
   └─ Update radio_board_if.c, radio_conf.h, and startup files
   └─ See complete guide for specific changes

5. Build, flash, and test
   └─ Build project (Ctrl+B)
   └─ Flash via ST-LINK or UART bootloader
   └─ Monitor output via serial terminal
