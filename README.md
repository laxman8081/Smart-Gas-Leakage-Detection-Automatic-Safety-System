# Smart-Gas-Leakage-Detection-Automatic-Safety-System
Arduino-based smart gas leakage detection system using MQ-2, SIM800L, relay, exhaust fan, and servo motor for automatic safety control and SMS alerts
#  Smart Gas Leakage Detection & Automatic Safety System

> An Arduino-based smart safety system designed to detect gas leakage, automatically activate ventilation, control the gas regulator/valve mechanism, trigger an alarm, and send an emergency SMS alert using GSM technology.

---

##  Project Overview

Gas leakage is a serious safety hazard that can lead to fire, explosions, health risks, and property damage.

The **Smart Gas Leakage Detection & Automatic Safety System** provides an automated solution using an **MQ-2 gas sensor, Arduino UNO, SIM800L GSM module, relay module, exhaust fan, servo motor, and buzzer**.

When the system detects a gas concentration above the defined threshold, it automatically performs safety actions and alerts the user.

---

##  Objectives

* Detect gas leakage at an early stage.
* Provide an immediate local alarm.
* Automatically switch ON an exhaust fan.
* Automatically operate a servo-based regulator/valve closing mechanism.
* Send an emergency SMS to a registered mobile number.
* Reduce the risk of fire, explosion, and gas-related accidents.
* Provide an affordable and easily deployable safety solution.

---

##  Key Features

* 🔍 **Real-time Gas Detection**
* 🚨 **Automatic Buzzer Alert**
* 💨 **Automatic Exhaust Fan Control**
* 🔄 **Automatic Regulator/Valve Control**
* 📱 **SMS Alert through SIM800L GSM**
* ⚡ **Relay-Based Appliance Control**
* 🤖 **Arduino-Based Automation**
* 🛡️ **Low-Cost Safety Solution**

---

##  Hardware Components

| Component          | Purpose                               |
| ------------------ | ------------------------------------- |
| Arduino UNO        | Main controller                       |
| MQ-2 Gas Sensor    | Detects LPG/smoke/flammable gases     |
| SIM800L GSM Module | Sends emergency SMS                   |
| Relay Module       | Controls exhaust fan/load             |
| Exhaust Fan        | Helps ventilate the area              |
| Servo Motor        | Controls regulator/valve mechanism    |
| Buzzer             | Provides local warning                |
| Power Supply       | Provides required power to the system |
| Connecting Wires   | Circuit connections                   |
| Breadboard/PCB     | Circuit assembly                      |

---

##  Software & Tools

* Arduino IDE
* Embedded C/C++
* Arduino UNO
* GSM AT Commands
* Git & GitHub
* Serial Monitor

---

## ⚙️ System Working

The system continuously monitors the surrounding environment using the **MQ-2 gas sensor**.

### Normal Condition

```text
MQ-2 Sensor
     ↓
Arduino UNO
     ↓
Gas Level Normal
     ↓
System Monitoring
```

### Gas Leakage Detected

```text
           GAS LEAKAGE
                ↓
          ┌───────────┐
          │  MQ-2     │
          │   Sensor  │
          └─────┬─────┘
                ↓
          ┌───────────┐
          │ Arduino   │
          │   UNO     │
          └─────┬─────┘
                ↓
       Gas Level Above Threshold
                ↓
     ┌──────────┼───────────┐
     ↓          ↓           ↓
  Buzzer      Relay      Servo Motor
     ↓          ↓           ↓
  Warning   Exhaust Fan   Regulator/
                         Valve Control
                ↓
           SIM800L GSM
                ↓
          Emergency SMS
```

---

##  Step-by-Step Operation

1. The **MQ-2 sensor** continuously monitors the gas concentration.
2. The sensor provides an analog signal to the **Arduino UNO**.
3. Arduino compares the sensor value with the predefined threshold.
4. If the value remains within the safe range, the system continues monitoring.
5. If gas leakage is detected:

   * 🚨 Buzzer is activated.
   * 💨 Exhaust fan is switched ON through the relay.
   * 🔄 Servo motor activates the regulator/valve closing mechanism.
   * 📱 SIM800L sends an emergency SMS.
6. The system continues monitoring until the gas level returns to a safe range.

---

## Basic Pin Configuration

> **Note:** Pin assignments can be changed according to the final circuit and Arduino code.

| Component          | Arduino UNO Pin              |
| ------------------ | ---------------------------- |
| MQ-2 Analog Output | A0                           |
| Buzzer             | D8                           |
| Relay Module       | D7                           |
| Servo Motor        | D9                           |
| SIM800L TX         | SoftwareSerial RX            |
| SIM800L RX         | SoftwareSerial TX            |
| GND                | GND                          |
| VCC                | Appropriate regulated supply |

### SIM800L Power Warning

The SIM800L requires a suitable power supply capable of handling its current peaks. **Do not power the SIM800L directly from the Arduino UNO 5V pin unless your specific module/setup is designed for it.**

Use an appropriate regulated supply and ensure that the **Arduino and SIM800L share a common ground**.

---

##  System Logic

```text
START
  ↓
Initialize Arduino
  ↓
Initialize MQ-2
  ↓
Initialize GSM
  ↓
Read Gas Sensor
  ↓
Is Gas Level > Threshold?
  ↓
 ┌───────────────┐
 │               │
NO              YES
 │               │
 ↓               ↓
Continue       Buzzer ON
Monitoring        ↓
              Fan ON
                 ↓
              Servo Activate
                 ↓
              Send SMS
                 ↓
              Continue Monitoring
```

---

## SMS Alert

When dangerous gas leakage is detected, the **SIM800L GSM module** can send an emergency SMS to the configured mobile number.

### Example Alert

```text
⚠️ GAS LEAKAGE ALERT!

Gas leakage has been detected.
Please check the gas regulator/cylinder immediately.

Automatic safety actions have been activated.
```

---

## Arduino Code

The main Arduino program is located in:

```text
Arduino/smart_gas_leakage.ino
```

The program handles:

* MQ-2 sensor reading
* Gas threshold detection
* Buzzer control
* Relay control
* Servo motor control
* SIM800L GSM communication
* SMS notification

---

## Project Structure

```text
Smart-Gas-Leakage-Safety-System/
│
├── Arduino/
│   └── smart_gas_leakage.ino
│
├── Circuit/
│   └── circuit_diagram.png
│
├── Documentation/
│   └── project_report.pdf
│
├── Presentation/
│   └── project_presentation.pdf
│
├── Images/
│   ├── hardware_setup.jpg
│   ├── circuit.jpg
│   └── testing.jpg
│
├── Video/
│   └── project_demo_link.txt
│
└── README.md
```

---

## Testing

The system should be tested in controlled conditions.

### Test Cases

| Test                            | Expected Result                  |
| ------------------------------- | -------------------------------- |
| Normal air                      | No alarm                         |
| Gas concentration increases     | MQ-2 detects change              |
| Leakage crosses threshold       | Buzzer ON                        |
| Leakage detected                | Exhaust fan ON                   |
| Leakage detected                | Servo safety mechanism activated |
| Leakage detected                | SMS alert sent                   |
| Gas level returns to safe range | System returns to monitoring     |

---

##  Advantages

* Low-cost implementation
* Automatic safety response
* Real-time monitoring
* Remote SMS notification
* Easy to expand
* Suitable for IoT and smart-home applications
* Can help reduce response time during gas leakage

---

## Safety Considerations

This project is an **educational prototype** and should not be treated as a certified gas-safety device.

* Do not test the system with uncontrolled LPG release.
* Perform testing only in a safe and controlled environment.
* Keep electrical components away from actual gas leakage sources.
* Use appropriate electrical isolation for AC loads.
* The servo mechanism should be mechanically designed so that it cannot damage the regulator.
* For a real deployment, use certified gas detectors and certified automatic shut-off valves.
* Never rely solely on this prototype for life-safety protection.

---

##  Future Scope

The system can be further improved by adding:

* 📡 IoT/cloud monitoring
* 📱 Mobile application
* 🌐 Web dashboard
* 🔔 Push notifications
* 📍 GPS location sharing
* ☁️ Cloud data logging
* 📈 Gas-level monitoring graphs
* 🔋 Battery backup
* 🧠 AI-based anomaly detection
* 📷 Camera-based verification
* 🏠 Smart-home integration
* 🔐 Secure communication and authentication

---

##  Cyber Security Scope

As a **Cyber Security & Forensics project**, future versions can include:

* Secure IoT communication
* Device authentication
* Encrypted communication
* Secure API integration
* Access control
* User authentication
* Event logging
* Tamper detection
* Security monitoring
* Cloud database security

---

## Project Demonstration

**Presentation Video:**
`[Add YouTube/Google Drive Video Link Here]`

---

## Deployment

**Live Project / Dashboard:**
`[Add Deployed Project Link Here]`

If the current version is hardware-only, write:

> **Deployment:** Hardware-based standalone prototype. IoT/web deployment is planned for the future version.

---

##  Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/Smart-Gas-Leakage-Safety-System.git
```

### 2. Open Arduino Code

Open:

```text
Arduino/smart_gas_leakage.ino
```

in **Arduino IDE**.

### 3. Select Board

```text
Tools → Board → Arduino UNO
```

### 4. Select COM Port

```text
Tools → Port → Select Arduino COM Port
```

### 5. Upload Code

Connect the Arduino UNO and upload the program.

### 6. Configure GSM Number

Update the emergency phone number in the Arduino code before uploading.

---

##  Requirements

### Hardware

* Arduino UNO
* MQ-2 Gas Sensor
* SIM800L GSM Module
* Relay Module
* Exhaust Fan
* Servo Motor
* Buzzer
* Suitable power supply
* Jumper wires
* Breadboard/PCB

### Software

* Arduino IDE
* Git
* GitHub account
* Active SIM card for GSM module

---

## License

This project is created for **educational and academic purposes**.

You may modify and use the project for learning and non-commercial educational purposes.

---

## 👨‍💻 Developer

**Laxman Verma**

BCA – Cyber Security & Forensics 
Babu Banarasi Das University, Lucknow

### Areas of Interest

* 🔐 Cyber Security
* 🕵️ Digital Forensics
* 🌐 Networking
* 🐍 Python
* 🤖 IoT Security
* 🔎 OSINT
* 🛡️ Ethical Hacking

---

## Acknowledgement

Special thanks to **Babu Banarasi Das University (BBDU)**, faculty members, and everyone who supported the development and testing of this project.

---

## Support

If you find this project useful for learning, consider giving the repository a .

**Made with Cyber Security, IoT & Smart Safety**
