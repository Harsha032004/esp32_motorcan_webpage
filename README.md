# ESP32 Four Motor Controllers Dashboard

A real-time web dashboard for monitoring four motor controllers via CAN bus communication using an ESP32 microcontroller.

## 🚀 Live Demo

**[View Live Dashboard](https://yourusername.github.io/esp32-motor-dashboard)**

*Replace `yourusername` with your actual GitHub username*

## 📋 Features

- **Real-time CAN Bus Monitoring** - Monitors 4 motor controllers simultaneously
- **Web-based Dashboard** - Beautiful, responsive interface accessible from any device
- **Motor Performance Metrics** - RPM, throttle percentage, and motor status
- **Power Monitoring** - Battery and AC voltage/current readings
- **Temperature Monitoring** - MCU and motor temperature with visual indicators
- **Fault Detection** - Real-time fault status and error reporting
- **Connection Status** - Live connection indicators for each motor
- **Mobile Responsive** - Works on desktop, tablet, and mobile devices

## 🛠️ Hardware Requirements

- **ESP32 Development Board**
- **CAN Bus Transceiver Module** (e.g., MCP2515, SN65HVD230)
- **4 Motor Controllers** with CAN bus support
- **CAN Bus Network** connecting all devices

## 📊 Motor Controller Protocol

The system monitors three types of CAN messages for each motor:

### Message Types:
1. **Basic Info (0x14520900 + Motor ID)**
   - Motor ID, RPM, Throttle %, Battery V/A

2. **AC & Temperature (0x18530900 + Motor ID)**
   - AC Voltage/Current, MCU Temperature, Motor Temperature, Ready Status

3. **Status & Faults (0x1C530900 + Motor ID)**
   - Drive Control Status, MCU Faults

### Supported Motor IDs:
- Motor 1: `0x02`
- Motor 2: `0x03` 
- Motor 3: `0x04`
- Motor 4: `0x05`

## 🔧 Installation & Setup

### ESP32 Arduino Code

1. **Install Required Libraries:**
   ```cpp
   #include <WiFi.h>
   #include <WebServer.h>
   #include <ArduinoJson.h>
   #include "driver/twai.h"
   ```

2. **Hardware Connections:**
   ```
   ESP32 Pin 21 (GPIO_NUM_21) → CAN TX
   ESP32 Pin 22 (GPIO_NUM_22) → CAN RX
   ```

3. **Configuration:**
   - Update WiFi credentials in the code
   - Verify CAN bus baud rate (default: 500kbps)
   - Confirm motor controller IDs match your setup

4. **Upload and Run:**
   - Compile and upload to ESP32
   - Connect to your WiFi network
   - Access dashboard via ESP32's IP address

### GitHub Pages Demo

The live demo shows simulated data demonstrating the dashboard's capabilities:
- Animated RPM, temperature, and current values
- Realistic motor controller behavior simulation
- All visual elements and fault indicators

## 📱 Dashboard Interface

### Status Bar
- Connection status for all 4 motors
- Last update timestamp
- Real-time connection indicators

### Motor Sections (×4)
Each motor displays:
- **Performance Card**: RPM, Motor ID, Throttle percentage
- **Power Card**: Battery/AC voltage and current
- **Temperature Card**: MCU and motor temperatures with visual bars
- **Status Card**: Vehicle ready status and fault indicators

### Visual Indicators
- 🟢 **Green**: Normal operation, connected
- 🟡 **Yellow**: Warning conditions
- 🔴 **Red**: Fault conditions, disconnected
- 📊 **Temperature
