# IoT Light Scheduler

This project creates a web-based light scheduling system using WebSocket and MQTT for the Rwanda Coding Academy's Embedded Systems Software Integration course. It is designed to simulate a real-world IoT dashboard for scheduling light ON/OFF operations using modern web technologies and hardware.

---

## Features

- **Sleek, Adaptive UI**: Built with Tailwind CSS for a modern and responsive design.
- **WebSocket Server**: Efficient handling of schedules in real-time.
- **MQTT Integration**: Enables precise, timed light control.
- **Hardware Integration**: Utilizes Arduino UNO with a relay module for physical light switching.

---

## Technologies Used

- **Frontend**: HTML, CSS, JavaScript (WebSocket).
- **Backend**: Python (WebSocket server + MQTT Subscriber), mosquitto_pub/sub.
- **Hardware**: Arduino UNO.

---

## Setup Instructions

### 1. Arduino Setup

1. Connect the relay module to the Arduino UNO:
   - **VCC** to 5V, **GND** to GND, **IN** to pin 8.
   - Ensure the live wire is securely placed between **COM** and **NO**, with proper insulation.
2. Upload the following Arduino code:
   ```cpp
   int relayPin = 8;

   void setup() {
     Serial.begin(9600);
     pinMode(relayPin, OUTPUT);
     digitalWrite(relayPin, HIGH); // Relay OFF initially
   }

   void loop() {
     if (Serial.available() > 0) {
       String cmd = Serial.readStringUntil('\n');
       cmd.trim();
       if (cmd == "ON") {
         digitalWrite(relayPin, LOW); // Relay ON
       } else if (cmd == "OFF") {
         digitalWrite(relayPin, HIGH); // Relay OFF
       }
     }
   }


### 2. Install Requirements
```bash
pip install websockets paho-mqtt pyserial