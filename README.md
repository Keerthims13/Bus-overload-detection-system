# 🚍 Bus Overload & Accident Detection System

This project is an **Arduino-based Bus Overload & Accident Detection System**.  
It integrates **Ultrasonic Sensor, GSM Module, Servo Motor, Bluetooth (HC-05), Buzzer, and LCD Display** to monitor passenger overload or accident situations and send alerts.

---

## 📌 Features

- **Ultrasonic Sensor (HC-SR04):**
  - Measures distance inside the bus (simulates passenger detection or accident proximity).
- **Accident Detection:**
  - If the distance is below 10 cm → accident is assumed → buzzer alerts, LCD displays warning, door opens automatically, and an SMS is sent.
- **Automatic Door Simulation (Servo Motor):**
  - Opens/closes bus door automatically.
- **Bluetooth (HC-05):**
  - Remote control to open/close/stop the door using commands:
    - `O` → Open Door
    - `C` → Close Door
    - `S` → Stop Servo
- **Buzzer:**
  - Alerts in case of accidents or overload.
- **GSM Module (SIM800L/SIM900):**
  - Sends an SMS alert to a predefined number when accident detected.
- **16x2 I2C LCD Display:**
  - Shows real-time distance and system alerts.

---

## 📂 Components Used

- Arduino Uno / Mega  
- Ultrasonic Sensor (HC-SR04)  
- GSM Module (SIM800L / SIM900)  
- Bluetooth Module (HC-05)  
- Servo Motor (SG90 / MG995)  
- Buzzer (3-pin)  
- 16x2 I2C LCD Display  
- Jumper wires & Breadboard  

---

## 🔧 Pin Connections

| Component              | Arduino Pin |
|-------------------------|-------------|
| Ultrasonic TRIG        | 8           |
| Ultrasonic ECHO        | 9           |
| Buzzer                 | 2           |
| Servo Motor            | 5           |
| GSM Module RX/TX       | 10 (RX), 11 (TX) |
| Bluetooth HC-05 RX/TX  | 6 (RX), 7 (TX)   |
| LCD (I2C Address 0x27) | SDA/SCL (A4/A5 on Uno) |

---

## ▶️ How It Works

1. **System Boot:**
   - LCD shows *System Ready!* message.
2. **Normal Mode:**
   - Ultrasonic sensor measures distance.
   - LCD continuously displays distance.
3. **Accident Detection:**
   - If distance `< 10 cm` → accident alert triggered.
   - Buzzer ON, LCD shows *Accident! SMS Sent!*
   - Servo opens door.
   - GSM module sends SMS alert to stored phone number.
4. **Bluetooth Control:**
   - Send command `O` → Open door
   - Send command `C` → Close door
   - Send command `S` → Stop servo

---

## 📜 Code Highlights

- `readUltrasonic()` → Measures distance.  
- `openDoor()` → Simulates door opening/closing.  
- `sendSMS()` → Sends SMS using GSM AT commands.  
- `printMessage()` → Displays LCD messages with typewriter effect.  

---

## 📱 SMS Alert Format

```text
Alert: Accident detected. Immediate help required!
