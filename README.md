# RADAR Using Arduino UNO

A low-cost, functional RADAR system built with an **Arduino UNO**, an **HC-SR04 ultrasonic sensor**, and an **SG90 servo motor** — with real-time scan visualization on a PC using **Processing IDE**.

> Mini Project — Electronics and Communication Engineering

---

## 📖 Overview

RADAR (Radio Detection and Ranging) systems are widely used in defense, aviation, maritime navigation, automotive safety, and meteorology — but conventional systems are expensive and complex. This project replicates the **fundamental working principle of RADAR** using inexpensive, easily available components, making it ideal for academic and educational purposes.

The ultrasonic sensor is mounted on a servo motor that sweeps it across a 0°–180° arc. At each angle, the sensor measures the distance to the nearest object. The Arduino sends the angle and distance data over serial communication to a PC, where a Processing sketch renders it as a live, sweeping radar display — complete with range rings, angle markers, and detected object blips.

## ✨ Features

- Real-time object detection and distance measurement (2 cm – 400 cm)
- 0°–180° sweep scanning using a servo motor
- Live graphical RADAR-style display built with Processing
- Serial communication between Arduino and PC
- Low-cost components, beginner-friendly build
- ~95% detection accuracy on flat, hard surfaces (indoor testing)

## 🧰 Hardware Components

| Component                    | Purpose                                    |
|-------------------------------|---------------------------------------------|
| Arduino UNO (ATmega328P)      | Main microcontroller / processing unit      |
| HC-SR04 Ultrasonic Sensor      | Measures distance via echolocation          |
| SG90 Micro Servo Motor         | Rotates the sensor to scan the surroundings |
| Jumper wires                  | Connections                                  |
| USB Cable                     | Power + serial communication with PC        |

## 💻 Software Required

- [Arduino IDE](https://www.arduino.cc/en/software) — to program the Arduino UNO
- [Processing IDE](https://processing.org/download) — to run the RADAR display sketch

## 🔌 Circuit Connections

**Ultrasonic Sensor (HC-SR04)**

| Sensor Pin | Arduino Pin |
|------------|-------------|
| VCC        | 5V          |
| GND        | GND         |
| Trig       | Digital Pin 10 |
| Echo       | Digital Pin 11 |

**Servo Motor**

| Servo Wire            | Arduino Pin |
|------------------------|-------------|
| VCC (Red)              | 5V          |
| GND (Brown/Black)      | GND         |
| Signal (Yellow/Orange) | Digital Pin 12 |

**Arduino ↔ PC:** Connect via USB cable (used for both power and serial data transfer at 9600 baud).

## ⚙️ How It Works

1. The servo rotates the ultrasonic sensor step-by-step from 0° to 180° and back.
2. At each step, the ultrasonic sensor emits a 40 kHz pulse and listens for its echo.
3. The Arduino calculates distance from the echo's round-trip time.
4. The angle and distance are sent over serial as `angle,distance.`
5. The Processing sketch reads this data and renders a live radar sweep, plotting detected objects as blips on the screen.

## 🚀 Getting Started

### 1. Hardware Setup
Wire the components as described in [Circuit Connections](#-circuit-connections).

### 2. Upload Arduino Code
1. Open `arduino/radar.ino` in the Arduino IDE.
2. Select **Board:** Arduino UNO and the correct **Port**.
3. Upload the sketch.

### 3. Run the Processing Display
1. Open `processing/radar_display.pde` in the Processing IDE.
2. Update the serial port name in the code:
   ```java
   myPort = new Serial(this, "COM3", 9600); // change "COM3" to your Arduino's port
   ```
3. Run the sketch — the radar screen will start displaying live scan data.

> ⚠️ Close the Arduino IDE Serial Monitor before running the Processing sketch — only one program can access the serial port at a time.

## 📊 Results

- Successfully scanned and displayed objects across a 0°–180° arc.
- Detection range: ~2 cm to 400 cm.
- ~95% detection accuracy for hard, flat surfaces under indoor conditions.
- Refresh rate of approximately 1–2 scans per second, sufficient for basic motion tracking.

### Limitations
- Reduced accuracy for soft, irregular, or angled surfaces (ultrasonic wave deflection).
- Sensitive to environmental noise and echo interference.
- Occasional servo jitter causing minor angle inaccuracies.

## 🔮 Future Enhancements

- Extend to full 360° scanning
- Increase detection range with upgraded sensors
- Add wireless data transmission (Bluetooth/Wi-Fi)
- Integrate with IoT platforms or machine learning for smarter object classification

## 📁 Repository Structure

```
├── arduino/
│   └── radar.ino              # Arduino sketch (sensor + servo control)
├── processing/
│   └── radar_display.pde      # Processing sketch (radar visualization)
├── docs/
│   └── RADAR_Project_Report.docx
└── README.md
```

## 👤 Author

**M. Jayantha Siva Srinivas**
Department of Electronics and Communication Engineering
Seshadri Rao Gudlavalleru Engineering College

## 📄 License

This project is open-source and available for educational use. Feel free to fork, modify, and build upon it.
